---
title: Ripristinare un database fino a una transazione contrassegnata (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 919c10372e397f0c2d66d7648363aef7916ec598
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875605"
---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a>Ripristino di un database fino a una transazione contrassegnata (SQL Server Management Studio)
  Quando un database è in stato di ripristino, è possibile usare la finestra di dialogo **Ripristina log delle transazioni** per ripristinare il database a una transazione contrassegnata nei backup del log disponibili.  
  
> [!NOTE]  
>  Per altre informazioni, vedere [Usare transazioni contrassegnate per recuperare coerentemente i database correlati &#40;modello di recupero con registrazione completa&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) e [Recupero di database correlati che contengono transazioni contrassegnate](recovery-of-related-databases-that-contain-marked-transaction.md).  
  
### <a name="to-restore-a-marked-transaction"></a>Per ripristinare una transazione contrassegnata  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espandere l'albero del server.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Ripristina**.  
  
4.  Fare clic su **Log delle transazioni**per visualizzare la finestra di dialogo **Ripristina log delle transazioni** .  
  
5.  Nella sezione **Ripristina fino a** della pagina **Generale** fare clic su **Transazione contrassegnata**per visualizzare la finestra di dialogo **Seleziona transazione contrassegnata** . In tale finestra è visualizzata una griglia in cui sono elencate le transazioni contrassegnate disponibili nei backup dei log delle transazioni selezionati.  
  
     Per impostazione predefinita, il ripristino viene eseguito fino alla transazione contrassegnata esclusa. Per ripristinare anche la transazione contrassegnata, selezionare l'opzione **Includi transazione contrassegnata**.  
  
     Nella tabella seguente vengono elencate le intestazioni delle colonne della griglia con una descrizione dei rispettivi valori.  
  
    |Intestazione|Value|  
    |------------|-----------|  
    |\<vuoto>|Consente di visualizzare una casella di controllo per selezionare il contrassegno.|  
    |**Contrassegno transazione**|Nome della transazione contrassegnata specificato dall'utente durante l'esecuzione del commit della transazione.|  
    |**Data**|Data e ora assegnate alla transazione quando ne è stato eseguito il commit. Vengono visualizzate la data e l'ora della transazione registrate nella tabella **msdbgmarkhistory** , non nella data e ora del computer client.|  
    |**Descrizione**|Eventuale descrizione della transazione contrassegnata specificata dall'utente quando è stato eseguito il commit della transazione.|  
    |**LSN**|Numero di sequenza del file di log (LSN) della transazione contrassegnata.|  
    |**Database**|Nome del database in cui è stato eseguito il commit della transazione contrassegnata.|  
    |**Nome utente**|Nome dell'utente del database che ha eseguito il commit della transazione contrassegnata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristinare un Backup del Database &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [Ripristinare un backup del log delle transazioni &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
  
