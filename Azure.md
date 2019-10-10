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