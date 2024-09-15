O conceito de microkernel ja eh bem antigo, a ideia dele eh simples. Voce cria um pacote e disponibiliza isso para seu usuario, eh basicamente um monolito grande para download.

Ao decorrer do capitulo os autores mostram que nao existe apenas um monolito, eh um pouco confuso mas a ideia de monolito vai se aplicar somente para o **core** da aplicacao, os plug-ins podem ser obtivos atraves de requisicoes rest, chamadas em fila, etc. A ideia de microkel nao morre pois no caso dessa arquitetura o que conta eh se o core dela eh monolito e a forma de deploy pro usuario final

# Topologia
Geralmente essa arquitetura eh dividida em 2 partes, o _core_ e os _plug-ins_. Eh meio auto-explicativo o que cada um faz, o core eh tudo aquilo que sua aplicacao nao vive sem enquanto os plug-ins sao tudo aquilo adicionado de forma a trazer mais funcionalidades para sua aplicacao.

A ideia de uma topologia assim eh desacoplar grande parte das coisas nao essenciais, isso traz expansividade, reduz complexidade ciclomatica, aumenta a manutenabilidade e melhora os testes do seu projeto

### plug-ins
Um plug-in nada mais eh que um codigo que anexado ao seu projeto te trara mais funcionalides. Eles podem ser **compile-based** ou **runtime-based**.

Runtime-based = Podemos adicionar/remover do nosso projeto sem precisar redeployar a aplicacao
Compile-based = Esses sao mais simples de gerenciar mas requer um redeploy de toda a aplicacao

# Registradores
A ideia de registradores no caso desse tipo de arquitetura eh bem simples, vamos ter um local que vai nos dizer onde estao os plug-ins (isso caso vc opte por fazer um microkernel com plug-ins distribuidos). Entao pode ser desde um map indicando a chave e o valor (sendo eles o nome da sua funcionalide e o local que ela se encontra) como coisas mais complexas que envolvam bibliotecas externas para auxiliar

# Contratos
Tem a exata mesma ideia de um contrato de microsservicos, a gente cria um padrao de JSON ou XML que vamos seguir onde as 2 pontas vao pegar essa informacao e fazer o que for necessario

# Pq usar esse tipo de arquitetura?
Simples e barata. Tem escalabilidade, tolerancia a falha e extensao muito ruins por conta de ser um monolito em essencia