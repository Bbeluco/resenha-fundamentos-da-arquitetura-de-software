Eh muito dificil escrever um livro de arquitetura pois tudo parece sempre mudar constantemente. Um exemplo bom eh que na decada passada (2014) muitos "arquitetos de software" nao se preocupavam com devops, isso pq simplesmente DevOps nao existia no passado

*A arte so pode ser entendida levando em conta o contexto*

A frase acima retrata uma boa logica a seguir, as pessoas (nesse caso tecnico, os arquitetos) sempre fazem o melhor que eles possuem no contexto que elas estao inseridas naquele momento.

Um exemplo mostrado nesse livro logo no comeco eh a questao de microservicos, se voltassemos a 2002 e dessemos a ideia de trazer escalabilidade mas em troca precisar do dobro de hardware nao iria fazer um pingo de sentido. Isso pq nao precisavamos de tantos recursos quanto hoje.

Lendo esse trecho do livro, eh correto admitir que **a evolucao vem somente de acordo com a necessidade**, nao faz sentido inventarmos o motor se ainda nao existe o carro para usar.

# Definindo arquitetura de software
Nos dias de hoje (2024), ainda nao existe um consenso na comunidade do que seria um arquitetura de software. Os autores do livro tentam colocar que os seguintes requisitos englobam arquitetura:

- Caracteristicas de arquitetura
- Principios de design
- Decisoes de arquitetura
- Estrutura


### Estrutura
Significa o(s) tipo(s) de estilo(s) de arquitetura que foi utilizado. Exemplo: microservices, layered, microkernel, etc
Nao podemos olhar um sistema e considerar arquitetura apenas a sua estrutura. Quando perguntar pra alguem qual eh a arquitura do projeto nao basta a pessoa responder (eh uma arquitetura de microservicos), isso apenas trata da estrutura que o sistema esta disposto.

### Caracteristicas de arquitetura
Sao os criterios de sucesso de uma aplicacao. Isso significa que essas caracteristicas nao dependem de conhecimento da funcionalidade do sistema. As caracteristicas sao:
- Disponibilidade
- Confiabilidade
- Testabilidade
- Escalabilidade
- Seguranca
- Agilidade
- Tolerancia a falhas
- Elasticidade
- Recuperabilidade
- Performance
- Deployability
- Learnability

### Decisoes de arquitetura
Definicoes de regras de como o sistema deve ser construido. Por exemplo: Somente a camada de negocios e de servicos deve se comunicar com o banco de dados. Basicamente eh ditado a forma que o sistema deve ser organizado

Se por algum acaso quando estivermos criando decisoes de arquitetura e encontrarmos um gap (Exemplo: Minha camada de apresentacao precisava muito se comunicar direto com o banco de dados), podemos abrir uma excesao. Essa excesao normalmente eh chamada de *variance*. Empresas geralmente possuem documentos bem definidos do que pode (ou nao) entrar no tema de variance.

### Principios de design
Diretriz que deve ser seguida no sistema. Exemplo (sempre que possivel deixe mensagens assincronas para aumentar a performance do sistema)

## O que esperado de um arquiteto?
- Realizar decisoes de arquitetura
- Analisar a arquitetura continuamente
- Se manter atualizado com o que ha de novo no mercado
- Garantir que compliance esta sendo seguido
- Ter experiencias variadas durante a carreira
- Ter dominio da logica de negocio
- Ter habilidades interpessoais
- Entender de politicas da empresa

### Realizar decisoes de arquitetura
*Eh esperado que o arquiteto defina decisoes e principios de design usados para guiar uma decisao de tecnologia com o time*

Na frase acima temos a palavra *guiar* nao eh correto para um arquiteto impor a sua vontade. (Exemplo: Vamos usar react nesse projeto aqui). O correto eh analisarmos a necessidade do negocio e baseado nisso propor o que aquela tecnologia deve conter (Exemplo: Esse projeto necessita de um framework "reactive-based", agora iremos discutir com a equipe qual seria o melhor para a empresa. Angular, Elm, React, Vue, etc).

### Analisar a arquitetura continuamente
*O arquiteto sempre deve estudar a arquitetura e propor melhorias*

Uma arquitetura que foi criada a 3 anos atras, ainda eh viavel nos dias de hoje?

### Se manter atualizado com o que ha de novo no mercado
A ideia que os autores dao nessa parte eh o seguinte: Se o arquiteto ficar atualizado com o que temos de novo no mercado ele podera fazer decisoes melhores de arquitetura que consequentemente vao perdurar por mais tempo.

Honestamente eu concordo com a frase mas a gente precisa tomar muito cuidado com essa afirmacao. Motivo:

Se estivermos falando de um novo modelo de desenvolvimento de software (exemplo devsecops), ai beleza, saber isso e colocar essa pratica pode salvar dinheiro pra empresa e tambem ficar atualizado com o mercado

Se estivermos falando do ultimo framework JS que saiu eu discordo completamente, isso pq essas tecnologias embrionarias se mostraram muito instaveis e nao tao duradouras (tenho essa percepcao justamente pelo famoso teste do tempo)

Sendo assim concluo que: Eh interessante ir e participar de eventos de TI, mas sempre tomando cuidado pra nao ser alvo de "modinhas" de tecnologia que existem por ai

### Garantir que compliance esta sendo seguido
Significa que o arquiteto precisa garantir que o time esta seguindo as decisoes de arquitetura (ou seja, regras) e principios de design (diretrizes).

Esse ponto pode facilmente ser alcancado colocando o arquiteto de software na revisao de pull requests (exatamente como a Vivo faz)

### Ter experiencias variadas durante a carreira
Esse aqui eh auto-explicativo, um arquiteto nunca pode ficar na sua zona de conforto, sempre deve se expor a tecnologias, plataformas, problemas diferentes.

Nessa parte eh interessante como o livro diz que eh melhor ser generalista do que especialista. Eh importante focar em saber pq A eh melhor que B daquela determinada situacao, mas nao necessariamente voce ganha muito sabendo A muito profundamente mas nao tendo ideia do que B eh capaz

### Ter dominio da logica de negocio
Alem de codigo eh preciso conhecer a empresa. Nao da pra saber qual eh a melhor solucao pro cliente A se eu nao tenho ideia do que o cliente A precisa

### Ter habilidades interpessoais
O mundo eh feito de pessoas nao de computadores, precisa aprender a falar com as pessoas sem parecer um lerdao

### Entender de politicas da empresa
Nessa parte os autores do livro nao trata de politica no sentido de ordens a serem seguidas e sim de politico (tipo os bandidos de terno e gravata).

Basicamente a ideia eh a seguinte. Se o dev quiser ao inves de fazer organizacao A fazer a B ninguem (ou quase ninguem) vai ligar pro que ele fez.

Agora se um arquiteto quiser mudar uma parte do sistema deus e o mundo vai pedir uma explicacao do pq foi feito isso. Nessa hora o arquiteto precisa saber negociar com todos aqueles que o colocaram a prova do pq sua implementacao eh a melhor

# Leis da arquitetura de software (segundo o livro)
Tudo sempre tem um trade-off
Se voce descobriu algo sem trade-off provavelmente voce nao encontrou o trade-off ainda
*Por que* eh mais importante do que *como*