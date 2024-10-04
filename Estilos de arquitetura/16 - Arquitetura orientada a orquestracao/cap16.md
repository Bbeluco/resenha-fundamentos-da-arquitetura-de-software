Essa arquitetura no geral foi esquecida com o tempo. Muito pq ela so cabe em cenarios hiper especificos entao o pessoal acabou largando.

Pelo que eh demonstrado no livro a ideia aqui eh quebrar a camada de servicos da empresa o quando fosse necessario, a granulacao presente nessa arquitetura eh bem bem alta. Um outro ponto que prejudicou bastante essa arquitetura era saber fazer o balanco entre reusabilidade e acoplamento, como esse balanco eh muito dificil de fazer e o pessoal vai atras da reusabilidade aqui eles simplesmente criavam uma arquitetura incrivelmente truncada

Eles quebravam os services em

- Business Service
- Enterprise Serive
- Application Service
- Infrastructure Service

## Business Service
Nessa camada nao existe codigo, apenas input e output de dados. Ela serve como entrypoint da aplicacao

## Enterprise Service
Pela forma que eh descrita no livro lembra muito um microservico, so que em escala ainda menor. Uma equipe desenvolve uma funcionalidade (aqui temos uma granulacao alta) e depois quando a gente junta tudo isso fica mais reaproveitavel

Esse paragrafo anterior tras a mesma ideia daquela arquitetura Atomica que existe hoje em dia para frontend (criamos um atomo, uma molecula, uma celula e um corpo)

A ideia dessa camada eh que codigo nunca seria duplicado pq no final iriamos juntar tudo e nao tinha pq reescrever codigo. No fim isso se mostrou errado pq software nao eh igual a um lego, sempre vamos ter um ecossistema vivo com especificidades e tudo mais seja por tecnologias utilizadas, tempo de mercado e etc

## Application Service
Essa camada era responsavel por manter codigo nao necessariamente reutilizavel. As vezes tinhamos cenarios que caiam em regras de negocio especificas, esses eram englobados por essa camada

## Infrastructure Service
Aqui ficavam coisas que diz respeito mais a parte operacional, coisas como logs e auth

## Orquestrador
Esse cara eh o responsavel por ligar todas as pontas do sistema apresentadas ate entao. Geralmente a equipe que era responsavel por cuidar especificamente dessa parte se tornava um gargalo pra organizacao pois eles por conhecerem muito bem o sistema nao flexibilizavam as regras para permitir alteracoes bruscas

# Pq usar esse tipo de arquitetura?
Essa aqui o melhor eh nem usar kkkk

Todas as caracteristicas que o livro cita de qualquer arquitetura ou nao existem ou sao pouco focadas isso pq ela eh uma arquitetura muito antiga onde esses conceitos ainda nao estavam bem definidos. Eh bom saber que uma arquitetura dessa existiu pois ela precede um pouco da ideia que temos de microservicos hoje em dia mas usar ela nao eh uma boa ideia nao