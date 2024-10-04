Geralmente arquiteturas sao criadas a partir do tempo e nao somente por uma pessoa so. O pessoal na area de programacao ve que determinada estrategia esta dando certo e resolvem nomeaar ela, isso nao foi verdade com microservicos. O que ocorreu nesse caso foi que martin flower e james lewis cunharam o termo e colocaram em seu blog como alguma coisa tinha que se parecer pra ser considerada microservicos

# Topologia
A ideia desse tipo de arquitetura eh "criar um mini sistema" dentro da aplicacao principal, entao criamos pequenos mundos que so sabem fazer um tipo de coisa. Isso implica no seguinte:

- 1 API layer (comum entre os MSs so para fazer o papel de orquestrador)
- 1 Service (cada service vai ser exclusivo pra determinada funcionalidade)
- 1 database (ao colocar um DB por MS garantimos que so aquele MS vai enxergar as coisas do seu mundo, e nao vai depender de "entidades externas" para sobreviver)

## Distribuicao
MSs tem o que chamamos de _arquitetura distribuida_ significa que cada um tem sua funcao muito bem definida dentro de um sistema e que nao precisa de ninguem para sobreviver. Dado essa caracteristica podemos ter diversos MSs dentro de uma mesma maquina fisica (atingimos isso atraves de containers), isso reduz para 0 a questao de utilizacao de banda de rede (eh claro que vai depender do recurso da maquina para fazer isso, nao eh errado termos diferentes MSs em diferentes PCs ligados pela rede)

Ter uma arquitetuar distribuida nao significa que tudo eh 1000 maravilhas, se a gente precisar espalhar os MSs pela rede ai caimos em um grande problema. Isso pq como o MS so sabe fazer uma unica coisa e nada mais precisaremos requisitar N servicos diferentes a fim de conseguir processar toda uma informacao (isso faz a nossa performance cair por conta da latencia de rede)

## Bounded context
De novo vamos bater na tecla que o MS so precisa dele mesmo para sobreviver e nada mais. Isso significa que se o servico A possuir um codigo que o B precisa, B precisara copiar o codigo de A e nao reaproveitar ele. **Em microservicos priorizamos duplicidade ao inves de acoplamento**

## Granularidade
Muito cuidado ao achar que so podemos fazer 1 coisa no microservico podemos fazer N coisas **que aquele determinado dominio contempla**. Nao caia no erro de criar um MS muito pequeno pois voce ira precisar criar algum outro pra contemplar dai entramos em questao de conectividade, uso de rede e tudo mais.

Aqui estao algumas dicas do livro pra voce saber quais sao os "limites" ao criar um MS

- Respeite o dominio
- Evite transacoes pela rede (se da pra deixar no mesmo lugar, deixe junto. Esse topico eh tao importante que tem 2 paragrafos so pra ele)

## Isolamento de dados
Isolamos dados (ou seja, temos um banco de dados por MS) devido a arquitetura distribuida e para a reducao de acoplamento entre MSs.

_Mas o que exatamente ganhamos com isso?_
A gente ganha liberdade de escolher o que melhor se encaixa para determinada necessidade. Vamos imaginar que voce precisa no caso A de um banco NoSQL e no caso B de um SQL. Com a questao de microservicos cada um pode ter o seu sem atrapalhar o outro (e obviamente isso acaba trazendo um melhor gerenciamento de recursos do sistema, o que como consequencia traz economia)

## API Layer
Camada responsavel por ligar o front com o Back (Isso nao eh a mesma coisa que um BFF, ela serve so como ponte e um bff tem mais usabilidade alem disso, confira a parte de **Transacoes** aqui neste capitulo para entender mais)

## Reusabilidade
Beleza, na parte de isolamento falamos que cada um tem que ter o seu proprio dado e que nao eh pra acoplar nada e pipipi popopo. Mas e quando a gente tem ganhos ao realizar acoplamentos? (Como por exemplo em analise de logs, monitoramento e circuit breaker)?

Nesse caso o livro sugere criar um acoplemento parecido com a ideia de microkernel. A gente cria um componente (leia-se biblioteca) que vai deter todas essas funcionalidades, quando a gente precisar atualizar eh so atualizar o componente que todos vao refletir essa mudanca (eh como se tivesse no package.json do JS e colocasse o @latest)

# Frontend
A ideia dos autores que que fossem criados tambem _microfrontends_, dessa forma o sistema teria seus limites ainda mais delimitados tendo em vista que somente um determinado front iria acessar um determinado MS.

Nao eh que esta errado ter um frontend como monolito requisitando MSs, mas para manter uma questao de limites eh mais recomendado a abordagem de microfrontends

# Comunicacao
Eh muito dificil encontrar a correta granularidade ao construir um MS, isso impacta diretamente em gerar mais comunicacoes pela rede. O que o pessoal recomenda nesses casos eh o seguinte:

- Protocol-aware
- Heterogeneous
- Interoperability

## Protocol-aware
Parte da comunicacao pode ocorrer entre MS, para isso sempre precisamos nos atentar em como essa comunicacao eh feita (se eh por REST, por fila, por RPC, etc)

## Heterogeneous
Nesse caso eles querem dizer que o MS consegue conviver em um ambiente que possui comunicacoes diferentes da sua

## Interoperability
Significa um MS chamando outro

# Transacoes
Mais uma vez nesse tema, deixar a responsabilidade de transacionar so para o MS eh um tiro no pe, isso pq temas como debugging em caso de erro e tambem sincronizar a ordem que as requisicoes vao acontecer eh simplesmente uma loucura (e so vai criar acoplemento no Ms). Pensando nisso o pessoal cria **orquestradores** (geralmente quem faz esse papel de orquestrador eh o BFF).

O BFF tem como objetivo ser a ligacao entre o front e o backend, mas ele tambem tem como papel orquestrar qual eh a ordem de chamadas que temos para um microservico. Vamos imaginar o seguinte cenario.

Precisamos de 3 informacoes, cada uma delas esta contida em um MS diferente.

Nesse caso, nosso bff vai fazer 3 requisicoes para 3 MSs diferentes, se por algum acaso algum der problema o BFF tera o simples papel de nos informar em qual deles deu erro e qual erro ocorreu.

Repare que nessa abordagem so precisamos consultar o orquestrador em caso de erro, assim, nao alteramos a logica dos MSs e criamos um ponto unico de controle sobre problemas que ocorreram

Eh interessante colocar que quanto mais transacoes fizermos em rede mais lento sera nossa resposta. Isso significa que adicionar um BFF pode ate ter suas vantagens mas a principal desvantagem eh com certeza a parte de performance (e nao pq o BFF eh lento, e sim pq existe a latencia de rede)

# Pq usar esse tipo de arquitetura?
Essa arquitetura aqui eh muito forte (nao significa que seja uma bala de prata). Mas eh valido ressaltar que sem uma boa equipe de DevOps ela nao vale de nada. Ela tambem tem seus defeitos por ser uma arquitetura distribuida. A performance tambem apanha bastante aqui

O ponto forte dela eh escalabilidade, elasticidade e capacidade de evolucao (geralmente os sistemas mais escalados ate entao usam essa arquitetura)