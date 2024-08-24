Modularidade nos dias de hoje (2024) ainda nao parece ter uma definicao formal e rigida entre a comunidade. Por conta disso os autores dao a definicao deles do que seria modularidade

Modularidade eh um principio de organizacao.

Organizacao nao acontece por acidente, na verdade existe um esforco sempre maior em manter as coisas organizadas do que desorganizadas (o mesmo conceito de entropia que existe na fisica). Eh papel do arquiteto reservar suas energias em manter o sistema organizado

# Definicao
Modularidade eh um grupo formado por partes menores que tem como objetivo pertencer a estruturas mais complexas.
Os autores tambem gostam de chamar de modularidade todo "pacote" de codigo que estao relacionados. Eh como se eu criase uma ferramenta e essa ferramenta pudesse ser chamada de forma independente durante o codigo

-------------------------------------------------------

Eh papel do arquiteto garantir que o desenvolvedor nao crie acoplamentos rigidos no codigo

# Medindo modularidade
Existem 3 pilares principais para medirmos modularidade:
- Coesao
- Acoplamento
- Connascência

# Coesao
Significa: O que temos nesse modulo (parte do sistema) deveria realmente estar aqui?

Tem uma visao interessante dos autores nesse trecho que eles falam que tudo que esta relacionado deveria ser chamado direto (sem criar por exemplo um utils). Eles argumentam que caso quebre precisara realizar chamadas do pacote para so depois conseguir acessar a funcionalidade que por sua vez gera acoplamento e diminuir a legibilidade do codigo

Na area dos estudiosos foi criado um modelo matematico para saber se seu codigo tem uma alta coesao ou nao, esse modelo tem a sigla LCOM (recomendo procurar por isso no google).

No resumo o que esse modelo implica eh o seguinte:

Tudo que temos dentro da nossa classe esta sendo usado? Todos os nossos metodos estao sendo usados por nossos "autores" (Tem uma imagem excelente no livro que descreve isso, eh a figura 3-1). Se todo mundo tiver usando tudo que tem na classe (pelo menos 1 vez), maravilha vida que segue. Se tivermos um codigo separado eh melhor extrair esses metodos.

# Acoplamento
Acoplamento eh o que conhecemos (um codigo eh fortemente dependente do outro), isso nao tem necessariamente haver com coesao, sao coisas diferentes.

Assim como coesao o pessoal criou um modelo matematico pra tentar metrificar esse ponto. O modelo eh o seguinte:

Abstracao = (Σ elementos abstratos) / (Σ elementos concretos)

elementos = funcoes, classes, interfaces, etc.
Abstrato = a palavra abstract que a gente tem na programacao mesmo
concretos = implementacao dessas abstracoes

Em uma equacao como essa uma relacao proxima de 1 eh sempre o alvo.

## Pq abstracao eh importante
A abstracao eh um recurso importante quando pensamos em facilitar reusabilidade de codigo e tambem facilidade de leitura.

O livro cita alguns outros modelos matematicos existentes que procuram relacionar um balanco entre abstracoes e implementacoes concretas. Isso se faz necessario pois segundo as palavras do livro:

*Codigos muito abstraidos sao dificeis de utilizar, enquanto codigos pouco abstratos sao dificeis de se realizar manutencoes*

# Connascência
Eh quando a alteracao no componente A precisa necessariamente afetar o componente B para o codigo continuar funcionando. 

Isso pode envolver desde nome de classes (quando mudamos o nome da classe todos os imports precisam alterar tambem), pode envolver tambem nome de variaveis (em uma tipagem por exemplo), sistemas que precisam por exemplo de o uso de um hash do lado do cliente e do serivdor, etc