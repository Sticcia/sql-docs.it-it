---
title: Sicurezza del trasporto per il mirroring del Database e gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- sessions [SQL Server], database mirroring
- cryptography [SQL Server], database mirroring
- certificates [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- transport security
- database mirroring [SQL Server], security
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 18b52163cb1e8c6be0cf7fdea37861662d6e4830
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62754291"
---
# <a name="transport-security-for-database-mirroring-and-alwayson-availability-groups-sql-server"></a>Sicurezza trasporto per il mirroring del database e i gruppi di disponibilità AlwaysOn (SQL Server)
  La sicurezza del trasporto implica l'utilizzo dell'autenticazione e, facoltativamente, della crittografia dei messaggi scambiati tra i database. Per il mirroring del database e [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], l'autenticazione e la crittografia devono essere configurate nell'endpoint del mirroring del database. Per un'introduzione agli endpoint del mirroring del database, vedere [Endpoint del mirroring del database &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md).  
  

  
##  <a name="Authentication"></a> Autenticazione  
 L'autenticazione è il processo di verifica che un utente sia effettivamente colui che dichiara di essere. Per le connessioni tra endpoint del mirroring del database è necessaria l'autenticazione. Le richieste di connessione da parte del partner o del server di controllo del mirroring devono essere autenticate.  
  
 Il tipo di autenticazione utilizzata da un'istanza del server per il mirroring del database o [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] è una proprietà dell'endpoint del mirroring del database. Per gli endpoint del mirroring del database sono disponibili due tipi di sicurezza del trasporto: l'autenticazione di Windows (Security Support Provider Interface, SSPI) e l'autenticazione basata su certificati.  
  
### <a name="windows-authentication"></a>Autenticazione di Windows  
 Con l'autenticazione di Windows, ogni istanza del server accede all'altra parte utilizzando le credenziali di Windows dell'account utente di Windows in cui è in esecuzione il processo. L'autenticazione di Windows potrebbe richiedere una configurazione manuale degli account di accesso, ad esempio:  
  
-   Se le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione come servizi con lo sotto lo stesso account di dominio, non è richiesta alcuna configurazione aggiuntiva.  
  
-   Se le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono in esecuzione come servizi con diversi account di dominio (in domini uguali o attendibili), è necessario creare l'account di accesso di ogni account in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint.  
  
-   Se le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono in esecuzione come account del servizio di rete, l'account di accesso di ogni account del computer host (*DomainName***\\***ComputerName$*) deve essere creato in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint. Ciò avviene in quanto un'istanza del server che è in esecuzione con l'account del servizio di rete esegue l'autenticazione utilizzando l'account di dominio del computer host.  
  
> [!NOTE]  
>  Per un esempio di configurazione di una sessione di mirroring del database tramite l'autenticazione di Windows, vedere [Esempio: Impostazione del mirroring del database tramite l'autenticazione di Windows &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md).  
  
### <a name="certificates"></a>Certificati  
 In alcuni casi, ad esempio quando le istanze del server non si trovano in domini di tipo trusted oppure quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione come servizio locale, l'autenticazione di Windows non è disponibile. In tali casi al posto delle credenziali utente per l'autenticazione delle richieste di connessione sono necessari certificati. L'endpoint del mirroring di ogni istanza del server deve essere configurato con il proprio certificato creato localmente.  
  
 Il metodo di crittografia viene stabilito al momento della creazione del certificato. Per altre informazioni, vedere [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md). Prestare attenzione nella gestione dei certificati utilizzati.  
  
 In un'istanza del server viene utilizzata la chiave privata del proprio certificato per stabilire la propria identità durante la configurazione di una connessione. Nell'istanza del server che riceve la richiesta di connessione viene utilizzata la chiave pubblica del certificato del mittente per autenticare l'identità del mittente. Considerare, ad esempio, due istanze del server, Server_A e Server_B. In Server_A viene utilizzata la propria chiave privata per crittografare l'intestazione di connessione prima di inviare una richiesta di connessione a Server_B. Server_B utilizza la chiave pubblica del certificato di Server_A per decrittografare l'intestazione di connessione. Se l'intestazione decrittografata è corretta, Server_B sa che l'intestazione è stata crittografata da Server_A e la connessione viene autenticata. Se l'intestazione decrittografata non è corretta, Server_B sa che la richiesta di connessione non è autentica e rifiuta la connessione.  
  
##  <a name="DataEncryption"></a> Crittografia dei dati  
 Per impostazione predefinita, un endpoint del mirroring del database richiede la codifica dei dati inviati in connessioni per il mirroring. In questo caso, l'endpoint può connettersi solo a endpoint che utilizzano la crittografia. A meno che non si sia assolutamente certi della sicurezza della rete, per le connessioni per il mirroring del database è consigliabile richiedere la crittografia. È tuttavia possibile disabilitare la crittografia oppure fare in modo che sia supportata ma non necessaria. Se la crittografia viene disabilitata, i dati non vengono mai crittografati e l'endpoint non può connettersi ad altri endpoint che la richiedono. Se la crittografia è supportata, i dati vengono crittografati solo se l'endpoint opposto supporta o richiede la crittografia.  
  
> [!NOTE]  
>  Gli endpoint del mirroring creati da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vengono creati con la crittografia impostata come richiesta o disabilitata. Per impostare il valore SUPPORTED per la crittografia, utilizzare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ENDPOINT. Per altre informazioni, vedere [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
 Facoltativamente, è possibile controllare gli algoritmi di crittografia che possono essere utilizzati da un endpoint specificando uno dei valori seguenti per l'opzione ALGORITHM in un'istruzione CREATE ENDPOINT o ALTER ENDPOINT:  
  
|Valore di ALGORITHM|Descrizione|  
|---------------------|-----------------|  
|RC4|Specifica che l'endpoint deve utilizzare l'algoritmo RC4. Impostazione predefinita.<br /><br /> Nota: L'algoritmo RC4 è deprecato. [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] È consigliabile utilizzare AES.|  
|AES|Specifica che l'endpoint deve utilizzare l'algoritmo AES.|  
|AES RC4|Specifica che due endpoint eseguiranno la negoziazione di un algoritmo di crittografia con l'endpoint corrente, dando la priorità all'algoritmo AES.|  
|RC4 AES|Specifica che due endpoint eseguiranno la negoziazione di un algoritmo di crittografia con l'endpoint corrente, dando la priorità all'algoritmo RC4.|  
  
 Se gli endpoint che stabiliscono la connessione specificano entrambi gli algoritmi ma in ordine diverso, avrà la priorità l'endpoint che accetta la connessione.  
  
> [!NOTE]  
>  L'algoritmo RC4 è supportato solo per motivi di compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive il materiale crittografato usando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.  
>   
>  Sebbene notevolmente più veloce rispetto all'algoritmo AES, RC4 è relativamente vulnerabile, mentre AES è relativamente avanzato. È quindi consigliabile utilizzare l'algoritmo AES.  
  
 Per informazioni sulla sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] per la specifica della crittografia, vedere [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per configurare la sicurezza del trasporto per un endpoint del mirroring del database**  
  
-   [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Impostazione dell'endpoint del mirroring del database per l'utilizzo di certificati per le connessioni in uscita &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql)   
 [Centro di sicurezza per il motore di database di SQL Server e il database SQL di Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [Gestire i metadati quando si rende disponibile un database in un'altra istanza del server &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [Endpoint del mirroring del database &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)   
 [sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)   
 [Risolvere i problemi relativi alla configurazione del mirroring del database &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [Risolvere i problemi di configurazione dei gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;eliminati](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)
  
  
