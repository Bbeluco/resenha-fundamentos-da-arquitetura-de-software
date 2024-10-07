Eh de suma importancia que o arquiteto trabalhe bem proximo aos desenvolvedores. Isso pq quando ele faz isso ele cria um melhor entrosamento entre a equipe, respondendo rapidamente todas as duvidas que os devs possam ter sobre a implementacao. Isso vai garantir que o que sera implementado sera feito de forma rapida e assertiva

# Limitacoes da equipe
Um bom arquiteto deve saber os limites de sua profissao, nessa etapa o livro afirma o seguinte:

_Se criarmos uma arquitetura muito rigida os devs nao terao espaco de fala e ficarao frustados_
_Se criarmos uma arquitetura com muitas pontas soltas os devs ficarao confusos_

O papel do arquiteto eh encontrar um equilibrio, muita das vezes permitindo com que os devs expressem suas opinioes sobre determinado tema na arquitetura

# Perfis de arquitetos
O livro levanta que existem 3 tipos de arquitetos

- Controlador (a equipe nao pode sugerir nada, tudo tem que ser do jeito dele)
- Desleixado (ele nao passa em detalhes o que a equipe tem que fazer, ele so fala pro pessoal fazer e ja era)
- Efetivo (ele sabe os limites da sua profissao e ao mesmo tempo lidera a equipe para atingir seus objetivos)

# Quanto de controle aplicar?
Isso vai depender de uma serie de fatores, alguns deles sao

- Familiaridade da equipe
- Tamanho da equipe
- Experiencia dos envolvidos
- Complexidade do projeto
- Duracao do projeto

# Team warnings
Eh interessante como no livro eles citam a lei de brook (nao importa se voce tem mais desenvolvedores sendo adicionados ao projeto, isso nao muda o fato que o projeto acabara em X tempo), porem eles citam o ponto de **process loss** eh interessante que se tiver a possibilidade de paralelizar uma atividade (sem colidir com o codigo do outro) a produtividade eh aumentada. Logo, o correto ponto de vista seria o seguinte

> Podemos sim adicionar mais desenvolvedores a um projeto, desde que eles nao trabalhem na exata mesma parte do sistema

**Ignorancia plurarista**: Esse tema tambem merece seu destaque, eh quando um sujeito fica com vergonha de falar um ponto pq a maioria aceitou isso como verdade. Exemplo:

_O arquiteto diz_: Vamos implementar o codigo utilizando tecnologia XPTO
_O dev pensa_: Nao podemos fazer isso por conta da limitacao Y
_Todos os outros da equipe concordam_
_O dev estava certo desde o comeco mas nao falou pois todos ja concordaram_

# Lideranca
Um bom arquieto deve saber guiar seu time nas tomadas de decisao. Um exemplo pra adicao de libs eh

1. Existe alguma sobreposicao entre a biblioteca e nosso sistema atual?
2. Qual eh a justificativa para a nova biblioteca?