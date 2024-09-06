# Extraindo Caracteristicas de Arquitetura do time de produto
Essa parte diz basicamente o seguinte: **qual eh o foco do nosso produto?**

Entender a pergunta acima eh crucial para entendermos o que precisaremos adicionar nas caracteristicas da arquitetura. Vamos a um exemplo:

Vamos supor que vamos desenvolver uma feature que vai *Salvar dados de log de uma aplicacao*. O que eh importante nesse caso?

Bom, nesse caso temos que ter uma redundancia para salvar essas informacoes (Fault tolerance). Mas se olharmos bem, o nosso foco aqui nao eh garantir elasticidade (elasticity) do servico (nesse exemplo).
O ponto chave para extracao de caracteristicas eh justamente isso. Baseado no que meu sistema tem, o que precisaremos se preocupar no quesito arquitetural.

### Entao seria interessante criar uma arquitetura generica que envolve todos os ilities?
**NAO**, arquiteturas no gerais sao coisas complexas. O correto eh mantermos a arquitetura mais simplificada possivel, colocar suporte para todos os ilities alem de deixar a arquitetura + complexa iria deixar certas partes inuteis (e ate gerando prejuizo financeiro para a empresa dependendo da implementacao adotada)

Tome cuidado quando arquitetar seus projetos em sempre olhar o projeto como um todo. Se o cliente te pedir por exemplo: Precisamos completar esse processo X todo dia

Olhar para essa demanda requer varias camadas de "ilities" no sistema, por exemplo:
Availability
Auditability
Recoverability
Performance
Etc

repare que em linhas normais eh comum o arquiteto olhar para o projeto e pensar:
*Se eles querem que eu termine o processo sempre no dia de hoje e ele esta lento eu vou aumentar a performance e vai funcionar.*
Isso nem sempre eh verdade pois por exemplo, vamos supor que o processo esta em 90% e da pane no sistema, ele vai ter que voltar do 0 de novo e nao tem performance no mundo que faca ele rodar tao rapido.

Sempre se lembre:
*Nao existe respostas erradas em arquitetura. Existem respostas caras*

# Extraindo Caracteristicas de Arquitetura de requerimentos
Essa parte do livro cita o seguinte exemplo:

Temos os requisitos: A, B, C

Segundo isso que o time de produto pede, como devemos estruturar nossa arquitetura?

Um site muito bom para praticar isso eh o https://nealford.com/katas/list.html

### Diferenca entre extrair de Requerimentos X Time de produto
Time de produto = Vai explicar que ele quer um produto da forma ABC
Requerimentos = Solicita que seu produto deve possuir as funcionalidades XPTO

Por mais que sao bem similares (ate a ideia por detras eh a mesma) a diferenca esta no nivel de granularidade das informacoes. Quando extraimos do requerimento ja temos as funcionalidades que nosso sistema deve possuir. Quando extraimos do time de produto temos a ideia geral de o que nosso software deve fazer
