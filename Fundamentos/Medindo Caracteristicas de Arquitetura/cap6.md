Antes da gente medir precisamos entender o que eh a medida de caracteristica que estamos trabalhando. Nos dias de hoje ainda temos caracteristicas de arquitetura que nao estao bem definidas e que caso a organizacao nao tenha bem descrito do que se trata pode acabar gerando confusao aos arquitetos.

Por exemplo: O que eh deployability e agility na arquitetura?

falar sobre esses temas pode ser meio confuso, entao antes mesmo de medir eh necessario que a empresa tenha bem definido o que sao as caracteristicas de design que estao trabalhando

# Medidas operacionais
Esse tema em entrar em consenso eh super importante inclusive em casos onde parece que tratamos da mesma coisa. 

Por exemplo: Falando em *performance* o que seria o aceitavel para pegar de base?
Seria a media? Percentil?

Isso eh importante saber pois ate mesmo se pegarmos 1 dia por exemplo que o percentil esta ruim e a media esta boa pode haver divergencia entre o pessoal

Por conta disso, sempre se tratando de caracteristicas de arquitetura eh importante que **todos** estejam na mesma pagina

# Medidas estruturais
Medidas estruturais sao tudo aquilo que nao sao relacionadas a operacao, por exemplo qualidade de codigo.

A qualidade de codigo eh um item que impacta a arquitetura mas entra naquele modelo de: *nao importa como voce fez, eu so quero que funcione*

Valido ressaltar que nao eh pq o time de negocio nao ta interessado em como voce coda que vc tem que sair fazendo tudo de qualquer jeito. Um codigo de qualidade (ou seja, organizado e bem estruturado) eh de extremo valor para a organizacao tendo em vista que os devs vao trabalhar de forma mais tranquila

### Complexidade ciclomatica
Medida criada em 1976 para determinar a partir de teoria dos grafos a **complexidade do codigo**
A formula para calcular a complexidade eh a seguinte:

CC = Possiveis decioes - Linhas de codigo + 2

_Qual eh um bom numero para CC?_
Nao existe resposta certa para esse problema. Os proprios autores do livro discordam do pessoal (Geralmente o pessoal fala que 10 eh um bom valor mas no livro eles defendem a ideia de 5)

Em resumo, so nao deixa o numero ficar muito alto que dai ce nao tem muito problema

# Medidas de processos
Por mais que o titulo do subcapitulo seja esse o que o pessoal quer passar de ideia eh o seguinte

O que o arquiteto de software tem que pensar para nao impactar nossos processos?

Se a organizacao pede **agilidade** por exemplo, nao da pra simplesmente subir rapido e nao garantir qualidade, logo, precisamos como consequencia melhorar aspectos de **testabilidade** do nosso codigo. Tambem nao da pra ser agil e o deploy demorar um ano, logo, precisamos **fazer deploys mais rapidos**

Isso tudo sao coisas que dependendo da autonomia do arquiteto ele pode pensar (atualmente eu trabalho no cliente o arquiteto de software pode impactar questoes de testes mas nao questoes de deploy)

# Governanca
Governanca deriva do grego *kubernan* quer dizer **dirigir**

O livro deriva dessa ideia de governanca o que ele chama de *Fitness function*. Basicamente eh voce virar pro dev e falar:

Faca a coisa A

Para garantir que o dev fez a coisa A de forma correta voce cria funcoes no codigo (normalmente testes) e faz o dev passar esses processos.

(Minha opiniao sobre esse tema eh que pode ate funcionar um pouco, mas no cliente atual que estou nao sei se valeria a pena. Essa ideia eh boa se o pessoal ficar em cima durante os testes, na pratica a empresa define 90% de coverage e o que nao passar o pessoal simplesmente esquece)

Valido lembrar que isso nao eh imposto e sim dialogado com o time de dev

Uma frase nesse livro foi bem marcante e deriva do que eu fui ensinado

**Erramos naquilo que costumamos fazer todo dia**

Essa frase eh verdade, eh por isso que eh recomendado o uso de fitness function, ela serve como um checklist para garantir que o dev vai conseguir notar aquele padrao de erro antes que aconteca