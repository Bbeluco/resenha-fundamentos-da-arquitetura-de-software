Essa arquitetura eh fortemente atrelada a um conceito conhecido como _request based model_

Funciona basicamente assim:

- Uma request chega no sistema
- A request eh enviada a um orquestrador
- Esse orquestrador sera o responsavel por dizer para qual processamento ela vai
- o processo eh feito e o processador devolve para o orquestrador essa informacao

A ideia da arquitetura ser dirigida por eventos ocorre justamente pelo fato que quem da o start nela de fato sao eventos oriundos do proprio sistema. Uma coisa eh o usuario requisitar uma informacao diretamente, outra coisa eh o sistema apos requisitar uma informacao disparar um evento.

Nesse caso, evento eh quase como se fosse algo com efeito colateral, enquanto _data-driven_ seria o proprio usuario requisitando a informacao

# Topologia
Existem 2

- Broker Topology
- Mediator Topology

## Broker topology
A principal diferenca entre o broker e o mediator eh que aqui nao temos um mediador de eventos central. Esse tipo de topologia eh util quando temos um evento bem simples a ser processado e nao precisamos coordenar nem orquestrar ele

Geralmente em uma topologia Broker temos 4 componentes principais

- Evento inicial = Isso eh o que da o start na nossa aplicacao
- Event Broker = Eh como se fosse um canal que vai ouvir nossos eventos e direciona-los
- Event processor = Processa o evento
- Processing event = Isso aqui na verdade eh o **resultado** do que o nosso event processor gerou

Esse evento descrito acima ocorre em loop apos a etapa de *evento inicial*, os event brokers sao responsaveis por transitar o resultado para todos os event processors necessarios de modo que o processo so acaba quando ninguem mais quiser essa informacao.

Uma recomendacao que os autores dao no livro eh que caso a gente crie um evento que gera um resultado X, devemos mandar esse resultado para todo nosso sistema (atraves dos event brokers) de modo que mesmo que ninguem use todos fiquem sabendo. Eles argumentam no livro que se no futuro alguem precisar consumir essa informacao ela ja esta la e que precisariamos do minimo de esforco possivel pra usar ela. Honestamente eu acho que isso so aumenta ainda mais a complexidade, tendo em vista que a pessoa nova no sistema vai ver que tem um evento que existe so por existir.

Da forma que o exemplo da pagina 183 eh descrito, parece muito que essa estrutura seria um enorme pub/sub (igual temos no RabbitMQ)

Pontos negativos dessa abordagem eh que como nao temos um maestro central as informacoes acabam indo de um lado para o outro e nao conseguimos estabelecer muitos controler em cima disso. Como temos diferentes entidades que acabam escutando do mesmo broker, se uma falhar temos um caos completo pois nao teremos a informacacao indo pro sistema do que ta acontecendo.

Como tem muita coisa acontecendo de forma assincrona nesse tipo de topologia eh muito dificil garantir atomicidade nas operacoes do banco (nao pelo fato de ser 1 coisa assincrona, mas sim pelo fato de VARIAS entendidades olharem pro banco de forma assincrona)

## Mediator topology
Esse caso eh praticamente a mesma coisa do broker, com a diferenca que teremos um orquestrador central que vai ditar para onde vao as requisicoes e estados do sistema.

Os componentes principais dessa topologia sao:

- Initiation event = Da o start no sistema
- Event Queue = A requisicao apos o start vem pra uma fila
- Mediator = Esse cara eh o resposavel por saber da onde a req veio e pra onde ela vai
- Event channel = Eh a mesma coisa que brokers, so que nesse caso eh uma fila passando pra outra fila
- Event processor = Processa o evento e devolve pro channel (que por sua vez vai devolver pro mediador)

Esse sistema tem um ponto de falha bem obvio que seria a parte do _mediator_, pra cobrir esse ponto de falha geralmente o pessoal escala essa parte do sistema segregando o mediator por dominio ou coisas do tipo

Diferente do broker aqui temos um orquestrador, isso significa que a informacao nao vai sair andando pelo sistema sem controle. Essa abordagem de mediator adiciona uma maior capacidade de lidar com erros, recuperar o estado do sistema, etc.

Diferente da topologia broker, aqui nao temos aquele modelinho de pub/sub e sim temos um modelo quase que sequencial. Quem coordena essa sequencia eh um maestro

Pontos negativos dessa abordagem eh que o primeiro gargalo do sistema vai ser o mediator, o processo nao eh tao desacoplado (ja que sempre vai ter que ser acoplado ao maestro)

# Capacidades assincronas
Sabemos de todo o poder de tratamentos assincronos, podemos simplesmente derrubar um tempo de resposta em 5, 10, 15 ou milhoes de vezes so por fazer um tratamento assincrono.

Aqui os autores falam tambem de **responsividade** e **performance**

_O segredo nao eh o seu sistema ser performatico, eh parecer performatico_

Imagine que publicar um comentario leve 3 segundos (considerando todas as validacoes e latencias de rede). O seu usuario nao precisa esperar 3 segundos pra ver o comentario que ele mesmo criou, ele pode ver esse comentario instantaneamente e de forma assincrona voce esta tratando as validacoes para colocar o comentario dele na rede.

Esse eh o poder de tratamentos assincronos e tambem da responsividade

# Escolhendo entre Request-based e Event-based
Request-based = Quando precisamos de controle no workflow (nao da pra fazer tudo async), quando somos orientados a dados (data-driven) e quando precisamos de forte centralizacao no sistema

Event-based = Quando precisamos de niveis altissimos de escalabildade, flexibilidade alta, quando o processamento do usuario precisa ser hiper dinamico

# Pq usar esse tipo de arquitetura?
A performance e escalabilidade nesse tipo de arquitetura nao eh visto em nenhuma outra a tolerancia a falhas tambem eh boa.

As desvantagens eh que ela eh muito, mas muito complexa entao testes sao dificeis de fazer e simplicidade simplesmente nao existe