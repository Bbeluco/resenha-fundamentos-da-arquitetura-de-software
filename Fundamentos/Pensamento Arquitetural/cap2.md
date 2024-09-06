Segundo o livro, um arquiteto deve pensar de forma diferente de um desenvolvedor

Os 4 aspectos principais para pensar como um arquiteto sao:
- Entender a diferenca entre arquitetura e design.
- Ter uma visao *wide breadth* ao mesmo tempo que *technical depth*
- Entender e analisar os trade-offs ao seguir pelo caminho A ou B
- Entender o que a empresa ou aquela solucao se propoe a resolver

# Arquitetura VS Design
Papel do arquiteto:
- Analisar requerimentos do negocio para desenvolver um sistema (atingindo caracteristicas de arquitetura citadas no arquivo Pensamento introducao/intro.md)
- Selecionar padroes de arquitetura (o mais coeso para aquele problema)
- O livro diz *creating components* (eu particularmente interpreto components aqui como sendo por exemplo os contratos que um BFF retorna, nao necessariamente o Arquiteto vai codar isso, ele so quer que seja desse jeito)

Papel do desenvolvedor:
- Colocar em pratica tudo aquilo que o arquiteto desenhou

O livro ressalta um ponto muito importante, **colocar o arquiteto isolado do desenvolvedor eh burrice** a comunicacao vai ficar simplesmente horrivel, e qualquer mudanca (seja na parte de dev ou de arq) sera um parto de deixar os 2 na mesma pagina.
O arquiteto precisa ser aquele cara que esta proximo aos devs (e que escuta tambem o que eles tem para dizer) e vice-versa, dessa forma a comunicacao fica fluida e tudo ocorre melhor

# Technical Breath
Eh esperado que o dev tenha technical depth (ou seja, ele entende a tecnoligia de forma aprofundada, conhece as nuances dela e tudo mais), enquanto o arquiteto tenha mais technical breath (nao conhece detalhes taaaao aprofundado assim, mas entende muito bem os trade offs delas)

O livro tem algumas imagens que representam esses pontos. Eh um triangulo dividido em 3. No topo temos *coisas que sabemos* (que seria tudo aquilo que temos pleno dominio e estamos em contato no dia a dia), *coisas que conhecemos* (nao possuimos conhecimento mas sabemos que existe. Exemplo linguagem Clojure), *coisas que nao conhecemos* (coisas que a gente nem sabe que existe).

O livro propoe ao inves do arquiteto saber 1 coisa so muito a fundo, que ele saiba 5 coisas de forma "mais superficial" (superficial entenda: o suficiente para conhecer os trade offs da tecnologia). Dessa forma, havera uma gama maior de tecnologias que ele sera capaz de propor e tudo mais

### Frozen Caveman Anti-Pattern
Esse anti-pattern diz que o arquiteto fica completamente preso a um problema no passado e tudo que ele faz/pensa envolve esse problema.

Exemplo: A 10 anos atras eu perdi a minha conexao com a Matriz. Nos dias atuais eu vou fazer uma feature e penso (e se eu perder a comunicacao com a matriz). Obvio que existem cenarios que isso faz total sentido, agora tem casos que nao faz. Eh papel do arquiteto saber dosar quando ele esta pensando demais ou nao

# Analise de Trade-Offs
*Thinking like an architect is all about seeing trade-offs in every solution*
*There are no right or wrong answers in architecture—only trade-offs.*

Essas frases acima foram retiradas do livro e descrevem muito bem o que eh a vida de um arquiteto. Analisar tradeoffs quer dizer: Baseado na minha realidade atual, eh melhor eu fazer A ou B?

Isso nao existe de mao beijada no google, voce precisa conhecer o que esta fazendo para so entao conseguir chegar a esta conclusao

# Bussiness Drive
Entender junto aos stakeholders o que aquela solucao precisa / a dor que ela procura resolver. Isso eh importante pois da a ideia para o arquiteto do que eh esperado a nivel de produto, fazendo assim com que ele tome decisoes mais acertadas por estar enxergando o todo e nao so a parte de codigo