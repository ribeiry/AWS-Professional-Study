## ElasticCache
   ### Elasticache for Redis: 
  ElastiCache for Redis é um datastore na memória com performance excepcional que oferece latência inferior a um milissegundo a aplicativos em tempo real na escala da Internet.
   * Operações disponíveis :
        * Sorted Sets
	* In-Memory Data-Store
	* Pub/Subnet
	* Armazenamento de Sessão 
 Suporta replicação de dados, e portanto entrega uma alta disponibilidade
 Obs.: 
     * Elasticache é baseado em armazenamento apenas de chave-valor e não de Relacional.
     * O mecanismo Redis não oferece suporte a vários núcleos ou threads(multi-thread) de CPU.	
					
  * Quando utilizar : 
Building real-time apps across versatile use cases like gaming, geospatial service, caching, session stores, or queuing, with advanced data structures, replication, and point-in-time snapshot support.
	
### Elasticache for Memcached : 
Serviço de armazenamento chave e valor em memória, que pode ser usado como cache ou data store
* Armazenamento de Sessão
* Não suporta replicação de dados e entrega menor disponibilidade
* Quando utilizar :
	Building a simple, scalable caching layer for your data-intensive apps.
### Patterns de ElastiCache:
			- Lazy Loading: Todos os dado lidos são em cache, o dado podem ficar obsoletos
			- Write Through: Adicionar ou atualizar dados em cache quando escrever no DataBase
			- Session Store: Armazene Temporariamente os dados de sessão em cache usando a feature de TTL
### Comparação MemCached X Redis
           

## RDS

### Manutenção do RDS:
		
- Hardware
				Antes que a manutenção seja agendada, você recebe uma notificação por e-mail sobre as janelas de manutenção de hardware agendada que inclui o tempo da manutenção e as zonas de disponibilidade afetadas. Durante a manutenção de hardware, as implantações Single-AZ ficam indisponíveis por alguns minutos. As implantações Multi-AZ ficam indisponíveis pelo tempo que leva para o failover da instância (geralmente cerca de 60 segundos) se a zona de disponibilidade for afetada pela manutenção. Se apenas a Zona de disponibilidade secundária for afetada, não haverá failover ou tempo de inatividade.
			
		- Sistema Operacional 
				Depois que a manutenção do sistema operacional for agendada para a próxima janela de manutenção, a manutenção pode ser adiada ajustando sua janela de manutenção preferida. Para minimizar o tempo de inatividade, modifique a instância do banco de dados Amazon RDS para uma implantação Multi-AZ. Para implantações Multi-AZ, a manutenção do sistema operacional é aplicada primeiro à instância secundária, em seguida, ocorre failover da instância e, em seguida, a instância primária é atualizada. O tempo de inatividade ocorre durante o failover. Para obter mais informações, consulte Manutenção para implantações multi-AZ.

		- Engine de banco de dados
				As atualizações no nível do mecanismo de banco de dados requerem tempo de inatividade. Mesmo se sua instância de banco de dados RDS usar uma implantação Multi-AZ, as instâncias de banco de dados principal e de reserva são atualizadas ao mesmo tempo. Isso causa tempo de inatividade até que a atualização seja concluída, e a duração do tempo de inatividade varia de acordo com o tamanho de sua instância de banco de dados.
### Authentication
	O AWSAuthenticationPlugin  é um plugin fornecido pela AWS, do qual ele se conecta com o seu IAM para poder autenticar os seus usuarios do IAM em seu RDS. Ao criar o usuario na em seu RDS é necessário indentifica-lo a forma de autenticação, Como por exemplo:
			CREATE USER jane_doe IDENTIFIED WITH AWSAuthenticationPlugin AS 'RDS'. No qual a instrução IDENTIFIED WITH permite que o MySQL user o plugin para o usuario jane_doe.
### Multi-AZ
	Multi-AZ RDS creates a replica in another AZ and synchronously replicates to it (DR only). 
			- Multi-AZ deployments for the MySQL, MariaDB, Oracle and PostgreSQL engines utilize synchronous physical replication. 
			- Multi-AZ deployments for the SQL Server engine use synchronous logical replication (SQL Server-native Mirroring technology).
    Para sair de um modelo Single-AZ para Multi-AZ apenas click em modify, não ha necessidade de para a instancia, o que acontece é :
			1 - É tirado um snapshot
			2 - A nova DB é restaurada do snapshot na nova AZ
			3 - A sincronização é estabelecida entre as duas instancias
## Aurora
	Aurora é um banco de dados relacional construido pela AWS em cima da engine do MySql, que tem performace melhor do que o MySQL devido ao seu desing.
### Aurora Serverless
    O Amazon Aurora Serverless é uma configuração com escalabilidade automática sob demanda para Amazon Aurora. Ele inicia, encerra e expande a capacidade automaticamente de acordo com as necessidades do seu aplicativo. O Amazon Aurora Serverless permite que você execute um banco de dados na nuvem sem gerenciar qualquer capacidade de banco de dados.
### Global Database
	O Amazon Aurora Global Database fornece acesso apenas de leitura a um banco de dados em várias regiões - ele não fornece configuração ativo-ativo com sincronização bidirecional (embora você possa fazer failover para seus bancos de dados somente leitura e promovê-los para graváveis caso o cluster principal ou a região onde está localizado o cluster principal caia).
### Failover
	Em caso de indisponibilidade da instancia Master o cluster Aurora toma as seguintes ações: 
		1º - Promove uma réplica saudável para a instancia master de acordo com a prioridade setada para a réplica ou de acordo com o tamanho, réplica ou de maneira aleatória.	
		2º - Se nenhuma Read Réplica saudável está disponível uma nova Instancia Master é criada, levando o aumento de down time.
### Multi AZ
	É possível transformar um cluster existente do Aurora em um cluster Multi-AZ adicionando uma nova instância de leitor e especificando uma zona de disponibilidade diferente.
  - Tipos de EndPoint
    - Built-in Cluster
		Built-in Cluster é o endpoint de escrita que se conecta a instancia primária do cluster
			
    - Built-in Reader
		Built-in Reader é o endpoint de leitura que balanceia a carga de leitura entre as Read Réplicas do cluster aurora, caso não haja Read Replicas definidas esse endpoint passa a consumir os dados da Instancia primária. 
## DynamoDb