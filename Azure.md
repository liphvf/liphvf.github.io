O Azure divide o mundo em geografias definidas por limites geopolíticos ou fronteiras de paíse.

Geografias são divididas nas seguintes áreas:

- Américas
- Europa
- Pacífico Asiático
- Oriente Médio e África

Cada região pertence a uma única geografia e tem regras específicas de disponibilidade de serviço, conformidade e residência/soberania de dados aplicadas a ela. Confira a documentação para saber mais (um link está disponível na unidade de resumo).

Zona de Disponibilidade?
Zonas de Disponibilidade são datacenters separados fisicamente dentro de uma região do Azure.

Cada Zona de Disponibilidade é composta por um ou mais datacenters equipados com energia, resfriamento e rede independentes. Ela é configurada para ser um limite de isolamento. Se uma zona ficar inativa, as outras continuarão funcionando. Zonas de Disponibilidade são conectadas por meio de redes de fibra óptica privadas de alta velocidade.

![https://docs.microsoft.com/pt-br/learn/modules/explore-azure-infrastructure/media/4-availability-zones.png](https://docs.microsoft.com/pt-br/learn/modules/explore-azure-infrastructure/media/4-availability-zones.png)


As Zonas de Disponibilidade são, principalmente, para VMs, discos gerenciados, balanceadores de carga e bancos de dados SQL. Os serviços do Azure que dão suporte a Zonas de Disponibilidade enquadram-se em duas categorias:

- Serviços zonais – você fixa o recurso em uma zona específica (por exemplo, máquinas virtuais, discos gerenciados, endereços IP)
- Serviços com redundância de zona – a plataforma replica automaticamente entre zonas (por exemplo, armazenamento com redundância de zona, Banco de Dados SQL).



# Par de Regiões
- Uma vez que o par de regiões está diretamente conectado e suficientemente afastado para ser isolado contra desastres regionais, você pode usá-lo para fornecer redundância de dados e serviços confiáveis. Alguns serviços oferecem armazenamento com redundância geográfica automática usando pares de regiões.

Vantagens adicionais dos pares de regiões incluem:

No caso de uma interrupção ampla do Azure, uma região de cada par é priorizada para ajudar a reduzir o tempo necessário para restaurá-las para os aplicativos.
As atualizações planejadas do Azure são distribuídas para regiões emparelhadas uma por vez, de modo a minimizar o tempo de inatividade e o risco de interrupção dos aplicativos.
Os dados continuam residindo na mesma geografia que seu par (com exceção do Sul do Brasil) para fins de jurisdição do imposto e aplicação da lei.


Resiliência
Resiliência é a capacidade de um sistema de se recuperar de falhas e continuar funcionando. Não se trata de evitar falhas, mas de responder a elas de uma maneira que evite o tempo de inatividade ou a perda de dados. A meta da resiliência é retornar o aplicativo a um estado totalmente funcional após uma falha. A alta disponibilidade e a recuperação de desastre são dois componentes fundamentais da resiliência.

Ao projetar sua arquitetura, você precisa ter em mente a resiliência e deve executar uma FMA (Análise de modo de falha). O objetivo de uma FMA é identificar possíveis pontos de falha e definir como o aplicativo responde a essas falhas.

Disponibilidade é o tempo durante o qual um sistema está funcional e em operação


# Azure 

Tipos de assinaturas
O Azure oferece opções de assinatura gratuita e paga que são adequadas a necessidades e requisitos diferentes. As assinaturas mais usadas são:

Gratuita
Pagamento Conforme o Uso
Contrato Enterprise
Aluno

![https://docs.microsoft.com/pt-br/learn/modules/create-an-azure-account/media/3-accounts-and-subscriptions.png](https://docs.microsoft.com/pt-br/learn/modules/create-an-azure-account/media/3-accounts-and-subscriptions.png)


O Microsoft Azure AD não é igual ao Windows Active Directory. O Windows Active Directory destina-se a proteger servidores e desktops do Windows. Por outro lado, o Microsoft Azure AD está relacionado a padrões de autenticação baseados na Web, como OpenID e OAuth.


# Dimensionamento de VMs no Azure
Você pode executar VMs individuais para testes, desenvolvimento ou tarefas menores, ou agrupar várias VMs para fornecer alta disponibilidade, escalabilidade e redundância. O Azure tem vários recursos para que, independentemente dos seus requisitos de tempo de atividade, o Azure possa atendê-los. Esses recursos incluem:

Conjuntos de disponibilidade
Conjuntos de Dimensionamento de Máquinas Virtuais
Lote do Azure
O que são conjuntos de disponibilidade?
Um conjunto de disponibilidade é um agrupamento lógico de duas ou mais VMs que ajudam a manter seu aplicativo disponível durante a manutenção planejada ou não planejada.

Um evento de manutenção planejada é quando a malha subjacente do Azure que hospeda VMs é atualizada pela Microsoft. Um evento de manutenção planejada é feito para corrigir as vulnerabilidades de segurança, melhorar o desempenho e adicionar ou atualizar recursos. Na maioria das vezes, essas atualizações são feitas sem qualquer impacto para as VMs convidadas. Mas, às vezes, as VMs exigem uma reinicialização para concluir uma atualização. Quando a VM faz parte de um conjunto de disponibilidade, as atualizações de malha do Azure são sequenciadas, portanto, nem todas as VMs associadas são reinicializadas ao mesmo tempo. As VMs são colocadas em diferentes domínios de atualização. Os domínios de atualização indicam grupos de VMs e hardware físico subjacente que podem ser reinicializados ao mesmo tempo. Domínios de atualização são uma parte lógica de cada data center e são implementados com software e lógica.

Eventos de manutenção não planejada envolvem uma falha de hardware no data center, como uma falha de disco ou interrupção de energia. As VMs que fazem parte de um conjunto de disponibilidade alternam automaticamente para um servidor físico funcional para que a VM continue em execução. O grupo de máquinas virtuais que compartilham um hardware comum está no mesmo domínio de falha. Um domínio de falha é basicamente um rack de servidores. Ele fornece a separação física de sua carga de trabalho em diferentes hardwares de energia, resfriamento e rede que dão suporte aos servidores físicos nos racks de servidores do data center. Caso o hardware que dá suporte a um rack de servidores fique indisponível, apenas esse rack de servidores será afetado pela interrupção.

Com um conjunto de disponibilidade, você obtém:

Até três domínios de falha que têm um rack de servidor com recursos dedicados de energia e de rede
Cinco domínios de atualização lógica que podem ser aumentados para um máximo de 20
Suas VMs são colocadas em sequência na falha e nos domínio de atualização. O diagrama a seguir mostra um exemplo no qual você tem seis VMs em um conjunto de disponibilidade distribuído entre os dois domínios de falha e cinco domínios de atualização.

![https://docs.microsoft.com/pt-br/learn/modules/intro-to-azure-compute/media/3-availability-sets.png](https://docs.microsoft.com/pt-br/learn/modules/intro-to-azure-compute/media/3-availability-sets.png)

Diagrama que mostra a atualização de conjuntos de disponibilidade e domínios de falha duplicados entre servidores

Não há custo para um conjunto de disponibilidade. Você paga apenas pelas VMs dentro do conjunto de disponibilidade. É altamente recomendável colocar cada carga de trabalho em um conjunto de disponibilidade para evitar um ponto único de falha em sua arquitetura de VM.

O que são os conjuntos de dimensionamento de máquinas virtuais?
Os Conjuntos de Dimensionamento de Máquinas Virtuais do Azure permitem criar e gerenciar um grupo de VMs idênticas e com balanceamento de carga. Imagine que você esteja executando um site que permite aos cientistas carregarem imagens de astronomia que precisam ser processadas. Se você duplicasse a VM, normalmente precisaria configurar um serviço adicional para rotear solicitações entre várias instâncias do site. Os Conjuntos de Dimensionamento de VM podem fazer esse trabalho para você.

Os conjuntos de dimensionamento permitem que você gerencie, configure e atualize centralmente um grande número de VMs em minutos para fornecer aplicativos de alta disponibilidade. O número de instâncias de VM pode aumentar ou diminuir automaticamente em resposta à demanda ou a um agendamento definido. Com Conjuntos de Dimensionamento de VM, você pode criar serviços em grande escala para áreas como computação, big data e cargas de trabalho de contêineres.

O que é o Lote do Azure?
O Lote do Azure proporciona agendamento de trabalho e gerenciamento de computação em larga escala, com a capacidade de dimensionar dezenas, centenas ou milhares de VMs.

Quando você estiver pronto para executar um trabalho, o lote:

Iniciará um pool de VMs de computação para você
Instalará aplicativos e dados de preparo
Executará trabalhos com todas as tarefas que você tiver
Identificará falhas
Colocará o trabalho em filas
Diminuirá o pool conforme o trabalho for concluído
Pode haver situações em que você precise de potência de computação bruta ou de potência de computação no nível de supercomputador. O Azure fornece esses recursos.


Resumir Redes
https://docs.microsoft.com/pt-br/learn/modules/intro-to-azure-networking/3-scale-load-balancer