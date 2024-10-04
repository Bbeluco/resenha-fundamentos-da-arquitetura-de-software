Esse eh o tipo de arquitetura mais presente pelas empresas, ela reflete muito bem o que seria a lei de Conway

> Organizacoes criam sistemas baseados na comunicacao que elas apresentam

Significa que se a empresa se comunica separando a API do banco de dados ha uma enorme change dela dividir seu sistema assim tambem.

# Topologia
A topologia nesse caso nada mais eh do que a forma em que dividimos as camadas do nosso sistema, ela nao precisa possuir um limite de tamanho e nem de tipos. Os tipos mais comuns de camadas sao:

- Apresentacao
- Negocios
- Persistencia
- Banco de dados

Repare que aqui os autores colocam "persistencia" e "banco de dados" como coisas separadas, a interpretacao que fica nesse caso eh que alem de separar logicamente dentro do codigo as camadas usadas na aplicacao separamos tambem a nivel de tecnologias.

O modelo descrito tambem como comum no livro eh o que hoje conhecemos como "MVC" (Model, View, Controller).

No livro, a topologia eh citada de forma que o deploy da aplicacao eh impactado diretamente. Podemos entao afirmar que se preocupar com **a topologia da aplicacao impacta tambem as _caracteristicas arquiteturais_ dela**. Como por exemplo: Deployability, testability, etc.

A topologia se preocupa diretamente com o **separation of concerns**. Isso facilita e muito a vida do dev e da pessoa que esta revisando o codigo, isso pq sabemos que tudo que estiver naquela determinada camada so servira exclusivamente para um proposito.

O **tradeoff** que temos eh em questao da **agilidade**, isso pq como temos tudo separadinho em camadas, se quisermos adicionar algo temos que mudar todas as camadas do projeto para fazer com que o novo codigo se adeque. Isso nao parece ser muito um problema na minha opiniao tendo em vista que ganhamos muito mais na parte dos devs entenderem mais rapido e produzirem mais rapido por conta de codigo organizado.

Esse tipo de arquitetura visa realizar separacoes da forma **techinical partitioned** (significa que vamos separar as responsabilidade de forma tecnica). Diferente de outras arquiteturas que separam por domain-partitioned que significa que vamos separar a demanda por dominio

# Camadas de isolamento
Em arquiteturas modernas, as camadas em nosso sistema so se comunicam com a camada imediatamente abaixo. Exemplo:

Controller -> View -> Model

Repare que a camada de controller nao chama a model diretamente, isso significa que o sistema tem a arquitetura de camada **fechada**. O oposto disso seria a arquitetura de camada aberta.

_Por que fechariamos as camadas da nossa aplicacao?_
Quando fechamos as camadas, garantimos que quando formos efetuar uma alteracao no nosso sistema o impacto sera minimo (no maximo na camada imediatamente apos a que estamos alterando). Isso significa que vamos diminuir o nosso acoplamento (tendo em vista que o sistema todo nao vai mudar por causa de um unico ponto).

Como tudo na arquitetura eh um tradeoff o que temos que abrir mao nesse caso eh de novo em relacao a agilidade. Isso pq como o sistema esta fechado temos que trafegar a informacao por todas as camadas ate chegar onde propriamente a gente quer

_Entao quer dizer que sempre devemos deixar a arquitetura de camadas fechada?_
Nao, existem casos onde por algum motivo componentes de camada diferentes precisam compartilhar da mesma informacao, nesses casos eh factivel que a gente deixe a camada de forma aberta. Um exemplo seria uma classe utils, eh interessante que toda a aplicacao veja ela

## Archtecture Skinhole
Esse anti-pattern diz que nao vale a pena so pegar a informacao e transportar entre as camadas. Eh interessante que cada vez que a informacao passar pelas camadas ela seja processada de uma forma diferente. Se ha apenas um transporte ocorrendo isso nao eh interessante que fique so a nivel de camadas.
Obvio que isso vai acontecer durante o projeto, mas que sejam apenas a menor parte das requisicoes que caiam nesse caso (a regra do 80-20 pode te ajudar a podenrar nesse caso)

# Pq usar esse tipo de arquitetura?
Barata, facil de usar, cabe muito bem em projetos pequenos, escala muito bem com novas regras.

O problema eh que ela parece ser uma arquitetura que se resolve em um monolito, o que significa que voce teria problemas pra escalar essa aplicacao e talvez tivesse que quebrar mais depois