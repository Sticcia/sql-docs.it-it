---
title: MSSQLSERVER_3159 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f6f367b13a821f7e47a7ece7853564789f8509e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710239"
---
# <a name="mssqlserver3159"></a>MSSQLSERVER_3159
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|3159|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_LOGNOTBACKEDUP|  
|Testo del messaggio|La parte finale del log per il database "%ls" non è stata inclusa nel backup. Se il log contiene informazioni che non si desidera perdere, utilizzare BACKUP LOG WITH NORECOVERY per eseguire il backup del log. Se si desidera semplicemente sovrascrivere il contenuto del log, utilizzare la clausola WITH REPLACE o WITH STOPAT dell'istruzione RESTORE.|  
  
## <a name="explanation"></a>Spiegazione  
Nella maggioranza dei casi, nel modello di recupero con registrazione completa o nel modello di recupero con registrazione minima delle operazioni bulk [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede l'esecuzione di un backup della parte finale del log per acquisire i record del log di cui non è stato ancora eseguito il backup. Un backup del log eseguito sulla parte finale del log stesso appena prima di un'operazione di ripristino è detto backup della parte finale del log.  
  
Quando si recupera un database fino al punto di un errore, il backup della parte finale del log è l'ultimo backup di interesse nel piano di recupero. Se risulta impossibile eseguire il backup della parte finale del log, è possibile ripristinare un database solo fino alla fine dell'ultimo backup creato prima dell'errore.  
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in genere necessario eseguire il backup della parte finale del log prima di avviare il ripristino di un database. Il backup della parte finale del log impedisce la perdita di dati e mantiene intatta la catena di log. Non in tutti gli scenari di ripristino è tuttavia necessario un backup della parte finale del log. Non è necessario eseguire il backup della parte finale del log se il punto di recupero è incluso in un backup del log precedente o se si sta spostando o sostituendo (sovrascrivendo) il database e non è necessario ripristinarlo fino a un punto nel tempo dopo l'ultimo backup. Inoltre, se i file di log sono danneggiati e non è possibile creare un backup della parte finale del log, è necessario ripristinare il database senza utilizzare un backup della parte finale del log. Qualsiasi transazione di cui sia stato eseguito il commit dopo l'ultimo backup del log andrà persa. Per ulteriori informazioni, vedere "Ripristino senza utilizzare un backup della parte finale del log" di seguito in questo argomento.  
  
> [!CAUTION]  
> È consigliabile utilizzare REPLACE raramente e solo dopo un'attenta valutazione.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire un backup della parte finale del log e ripetere l'operazione di ripristino.  
  
Se non è possibile eseguire il backup della parte finale del log, utilizzare WITH STOPAT o WITH REPLACE nelle istruzioni RESTORE.  
  
## <a name="see-also"></a>Vedere anche  
[Ripristinare un database di SQL Server fino a un punto specifico &#40;modello di recupero con registrazione completa&#41;](~/relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
[Eseguire il backup del log delle transazioni quando il database è danneggiato &#40;SQL Server&#41;](~/relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
[Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](~/relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
[Backup della parte finale del log &#40;SQL Server&#41;](~/relational-databases/backup-restore/tail-log-backups-sql-server.md)  
  
