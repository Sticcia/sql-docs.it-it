---
title: "Attività Pulizia contenuto cronologia (Piano di manutenzione) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fbf4cfd2254dbe3e5f482e603ca7535682102d80
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="history-cleanup-task-maintenance-plan"></a>Attività Pulizia contenuto cronologia (Piano di manutenzione)
  Utilizzare la finestra di dialogo **Attività Pulizia contenuto cronologia** per eliminare le informazioni cronologiche meno recenti dalle tabelle del database msdb. Questa attività supporta l'eliminazione della cronologia delle operazioni di backup e ripristino, della cronologia processo agente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e della cronologia del piano di manutenzione.  
  
 Questa istruzione usa le istruzioni **sp_purge_jobhistory** e **sp_delete_backuphistory** .  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Connessione**  
 Consente di selezionare la connessione server da utilizzare per l'esecuzione dell'attività.  
  
 **Nuovi**  
 Consente di creare una nuova connessione server da utilizzare per l'esecuzione dell'attività. La finestra di dialogo **Nuova connessione** viene descritta più avanti in questo argomento.  
  
 **Cronologia operazioni di backup e ripristino**  
 Se si mantengono i record relativi alla data di creazione di backup recenti, è possibile semplificare la creazione di un piano di recupero da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in caso si desideri ripristinare un database. Il periodo di memorizzazione deve essere almeno pari alla frequenza dei backup completi del database.  
  
 **Cronologia processo di SQL Server Agent**  
 Questa cronologia si rivela utile per risolvere problemi relativi a processi non riusciti o per individuare le cause di determinate azioni sul database.  
  
 **Cronologia piano di manutenzione**  
 Questa cronologia si rivela utile per risolvere problemi relativi a processi del piano di manutenzione non riusciti o per individuare le cause di determinate azioni sul database.  
  
 **Rimuovi dati presenti nella cronologia da più di**  
 Specifica il periodo di permanenza nella cronologia oltre il quale gli elementi devono essere eliminati.  
  
 **Visualizza codice T-SQL**  
 Consente di visualizzare le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite sul server per questa attività, in base alle opzioni selezionate.  
  
> [!NOTE]  
>  Se il numero di oggetti interessato dall'attività è elevato, la visualizzazione del codice potrebbe richiedere una considerevole quantità di tempo.  
  
## <a name="new-connection-dialog-box"></a>Finestra di dialogo Nuova connessione  
 **Nome connessione**  
 Consente di immettere un nome per la nuova connessione.  
  
 **Selezionare o immettere il nome di un server**  
 Consente di selezionare il server a cui connettersi per l'esecuzione dell'attività.  
  
 **Aggiorna**  
 Consente di aggiornare l'elenco dei server disponibili.  
  
 **Immettere le informazioni per l'accesso al server**  
 Consente di specificare le opzioni di autenticazione per l'accesso al server.  
  
 **Usa la sicurezza integrata di Windows NT**  
 Consente di connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] di SQL Server utilizzando l'autenticazione di Microsoft Windows.  
  
 **Usa nome utente e password specifici**  
 Consente di connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] di SQL Server utilizzando l'autenticazione di SQL Server. Questa opzione non è disponibile.  
  
 **Nome utente**  
 Consente di specificare un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da utilizzare per l'autenticazione. Questa opzione non è disponibile.  
  
 **Password**  
 Consente di specificare una password da utilizzare per l'autenticazione. Questa opzione non è disponibile.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)  
  
  