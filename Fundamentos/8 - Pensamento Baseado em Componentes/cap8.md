Modulo = colecao de codigo relacionado
Componente = Empacotamento fisico do modulo

A ideia que passa eh que componente eh como se fosse uma parte pronta do codigo. Vamos imaginar um martelo, temos a parte de metal e o cabo. Cada uma das partes sao modulos, elas juntas formam o componente *martelo*

# Escopo de Componente
Eh interessante de ver da explicacao anterior que componente e biblioteca querem dizer basicamente a mesma coisa (uma ferramenta que vai ser usada em tempo de compilacao)

Um arquiteto nao precisa necessariamente utilizar componentes, faz pq na maioria das vezes eh conveniente. Um componente pode ser pequeno ou grande, o que importa no fim das contas eh atender as necessidades

# Funcao do arquiteto
Obviamente, como estamos falando de ferramentas eh interessante que o arquiteto tenha peso na hora da escolha. Porem o livro nessa parte parece dar muito mais uma ideia de **arquiteto de solucao** do que **arquiteto de software**. Isso pq ele fala que eh mais papel de um tech lead / devs decidirem o que querem usar de componentes do que ele mesmo em si.

No resumo, obvio que eh importante considerar qual ferramenta usar, mas esse peso fica muito mais com a equipe que esta desenvolvendo (tech lead, arquiteto de software, devs) do que propriamente o cara de solucoes. Segundo o livro, fazer microgerenciamento dessas coisas em 1 unico ponto focal (arquiteto) vai gerar um gargalo la na frente.

# Particoes
Essa parte diz como a gente organizaria nosso componente (entenda-se MVC, Domain partitioning, etc). O livro busca nessa parte apenas apresentar diferentes pontos de vistas de como pode ser separado alguns conceitos da aplicacao. Na parte II o livro promete explicar com mais detalhes do que se trata esse nivel de particoes.

Lembrando que tudo na arquitetura eh um trade-off, entao nao existe certo e errado nesses casos

### Lei de Conway
Criada em 1960, diz o seguinte:
Quando uma empresa cria um design system (padrao de projeto a ser seguido) toda a comunicacao da equipe passa a girar em cima desse tipo de design, nao importando o nivel de cargo das pessoas presentes na organizacao

# Identificacao de componentes
Como aqui nosso objetivo eh criar particoes no codigo (que se traduzem em componentes). Aqui vamos descrever as etapas que compoem esse processo:

- Identificar componentes iniciais
- Atrelhar requerimentos para o componente
- Analizar papeis e responsabilidades
- Analizar caracteristicas de arquitetura
- Reestruturar componentes

## Identificar componentes iniciais
Nessa etapa vamos levantar de forma embrionaria todos os componentes que acreditamos potencialmente serem necessarias para o sucesso do projeto.

Parece algo simples, mas eh isso que dara um norte aos desenvolvedores sobre o que trabalharemos

## Atrelhar requerimentos para o componente
Essa etapa vamos fazer um de/para com o que temos entre os requirimentos do time de negocio e tambem os componentes que haviamos criados. Eh notavel que essa etapa e a anterior sao fortemente acopladas, se por algum acaso identificarmos que ha lacunas existentes entre nossos componentes e os requerimentos podemos refazer a etapa 1 sem problemas

## Analizar papeis e responsabilidades
Aqui o objetivo eh garantir que o componente esta com a granularidade correta (ou seja, se ele nao esta com responsabilidade d+ ou d-)

## Analizar caracteristicas de arquitetura
A caracteristica de arquitetura nao eh levantada nessa etapa. Na verdade ela eh levantada **anteriormente**, nessa etapa o que vamos fazer eh pegar as caracteristicas levantadas e fazer elas se encaixarem a nivel dos nossos componentes

## Reestruturar componentes
Essa eh uma etapa de feedback, basicamente vamos conferir se tudo o que fizemos ate entao esta correto. Se nao tiver voltamos pra etapa que esta errada e repetimos todos os processos apresentados ate entao

# Granularidade de componentes
Significa verificar se o seu componente esta com resposabilidade d+ ou d-. Eh meio complexo criar um bom balanco entre essas 2 coisas, isso pq se deixarmos o componente muito dividido vai exigir muitas comunicacoes entre ele para funcionar, e se deixarmos pouco dividido vai ser ruim de testar (pq vc vai ter basicamente um blocao que faz tudo) e consequentemente fazer deploy e ser agil