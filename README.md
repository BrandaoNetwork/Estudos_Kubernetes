# Estudos_Kubernetes
Material organizado dentro de meus estudos relacionados ao Kubernetes!
![mod](https://github.com/BrandaoNetwork/Estudos_Kubernetes/blob/main/assets/sensors-22-02869-g001.webp)


>## Pod é a menor unidade no modelo de objetos do Kubernetes.

Ele representa um único processo em execução em um cluster Kubernetes.
Um Pod pode conter um ou mais contêineres, que compartilham o mesmo espaço de rede e armazenamento. Cada Pod é criado com um endereço IP único dentro do cluster, o que permite que os contêineres dentro do Pod se comuniquem entre si.
Os Pods são escalonados e gerenciados pelo Kubernetes, que pode replicá-los para fornecer alta disponibilidade e escalabilidade aos aplicativos implantados no cluster. O Kubernetes também gerencia a programação dos Pods em nós de cluster disponíveis, com base nos recursos necessários pelos contêineres do Pod e nos recursos disponíveis em cada nó.
Em resumo, um Kubernetes Pod é a unidade básica de implantação no Kubernetes, que fornece uma maneira de agrupar contêineres relacionados e gerenciá-los como uma única unidade.

[Exemplo: Pod](https://github.com/BrandaoNetwork/Estudos_Kubernetes/blob/main/pod.yaml)

>## Deployment é um objeto que define o estado desejado de um conjunto de Pods em um cluster Kubernetes.
Ele fornece um mecanismo para atualizar e gerenciar o estado dos Pods em execução em um cluster.
Um Deployment gerencia um conjunto de réplicas de um Pod, garantindo que o número especificado de réplicas esteja sempre em execução. Se houver um problema em um nó ou um Pod falhar, o Deployment garante que um novo Pod seja iniciado para substituí-lo.
Os Deployments também fornecem um mecanismo para atualizar um conjunto de Pods para uma nova versão de um aplicativo de maneira controlada, permitindo uma atualização gradual do estado de execução dos Pods em um cluster. Por exemplo, um Deployment pode ser configurado para atualizar um conjunto de Pods com um novo contêiner de imagem, um novo arquivo de configuração ou uma nova versão do aplicativo.
Além disso, um Deployment pode ser escalado para aumentar ou diminuir o número de réplicas de um conjunto de Pods, permitindo que os aplicativos sejam dimensionados de acordo com a demanda.
Em resumo, um Kubernetes Deployment é um objeto que gerencia a implantação, atualização e escalabilidade de um conjunto de Pods em um cluster Kubernetes. Ele fornece um mecanismo para gerenciar o estado desejado de um aplicativo em execução em um cluster.

[Exemplo: Deployment](https://github.com/BrandaoNetwork/Estudos_Kubernetes/blob/main/Deployment.yaml)

>## DaemonSet é um tipo de objeto no Kubernetes que garante que um determinado conjunto de pods seja executado em todos os nós do cluster ou em um subconjunto específico de nós, dependendo da configuração.
Ele é usado principalmente para implantar daemons, como monitores de registro, coletadores de métricas ou proxies de rede, em todos os nós de um cluster.

O DaemonSet garante que um pod seja executado em todos os nós do cluster, ou em um subconjunto de nós com determinada etiqueta, independentemente da criação ou exclusão de nós. Quando um novo nó é adicionado ao cluster, o DaemonSet implanta automaticamente um pod nele. Da mesma forma, quando um nó é removido do cluster, o DaemonSet garante que o pod correspondente seja removido.
Essa abordagem é útil para garantir que certos serviços, como monitoramento e logging, estejam sempre disponíveis em todos os nós do cluster, mesmo quando novos nós são adicionados dinamicamente.

>## StatefulSet é um objeto no Kubernetes que permite a execução de aplicativos que exigem identificadores persistentes e estáveis para cada uma de suas instâncias.
É uma abstração de mais alto nível em relação a um Deployment, projetada para gerenciar aplicativos de estado, como bancos de dados, cache e sistemas de processamento de fluxo.
Ao contrário dos Deployments, que gerenciam um conjunto de réplicas de contêineres sem identidade ou estado, o StatefulSet é projetado para garantir que cada pod em sua coleção tenha um nome único e persistente e mantenha sua identidade e estado durante todo o ciclo de vida do pod.
Os StatefulSets são úteis para aplicativos que exigem um número fixo de instâncias e onde a ordem de inicialização ou paralisação é importante. Eles também são capazes de lidar com operações de atualização e rollback em aplicativos com estado sem perder dados.
Os StatefulSets são frequentemente usados para gerenciar aplicativos de banco de dados, como o MySQL e o PostgreSQL, e sistemas de processamento de fluxo, como o Apache Kafka.

[Exemplo: StatefulSet](https://github.com/BrandaoNetwork/Estudos_Kubernetes/blob/main/StatefulSet.yaml)

>## ReplicaSet é um objeto que ajuda a garantir que um determinado número de réplicas de pods esteja sempre em execução no cluster do Kubernetes.
Ele é frequentemente usado para garantir alta disponibilidade e escalabilidade de aplicativos em contêiner.
O ReplicaSet é uma versão mais avançada do objeto ReplicationController, que é um dos objetos Kubernetes mais antigos e básicos. Enquanto o ReplicationController gerencia apenas a criação e a exclusão de réplicas, o ReplicaSet oferece suporte a recursos adicionais, como atualizações controladas de aplicativos, balanceamento de carga e seleção avançada de pods.
O ReplicaSet é projetado para monitorar o estado dos pods e garantir que o número desejado de réplicas esteja sempre em execução, mesmo quando os pods falham ou os nós do cluster são adicionados ou removidos. Se houver mais ou menos réplicas do que o número desejado, o ReplicaSet fará as ações necessárias para corrigir o estado atual.
Em geral, os ReplicaSets são usados em conjunto com outros objetos Kubernetes, como Services e Deployments, para implementar aplicativos altamente disponíveis e escaláveis. Eles são uma peça fundamental da arquitetura de orquestração de contêineres do Kubernetes.

>## Replication Controllers no Kubernetes são responsáveis por garantir que um número especificado de réplicas de um pod esteja sendo executado a qualquer momento.
Eles são essencialmente usados para manter o estado desejado do sistema, escalando o número de réplicas para cima ou para baixo com base na configuração fornecida.

No entanto, com a introdução da versão 1.9 do Kubernetes, o Replication Controller foi depreciado em favor dos ReplicaSets. Os ReplicaSets são semelhantes aos Replication Controllers, mas oferecem recursos e funcionalidades adicionais, como a capacidade de usar seletores mais expressivos para corresponder aos pods.

Embora os Replication Controllers ainda possam ser usados em versões mais antigas do Kubernetes, geralmente é recomendado usar ReplicaSets ou Deployments em vez disso, pois eles fornecem recursos de gerenciamento mais avançados e flexíveis.

>## Job é um objeto que cria um ou mais pods para executar uma determinada tarefa e garante que o número desejado de pods seja executado com sucesso.
A principal diferença entre um Job e um Deployment é que um Job é usado para trabalhos pontuais e de curta duração, enquanto um Deployment é usado para aplicativos de longa duração e em execução contínua.
O Kubernetes garante que cada pod criado pelo Job execute a tarefa especificada até a conclusão e, em seguida, encerre o pod. Se algum pod falhar, o Job cria um novo pod para substituí-lo e garantir que o número desejado de pods esteja sempre em execução.
Os Jobs são úteis para trabalhos que exigem uma execução única, como migração de banco de dados, criação de backups ou processamento em lote. Eles também podem ser usados para executar trabalhos que precisam ser executados periodicamente, definindo cronjobs que criam Jobs em intervalos regulares.

>## CronJob é um objeto que cria Jobs em intervalos regulares com base em uma expressão cron. 
Isso permite que você execute tarefas programadas periodicamente em um cluster Kubernetes.
A expressão cron especifica o cronograma no qual o CronJob criará Jobs. É composta por cinco campos separados por espaços: minutos, horas, dias do mês, meses e dias da semana. Cada campo pode ser preenchido com um número ou com um caractere curinga (*), que significa "todos os valores".
Quando um CronJob é criado, ele cria automaticamente um Job de acordo com a expressão cron especificada. O Job é executado em um pod e executa a tarefa programada. Após a conclusão do Job, o pod é encerrado. Se o Job falhar, o Kubernetes tentará recriá-lo novamente em um pod novo.
Os CronJobs são úteis para tarefas que precisam ser executadas em intervalos regulares, como backups de banco de dados, atualizações de software, processamento de dados em lote ou envio de e-mails agendados. Eles permitem que você automatize tarefas recorrentes e economize tempo e esforço.

>## ConfigMap é um objeto que armazena dados de configuração em formato de chave-valor. 
Ele permite que você separe a configuração do seu aplicativo da imagem do contêiner, facilitando a configuração do aplicativo em diferentes ambientes.
Os dados em um ConfigMap podem ser definidos manualmente ou carregados de um arquivo ou diretório externo. O Kubernetes injeta os dados do ConfigMap em um contêiner como variáveis de ambiente ou volumes montados, dependendo da sua configuração.
As variáveis de ambiente são úteis para armazenar dados de configuração pequenos e simples, como endereços de banco de dados ou credenciais de API. Já os volumes montados são úteis para armazenar arquivos de configuração mais complexos, como arquivos de propriedades, XML ou JSON.
Os ConfigMaps são úteis para separar a configuração do seu aplicativo da imagem do contêiner, tornando mais fácil a implantação do seu aplicativo em diferentes ambientes. Eles permitem que você configure seu aplicativo de forma dinâmica sem precisar recriar a imagem do contêiner ou alterar o código-fonte.

>## Secret é um objeto que permite armazenar dados confidenciais, como senhas, tokens de acesso e chaves SSH.
Esses dados podem ser usados por pods em um cluster Kubernetes, sem que a necessidade de expor informações confidenciais diretamente no código ou nas configurações de deployment.
Os Secrets são armazenados no cluster Kubernetes e podem ser consumidos pelos pods de várias formas, como variáveis de ambiente, volumes montados em containers ou diretamente em arquivos.
Os Secrets são codificados em base64 quando são armazenados no cluster, para evitar que dados sensíveis sejam expostos em texto simples. Além disso, os Secrets são criptografados em repouso no armazenamento do Kubernetes, o que ajuda a proteger ainda mais as informações confidenciais armazenadas neles.
Os Secrets podem ser criados e gerenciados usando a interface de linha de comando do Kubernetes (kubectl) ou arquivos YAML que descrevem o objeto Secret e podem ser aplicados ao cluster usando o kubectl apply.

