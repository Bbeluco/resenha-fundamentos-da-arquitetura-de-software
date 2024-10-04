# Diferenca entre: Arquitetuar de software, codigo e design

A diferenca principal seria que o papel do arquiteto seria levantar os requisitos de um sistema (para garantir a conformidade com o que o cliente solicitou). 

*Podemos considerar isso requisitos funcionais?*
NAO, requisitos funcionais eh aquilo que o cliente solicita como funcionalidade que deseja que o sistema tenha, **como / por que** vai ser feito essa funcionalidade eh a ultima coisa do mundo que ele quer saber. Para esses casos um termo comum sao *requisitos nao funcionais* (os autores nao gostam dessa fala pois implica em algo negativo, se nao eh funcional o time tecnico nao precisaria prestar atencao. No livro eles preferem o termo **Caracteristica da Arquitetura**)

# Caracteristicas Arquiteturais
Essas caracteristicas possuem 3 pilares

- Especificar consideracoes de "nondomain design"
- Influenciar aspectos do design
- Eh critico ou importante para o sucesso do negocio

### Especificar consideracoes de "nondomain design"
Temos as regras de negocio que o time de negocio passou, a parte de nondomain design serve justamente para a comunicacao do arquiteto para com o time. Seria basicamente um **como** a aplicacao vai ser construida e um **por que** ela vai ser construida dessa forma

### Influenciar aspectos do design
Fatores inerentes ao projeto que precisam ser levados em consideracao para que este saia bem. Exemplo seguranca, performance, consumo de informacoes de terceiros, etc.

O arquiteto precisa levar em conta esses fatores pois as vezes deve haver um tratamento especial para que se alcance certo nivel de qualidade a tratar desses assuntos. Tratamento especial entenda: redundancia, escalabilidade, seguranca, etc.

### Eh critico ou importante para o sucesso do negocio
Podemos fazer decisoes de arquitetura complexas a todo momento, se quisermos o projeto inteiro pode ter N caracteristicas diferentes. Porem isso nao eh nem um pouco viavel, a cada decisao de arquitetura complexa que fazemos aumentamos o nivel de esforco que precisaremos fazer para aquele projeto se manter. Eh papel do arquiteto tentar encontrar o equilibrio entre desenvolver novas caracteristicas ou manter as coisas mais simples