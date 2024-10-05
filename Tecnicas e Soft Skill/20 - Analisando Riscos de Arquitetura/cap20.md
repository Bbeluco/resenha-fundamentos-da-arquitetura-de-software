# Matrix de Risco
Toda arquitetura tera riscos atrelados a ela, eh papel do arquiteto identificar quais sao esses riscos, se eles sao aceitaveis e como fazer pra mitiga-los ao maximo. Geralmente classificamos entre low, medium e high. Dentro dessas classificacoes nos nao podemos deixar simplesmente de forma subjetiva a ponderacao desses riscos, foi pensando nisso que uma matrix de risco foi criada

|        	| Low 	| Medium 	| High 	|
|--------	|-----	|--------	|------	|
| Low    	| 1   	| 2      	| 3    	|
| Medium 	| 2   	| 4      	| 6    	|
| High   	| 3   	| 6      	| 9    	|

O "eixo X" representa a probabilidade do erro ocorrer enquanto o "eixo Y" representa o impacto geral desse risco.

Quando nos cruzamos essas informacoes na tabela nos conseguimos ter uma melhor dimensao do que acontece. Por exemplo:

Supondo que temos uma arquitetura service based onde ha somente 1 banco de dados pro sistema inteiro. Se esse banco de dados cair, qual eh o impacto para a aplicacao? Todos concordamos que o impacto eh alto, logo, no "eixo Y" vamos procurar pela coluna de alto e temos como resultado 9. Agora em questao de probabilidade vamos supor que esse DB esta hospedado na nuvem com uma redundancia enorme nele, entao podemos concluir que a probabilidade do banco cair eh baixa, logo vamos atribuir o "eixo X" o valor referente a low. Tendo em vista isso, nosso resultado final eh 3

# Avaliacao de Riscos
A avaliacao de risco nada mais eh do que pegar o risco que ja temos catalogado na matrix de risco e colocarmos em outra tabela, dessa vez considerando outros fatores, como por exemplo:

| Risk Criteria 	| Customer Registration 	| Catalog Checkout 	| Order fulfillment 	| Order Shipment 	| Total Risk 	|
|:---:	|:---:	|:---:	|:---:	|:---:	|:---:	|
| Scalability 	| 2 	| 6 	| 1 	| 2 	| 11 	|
| Availability 	| 3 	| 4 	| 2 	| 1 	| 10 	|
| Performance 	| 4 	| 2 	| 3 	| 6 	| 15 	|
| Security 	| 6 	| 3 	| 1 	| 1 	| 11 	|
| Data Integrity 	| 9 	| 6 	| 1 	| 1 	| 17 	|
| Total Risk 	| 24 	| 21 	| 8 	| 11 	|  	|

Repare que nesse tipo de tabela o resultado de cada celula eh a matrix de risco.

# Risk Storming
Eh muito arriscado um arquiteto sozinho levantar todos os pontos de risco de um sistema, isso pq a visao dele pode estar limitada (por nao ter conhecimento pleno do sistema) ou ate mesmo ele pode ponderar coisas com um risco maior/menor do que realmente tem. Pensando nisso foi criada a dinamica de _risk storming_, ela consiste em basicamente fazer um brain storm so que de riscos. Os pontos principais sao:

- Identificacao
- Consenso
- Mitigacao

## Identificacao
Nessa etapa todos os envolvidos vao levantar os riscos do sistema (no formato brain storm mesmo) baseando-se nos diagramas de arquitetura que o arquiteto enviou anteriormente para a equipe, a matrix de risco sera usada para ponderar os riscos que cada participante levantou.

Valido falar que nessa fase podemos focar em so um ponto de "-ilities" ao inves de todos os pontos da avaliacao de risco, isso faz com que a reuniao seja menor e centrada apenas em um unico ponto

## Consenso
Aqui o orquestrador da reuniao vai pegar a opiniao individual de cada um sobre determinado risco e colocar na mesa, o intuito aqui eh todos entrarem em um consenso sobre os riscos que serao tomados.

Um fato interessante eh que na etapa anterior alguma pessoa envolvida na reuniao pode nao saber o que seria determinada tecnologia, nesse caso sempre atribua o maior risco possivel.

## Mitigacao
Apos todo mundo entrar em um consenso chegou a hora da gente mudar a arquitetura para tentar diminuir o grau de riscos apresentados, mesmo que tenha que mudar toda a arquitetura para diminuir determinados riscos

