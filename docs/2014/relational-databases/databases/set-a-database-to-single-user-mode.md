---
title: Impostare un database in modalità utente singolo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ea6e37603ae997c218db196c14fe7831bef95e81
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871234"
---
# <a name="set-a-database-to-single-user-mode"></a>Impostare un database in modalità utente singolo
  In questo argomento si descrive come impostare un database definito dall'utente in modalità utente singolo in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Questa modalità consente l'accesso a un solo utente alla volta e viene in genere utilizzata per azioni di manutenzione.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
     [Sicurezza](#Security)  
  
-   **Per impostare un database in modalità utente singolo utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se altri utenti sono connessi al database nel momento in cui viene impostata la modalità utente singolo, le relative connessioni verranno chiuse senza preavviso.  
  
-   Il database rimane in modalità utente singolo anche se l'utente che ha impostato l'opzione si disconnette. A questo punto, un altro utente (ma solo uno) potrà connettersi al database.  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Prima di impostare il database in modalità SINGLE_USER, verificare che l'opzione AUTO_UPDATE_STATISTICS_ASYNC sia impostata su OFF. Se l'opzione è impostata su ON, tramite il thread in background utilizzato per aggiornare le statistiche viene stabilita una connessione con il database che non sarà quindi accessibile in modalità utente singolo. Per altre informazioni, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-a-database-to-single-user-mode"></a>Per impostare un database in modalità utente singolo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Fare clic con il pulsante destro del mouse sul database di cui modificare l'impostazione e quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà database** fare clic sulla pagina **Opzioni** .  
  
4.  Selezionare **Single** nell'opzione **Limitazione accesso**.  
  
5.  Se altri utenti sono connessi al database, verrà visualizzato il messaggio **Connessioni aperte** . Per modificare la proprietà e chiudere tutte le altre connessioni, fare clic su **Sì**.  
  
 Tramite questa procedura, è inoltre possibile impostare l'accesso Multiple o Restricted per il database. Per altre informazioni sulle opzioni di limitazione dell'accesso, vedere [Proprietà del database &#40;pagina Opzioni&#41;](database-properties-options-page.md).  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-set-a-database-to-single-user-mode"></a>Per impostare un database in modalità utente singolo  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si imposta il database in modalità `SINGLE_USER` in modo da ottenere l'accesso esclusivo. Nell'esempio lo stato del database [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] viene quindi impostato su `READ_ONLY` e viene ripristinato l'accesso al database per tutti gli utenti. L'opzione di chiusura `WITH ROLLBACK IMMEDIATE` è specificata nella prima istruzione `ALTER DATABASE` . Questa operazione comporterà il rollback di tutte le transazioni incomplete e l'immediata interruzione di qualsiasi altra connessione al database [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] .  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
