Eh fundamental que um arquiteto realize **estruturacao da aplicacao/sistema e tecnologias envolvidas**. Uma boa decisao de arquitetura eh fundamentada em informacoes colhidas anteriormente, valido lembrar que o arquiteto deve servir de consultor para os desenvolvedores, logo, sempre a opiniao deles tambem deve ser levada em consideracao

# Anti-Patterns
Segundo o programador Andrew Koenig anti-pattern eh aquilo que parece ser uma ideia boa no inicio mas acaba se tornando um pesadelo no futuro. Os principais anti-patterns catalogados sao:

- Covering Your Assets
- Groundhog Day
- Email-Driven Architecture

## Covering Your Assets
Esse padrao nasce quando um arquiteto demora para fazer uma decisao de arquitetura com medo de fazer a decisao errada. Esse anti-pattern pode ser evitado de 2 formas.

1. Esperando o ultimo momento responsavel para tomar a decisao da arquitetura (momento responsavel entenda um momento que voce nao impacta seu time de trabalhar ao mesmo tempo que tem informacao suficiente pra nao fazer besteira)
2. Acompanhando o desenvolvimento de perto para ver se tudo esta dentro dos conformes

## Groundhog Day
Esse anti-pattern significa que a **equipe** nao tem nocao do pq determinada decisao foi tomada, entao sempre caem em discussoes do pq isso foi feito e nunca evoluem. Equipe na frase anterior esta destacado pq nao apenas a equipe tecnica precisa ter uma clara visao da decisao mas a equipe de negocios tambem (a final de contas, eh de la que vem o dinheiro. Se a solucao do arquiteto nao convencer o pessoal a abrir o bolso ela simplesmente nao vai ser implementada)

## Email-Driven Architecture
Esse anti-pattern significa o seguinte: passamos pelos 2 anti-patterns anteriores e agora simplesmente esquecemos como vai ser a implementacao da arquitetura.

O nome leva "email" pq por mais que o email eh bom pra comunicacao eh **pessimo para documentacao**. Nesse parte os autores focam em falar em como deve ser uma comunicacao por email, mas eu vou me aventurar e deixar a minha interpretacao sobre o melhor local para comunicar sobre decisoes de arquitetura (o que eu falar aqui vale mais para empresas grandes, se a empresa eh pequena melhor seguir o email e os pensamentos dos autores).

Acredito que um bom lugar para salvar decisoes de arquitetura sao em ferramentas de documentacao como um confluence da vida. Nele sera possivel ver atualizacoes de decisoes bem como ter de forma centralizada (disponivel para todos os interessados), informacoes sobre a arquitetura

# O que sao decisoes de arquitetura
Nessa parte os autores referenciam Michael Nygard (autor do livro Release It! (PragmaticBookshelf)), segundo ele podem ser consideradas decisoes de arquitetura:

- Estrutura (decisoes que impactem o padrao da arquitetura)
- Caracteristicas nao funcionais (aqueles "-ilities" citados no comeco do livro)
- Dependencias (pontos de acoplamento no sistema, em linhas gerais impactam escalabilidade, modularidade, etc)
- Interfaces (Componentes e servicos de um sistema coordenado por um orquestrador)
- Tecnicas de construcao (escolha de framework, plataforma, ferramenta, etc)

# Architecture Decision Records 
As **A**rchitecture **D**ecision **R**ecords (ADR) sao documentos que tem como finalidade guardar as informacoes do pq determinada decisao de arquitetura foi tomada. Geralmente esse tipo de documento comporta a seguinte estrutura:

- Titulo
- Status
- Contexto
- Decisao
- Consequencias

## Titulo
Eh literalmente um titulo falando sobre a decisao de arquitetura, exemplo: _42. Use of Asynchronous Messaging Between Order and Payment Services._

## Status
Podemos ter 3 status diferentes sao eles:

1. Proposed (Significa que a gente propos uma decisao de arquitetura que vai ser analisada por outras pessoas)
2. Accepted (Significa que a decisao foi aceita e agora eh so implementar)
3. Superseded (Significa que alguem deu uma decisao melhor de arquitetura e agora estamos largando essa)

## Contexto
Aqui eu descrevo _qual situacao me levou a tomar essa decisao_

## Decisao
Aqui eh meio obvio, eh a decisao de arquitetura que foi tomada. Quando estamos nessa parte eh essencial que a gente foque no **porque** aquela decisao foi tomada ao inves do **como**. O argumento dos autores eh que o "como" eh muito facil da gente entender (qualquer coisa alguns diagramas ja resolvem), agora a parte do "porque" aquela decisao foi tomada pode ser que fique algo meio obscuro e eh por conta disso que devemos focar em descrever melhor essa parte

## Consequencias
Aqui a gente fala quais serao as consequencias que determinada arquitetura trara ao sistema, existem consequencias boas e ruins, ambas devem ser descritas nessa parte do documento