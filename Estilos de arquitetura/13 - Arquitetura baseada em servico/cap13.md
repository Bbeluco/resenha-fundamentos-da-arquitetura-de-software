# Topologia
A topologia dessa arquitetura se baseia no seguinte:

- 1 UI geral
- N "Componentes" (tambem conhecidos como _services_ ou _domain services_)
- 1 Unico banco de dados

Essa abordagem de colocar N componentes conforme a necessidade possibilita em cenarios que requerem escalabilidade facilmente pode ser adicionado mais instancias a aplicacao (no caso da aplicacao subir mais de um _domain service_ de mesmo tipo eh necessario trabalhar com load balancer)

Geralmente a comunicacao entre UI e servicos eh feita em REST, SOAP ou RPC

### Variacoes de Topologia
Podemos ter as seguintes variantes para essa topologia:

Uma topologia **baseada em dominio**:

- 2 UI geral (Uma UI para cada dominio da minha aplicacao)
- N "Componentes" (Nesse caso os componentes ligados a UI possuem correlacao com o mesmo dominio)
- 1 Unico banco de dados

Uma topologia **baseada em servicos**:
- N UI geral (Uma UI para cada servico)
- N "Componentes" (Cada componente vai ter sua propria UI)
- 1 Unico banco de dados

Um ponto adicional que podemos ter tambem entre a UI e os componentes sao as APIs (nesse caso elas atuam como um reverse proxy).
Isso eh muito bom caso a gente queira escalar a aplicacao pra UI ficaria transparente pois sempre consultariamos o reverse proxy.

# Service Design e Granularidade
Essa arquitetura trata de um sistema como um todo, mas o livro separa essa parte para descrever como seria a arquitetura dentro do _domain service_
Em linhas gerais, usamos a arquitetura baseada em camadas para tratar pontos desse nivel.

Em teoria o nivel de granularidade que divide uma arquitetura de microservicos e uma arquitetura baseada em servico
Em suma, a API que a gente coloca nessa arquitetura possui como responsabilidade _Orquestrar a requisicao de negocios da UI_
Funciona mais ou menos assim:

Se a gente for fazer checkout teremos que ter os seguintes passos:
- Realizar pedido
- Gerar o ID do pedido
- Aplicar pagamento
- Atualizar o inventario

Em uma arquitetura baseada em servico todos esses passos sao feitos de uma vez pelo componente responsavel, enquanto numa arquitetura de MS isso eh feito em diferentes locais por diferentes servicos

Em relacao a banco de dados a arquitetura baseada em servico foca em ter **ACID**, enquanto microservicos foca em ter **BASE**

ACID = **A**tomicidade, **C**onsistencia, **I**solamento e **D**urabilidade
BASE = **B**asic **A**vailability, **S**oft state e **E**ventual consistency

Fazendo uma analise do livro chegamos a conclusao que eh muito mais facil lidar com banco de dados quando temos uma arquitetura baseada em servico do que uma arquitetura baseada em microsservico. Isso pq como todo mundo compartilha do mesmo DB fica muito mais facil de dar rollback caso alguma coisa de errado (gracas a atomicidade)

# Particionamento de banco de dados
Como dito inicialmnete nesse tipo de arquitetura geralmente o banco de dados eh compartilhado entre os _domain services_ da aplicacao. Temos que tomar cuidado nesse caso de nao criar uma **shared lib** nesse caso pois se por acaso a biblioteca que realiza as chamadas pro DB for atualizada todos os servicos que consomem ela vao precisar de um novo deploy novamente

Um modo interessante de evitar esse tipo de problema seria criar uma separacao logica dentro do banco de dados, e quando criasse a lib se baseasse nesse tipo de separacao (no fim, cada um dos _domain services_ teria "sua propria lib") o que diminuiria o impacto do deploy

# Pq usar esse tipo de arquitetura?
Esse tipo de arquitetura pode ser classificado como: uma arquitetura _baseada em dominio_ (Significa que a gente divide baseado em requisitos funcionais e nao tecnicos)

Ela possui boa agilidade (gracas a criacao dos componentes), eh testavel (gracas a granulacao do sistema), tem bom deployability (gracas a criacao dos componentes). Ou seja, essa arquitetura eh boa para alacancar **time-to-market**
Segundo os autores essa arquitetura nao possui a melhor das elasticidades (isso pq se a gente escalar esse sistema outras coisas escalam junto ja que separamos por dominio). Ela tambem possui um custo alto e abrimos sim mao da simplicidade pois se trata de algo mais rebuscado

Essa arquitura em linhas gerais eh super completinha, e eh bem equilibrada, mas o fato de ser cara de manter e tambem de ser mais complexa pesa bastante na balanca.