---
title: Avviare o arrestare un set di raccolta | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96f5a873e8d172254e1ea18abbd0c570b27a35ed
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918446"
---
# <a name="start-or-stop-a-collection-set"></a>Avviare o arrestare un set di raccolta
  In questo argomento viene descritto come avviare o arrestare un set di raccolte in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per avviare o arrestare un set di raccolta utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Le stored procedure dell'agente di raccolta dati e le viste del catalogo vengono archiviate nel database **msdb** .  
  
-   A differenza delle normali stored procedure, i parametri per le stored procedure dell'agente di raccolta dati utilizzano parametri fortemente tipizzati e non supportano la conversione automatica del tipo di dati. Se tali parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituisce un errore.  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario che il servizio SQL Server Agent sia avviato.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Per ottenere informazioni sui set di raccolta, eseguire una query sulla vista del catalogo [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) .  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'appartenenza al ruolo predefinito del database **dc_operator** . Se al set di raccolta non è associato un account proxy, è richiesta l'appartenenza al ruolo predefinito del server **sysadmin** . Esempi  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-start-a-collection-set"></a>Per avviare un set di raccolta  
  
1.  In Esplora oggetti espandere il nodo **Gestione** , **Raccolta dati**, quindi **Set di raccolta dati di sistema**.  
  
2.  Fare clic con il pulsante destro del mouse sul set di raccolta che si vuole avviare, quindi scegliere **Avviare il set di raccolta dati**.  
  
     In una finestra di messaggio verranno visualizzati i risultati di questa azione, mentre una freccia verde sull'icona del set di raccolta indica che il set di raccolta è stato avviato.  
  
#### <a name="to-stop-a-collection-set"></a>Per arrestare un set di raccolta  
  
1.  In Esplora oggetti espandere il nodo **Gestione** , **Raccolta dati**, quindi **Set di raccolta dati di sistema**.  
  
2.  Fare clic con il pulsante destro del mouse sul set di raccolta che si vuole arrestare, quindi scegliere **Arrestare il set di raccolta dati**.  
  
     In una finestra di messaggio verranno visualizzati i risultati di questa azione, mentre un cerchio rosso sull'icona del set di raccolta indica che il set di raccolta è stato arrestato.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-start-a-collection-set"></a>Per avviare un set di raccolta  
  
1.  Connettersi al [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si usa [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) per avviare il set di raccolta con l'ID `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a>Per arrestare un set di raccolta  
  
1.  Connettersi al [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si usa [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) per arrestare il set di raccolta con l'ID `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste dell'agente di raccolta dati &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql)   
 [Raccolta dati](data-collection.md)  
  
  
