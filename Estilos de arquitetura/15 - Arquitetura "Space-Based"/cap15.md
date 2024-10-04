Interessante como nesse capitulo logo no comeco os autores realizam a seguinte afirmacao:

_In any high-volume application with a large concurrent user load, the database will usually be the final limiting factor in how many transactions you can process concurrently._

# Topologia
A ideia dessa aplicacao eh tirar o gargalo quando precisamos escalar e o database vai ficar atrapalhando nossa vida. O plano eh mais ou menos o seguinte:

Vamos colocar todos os nossos dados em memoria (que por si so ja eh mais rapido que DB). Se por algum acaso a gente precisar atualizar algum dado da memoria a gente atualiza e manda um sinal pro database atualizar de forma **assincrona** tambem. Depois que o database atualizar ele avisa pra todo mundo qual eh o novo dado que precisa estar na memoria.

Dessa forma, como o foco da informacao nao eh se manter no banco de dados e sim na memoria removemos o gargalo

Itens comuns na topologia sao:
- Process unit
- Virtualized middleware
- Data pump
- Data wire
- Data reader

## Process unit
Contem a logica da aplicacao + in-memory DB
Se a aplicacao for pequena podemos criar um monolito de process unit, se for grande eh melhor quebrar em microservicos

## Virtualized middleware
Responsavel por lidar com as requests e tambem com a sincronizacao dos dados que vai ficar nas memorias da process unit

### Message grid
Guarda estado da sessao e input request. Em relacao a input request ele atua basicamente como um reverse proxy, ele olha pra onde eh melhor mandar a requisicao e assim o faz

### Data grid
Aqui eh basicamente a conexao entre o middleware e as memorias internas de cada _process unit_. Eh aqui que todo o conceito da arquitetura mora, em linhas gerais o papel desse cara eh sincronizar toda a questao de banco de dados dentro dos caches presentes em cada unidade de processamento

Eh interessante que essa conexao nao acontece somente entre o data grid e as unidades de processamento. Acontece tambem **entre** as unidades de processamento. Basicamente as unidades conhecem o data grid e todas as outras que estao perto dela. Quando alguma informacao atualiza as unidades primeiro podem perguntar umas as outras antes de consultar o BD em si

### Processing grid
Esse cara eh opcional, usamos quando numa request so eu preciso acessar 2 ou mais unidades de processamento distintas

### Deployment manager
Ele orquestra o liga/desliga das unidades de processamento (usado pra trazer escalabilidade e elasticidade pra aplicacao)

## Data pump
Eh uma forma de enviar dados a um outro processo que ira atualizar o banco de dados. Geralmente enviamos por uma fila (modo FIFO) as informacoes que deverao ser atualizadas.

Ele tem uma funcao similar a um broker visto na "Arquitetura direcionada a eventos/cap14.md"

## Data writers
Pega a informacao que recebeu do _data pump_ e atualiza o banco de dados. Podemos ter 1 ou N data writers nesse tipo de arquitetura, vai do que os arquitetos acharem melhor. Lembrando que quanto mais data writers tivermos mais escalavel a aplicacao fica (em contra-partida mais complexa tambem)

## Data readers
Le as informacoes do banco de dados e envia para as _process unit_ atraves dos data pumps. Eles raramente sao usados (isso pq as process unit vao se atualizando entre si). Mas quando temos algum evento extraordinario (crash de sistema ou process unit sem informacao em cache) recorremos a esse cara.

# Colisao de dados
A colisao de dados vai acontecer quando o cache B atualiza no mesmo momento que o cache A iria passar a informacao para sincronizar. Vamos imaginar assim

- Estoque inicial 500 unidades
- Componente A vende 10 unidades (estoque agora 490)
- Cache A salva a informacao 490 e envia um sinal para outros caches
- Componente B vende 5 unidades (estoque agora 495)
- Cache B ainda nao sincronizou com cache A, mas como ele fez essa operacao ele sobescreveu e agora ja eh tarde

Existe uma forma que calcula a chance das informacoes colidirem, essa formula eh:

CollisionRate = N * (UR^2 / S) * RL

N = numero de instancias de servico que esta rodando (process units)
UR = update rate (medida em milisegundos ao quadrado)
S = tamanho do cache
RL = replication latency

# Cloud X On-Premise
Nesse caso podemos colocar tudo on-prem ou tudo na cloud. Os autores falam que existe ganho em deixar tudo menos os _data writers_ e _banco de dados_ em cloud. Dessa forma voce tem um controle melhor das suas informacoes

# Pq usar esse tipo de arquitetura?
Ela eh boa em casos que a gente sempre tem um volume pequeno de dados e do nada entra muita gente na nossa aplicaca (como num site de venda de ingressos por exemplo).

Essa arquitetura tras escalabilidade, elasticidade e performance como sendo seus pontos principais, em contra-partida ela eh complexa e dificil de testar