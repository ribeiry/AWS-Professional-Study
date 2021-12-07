	AWS Storage Gateway:
		- Serviço de armazenamento hibrido na Cloud, apropriado para estender a sua rede on-premisse, que possibilita acesso vitural ao armazenamento ilimitado da cloud. Vc pode pensar nele como um mount em um S3
		- Tipos : 
			- Tape Gateway - um gateway de fita fornece armazenamento em fita virtual com suporte da nuvem
			- File Gateway - Você pode pensar no gateway de arquivos como uma montagem de sistema de arquivo no S3 e é compatível com o SMB e NFS.
			- Gateway Volume - Volumes de armazenamento de backup em nuvem que você pode montar como dispositivos :
				- Cached volumes : Armazena em um S3 e mantem como cópia dos dados acessados com frequencia mantendo a baixa latencia não é compatível com o SMB e NFS
				- Stored volumes : você pode armazenar localmente todo o conjunto de dados de volume e armazenar backups periódicos e pontuais (snapshots) na AWS
			
			
			https://docs.aws.amazon.com/pt_br/storagegateway/latest/userguide/WhatIsStorageGateway.html
## Storage
   ### AWS Storage Gateway:
		- Serviço de armazenamento hibrido na Cloud, apropriado para estender a sua rede on-premisse, que possibilita acesso vitural ao armazenamento ilimitado da cloud. Vc pode pensar nele como um mount em um S3
		- Tipos : 
			- Tape Gateway - um gateway de fita fornece armazenamento em fita virtual com suporte da nuvem
			- File Gateway - Você pode pensar no gateway de arquivos como uma montagem de sistema de arquivo no S3 e é compatível com o SMB e NFS.
			- Gateway Volume - Volumes de armazenamento de backup em nuvem que você pode montar como dispositivos :
				- Cached volumes : Armazena em um S3 e mantem como cópia dos dados acessados com frequencia mantendo a baixa latencia não é compatível com o SMB e NFS
				- Stored volumes : você pode armazenar localmente todo o conjunto de dados de volume e armazenar backups periódicos e pontuais (snapshots) na AWS
			
			https://docs.aws.amazon.com/pt_br/storagegateway/latest/userguide/WhatIsStorageGateway.html