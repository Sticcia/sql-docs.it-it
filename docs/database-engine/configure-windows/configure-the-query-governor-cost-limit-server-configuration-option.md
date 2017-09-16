---
title: Configurare l'opzione di configurazione del server query governor cost limit | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], time to execute
- query governor cost limit option [SQL Server]
- time [SQL Server], query run time
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c37c6564ace5110c3035003cecad2ab3b52461ac
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-query-governor-cost-limit-server-configuration-option"></a>Configurare l'opzione di configurazione del server query governor cost limit
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questo argomento si illustra come configurare l'opzione di configurazione del server **query governor cost limit** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'opzione Query Governor Cost Limit consente di specificare un limite di tempo massimo per l'esecuzione di una query. Il costo delle query equivale al tempo trascorso, in secondi, stimato per l'esecuzione di una query in una configurazione hardware specifica. Il valore predefinito per questa opzione è 0, cioè Query Governor viene impostato su OFF. In questo modo, tutte le query vengono eseguite senza limitazione di tempo. Se si specifica un valore diverso da zero e positivo, tramite Query Governor non sarà possibile l'esecuzione delle query il cui costo stimato supera quel valore.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per configurare l'opzione query governor cost limit utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la configurazione dell'opzione query governor cost limit](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Questa opzione è avanzata e la relativa modifica è riservata ad amministratori di database esperti o a tecnici dotati di certificazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Per modificare il valore di Query Governor Cost Limit a livello di singola connessione, usare l'istruzione [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md) .  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o per l'esecuzione dell'istruzione RECONFIGURE, a un utente deve essere concessa l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>Per configurare l'opzione query governor cost limit  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un server e scegliere **Proprietà**.  
  
2.  Fare clic sulla pagina **Connessioni** .  
  
3.  Selezionare o deselezionare la casella di controllo **Usa Query Governor per evitare query con esecuzione prolungata** .  
  
     Se si seleziona questa casella di controllo, nella casella sottostante immettere un valore positivo che verrà utilizzato da Query Governor per impedire l'esecuzione di qualsiasi query di durata superiore a quel valore.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-configure-the-query-governor-cost-limit-option"></a>Per configurare l'opzione query governor cost limit  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si illustra come utilizzare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) per impostare il valore dell'opzione `query governor cost limit` su `120` secondi.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione query governor cost limit  
 L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
## <a name="see-also"></a>Vedere anche  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
