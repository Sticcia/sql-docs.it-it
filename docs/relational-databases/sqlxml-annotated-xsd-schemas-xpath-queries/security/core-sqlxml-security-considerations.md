---
title: Considerazioni sulla sicurezza SQLXML di base | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- security [SQLXML], about security
ms.assetid: 330cd2ff-d5d5-4c8e-8f93-0869c977be94
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b801d18e2420f79e6f5ca53cc5d7e29677f1f70b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2019
ms.locfileid: "56042972"
---
# <a name="core-sqlxml-security-considerations"></a>Considerazioni principali sulla sicurezza di SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Di seguito sono riportate alcune linee guida relative alla sicurezza quando si utilizza SQLXML per l'accesso ai dati.  
  
-   Il provider SQLXMLOLEDB espone una **StreamFlags** proprietà che è possibile impostare i flag che indica la funzionalità di SQLXML da abilitare o disabilitare per ogni istanza specifica. È possibile utilizzare questa proprietà per personalizzare l'utilizzo di SQLXML e assicurarsi che siano abilitati solo i componenti desiderati. Per altre informazioni, vedere [Provider SQLXMLOLEDB &#40;SQLXML 4.0&#41;](https://msdn.microsoft.com/library/fc489682-690a-4bb0-b5ac-237d376dc110).  
  
-   Gli eventuali errori SQLXML restituiti possono includere informazioni sullo schema del database, come i nomi delle tabelle o delle colonne oppure informazioni sui tipi. Prestare attenzione nella gestione di questi errori in modo tale da rendere difficile l'individuazione delle informazioni sull'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] da parte di utenti laddove non sia previsto o necessario.  
  
-   Quando utilizzato per eseguire query o inviare aggiornamenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], SQLXML non prevede l'impostazione di limiti sulla quantità di dati che è possibile scambiare e l'esecuzione di controlli sulle dimensioni dei dati di un payload prima che ne venga tentata l'elaborazione. Quando si sviluppa l'applicazione utilizzando SQLXML, è necessario assicurarsi che sia presente una quantità di memoria sufficiente nel sistema per elaborare i dati. Quando ad esempio si eseguono query sui dati del server, è necessario verificare la presenza di spazio sufficiente nella memoria del client per riceverli. Analogamente, se si caricano dati nel server, è necessario verificare la disponibilità di memoria sufficiente nel server per elaborarli e di spazio di archiviazione su disco sufficiente nel server per archiviarli.  
  
-   SQLXML consente di generare le query [!INCLUDE[tsql](../../../includes/tsql-md.md)] e di aggiornare i comandi in modo dinamico, quindi di inviarli a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per l'esecuzione. Si tratta dell'unico sistema disponibile in SQLXML per eseguire query nel server e per aggiornare quest'ultimo. I risultati verranno ricevuti come flusso (di XML) o come set di righe.  
  
-   Alla ricezione dei risultati delle query, non vengono eseguite azioni in base al contenuto dei dati ricevuti. Non vengono eseguite ulteriori operazioni di elaborazione in base al tipo o al contenuto dei dati. I dati non vengono mai trattati come codice con il quale eseguire azioni.  
  
-   Quando si eseguono modelli XML, in SQLXML le query XPath e DBObject contenute nel modello inviato vengono tradotte in comandi [!INCLUDE[tsql](../../../includes/tsql-md.md)] che verranno eseguiti su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Tali comandi influiscono solo sui dati esistenti. I comandi generati da SQLXML non modificheranno mai la struttura del database. Gli utenti devono inviare comandi espliciti per modificare la struttura del database, Ad esempio includendoli in un **SQL: query** blocco di un modello.  
  
-   Quando si eseguono query DBObject e istruzioni XPath su file di mapping, SQLXML non prevede la modifica dei dati del database.  
  
-   SQLXML consente di apportare modifiche relative alla formattazione ai dati specificati in base alle differenze tra i modelli di dati XML e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il formato per la specifica dell'ora è ad esempio diverso. Poiché in SQLXML viene tentata la risoluzione di queste differenze, si potrebbero perdere alcune informazioni sulla precisione.  
  
-   SQLXML non prevede l'impostazione di alcun limite sulla quantità di tempo necessaria per l'elaborazione dei dati. L'elaborazione continuerà finché non sarà stata completata o non si verificherà un errore.  
  
-   SQLXML non prevede la scrittura nel file system. L'eventuale salvataggio dei dati recuperati dal database deve essere eseguito nel codice.  
  
-   SQLXML consente agli utenti di eseguire qualsiasi query SQL sul database. Questa funzionalità non deve essere mai esposta a un'origine non protetta o non controllata, che equivarrebbe a consentire l'accesso al database SQL a qualsiasi utente.  
  
-   Quando si eseguono updategram, in SQLXML vengono tradotti i **updg: Sync** blocchi in comandi DELETE, UPDATE e INSERT sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza. Tali comandi influiscono solo sui dati esistenti. I comandi generati da SQLXML non modificheranno mai il database. Gli utenti devono inviare comandi espliciti per modificare la struttura del database, Ad esempio includendoli in un **SQL: query** blocco di un modello.  
  
-   Quando si eseguono DiffGram, in SQLXML vengono tradotti in comandi DELETE, UPDATE e INSERT sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Tali comandi influiscono solo sui dati esistenti. I comandi generati da SQLXML non modificheranno mai il database. Gli utenti devono inviare comandi espliciti per modificare la struttura del database, Ad esempio includendoli in un **SQL: query** blocco di un modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza per SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/sqlxml-4-0-security-considerations.md)  
  
  
