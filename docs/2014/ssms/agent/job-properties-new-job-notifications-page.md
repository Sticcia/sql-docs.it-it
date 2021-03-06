---
title: 'Proprietà processo: Nuovo processo (pagina notifiche) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10cee6f0d5bf62178c71d25b8eb5682c22bbbe3b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2018
ms.locfileid: "52797689"
---
# <a name="job-properties-new-job-notifications-page"></a>Proprietà processo: Nuovo processo (pagina notifiche)
  Usare questa pagina per impostare le azioni che devono essere eseguite da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent al completamento del processo.  
  
## <a name="options"></a>Opzioni  
 **Posta elettronica**  
 Selezionare questa opzione per inviare un messaggio di posta elettronica al completamento del processo. Dopo aver selezionato questa opzione, scegliere l'operatore da notificare e la condizione che attiverà tale notifica: **Quando il processo ha esito positivo**; **Quando il processo ha esito negativo**; oppure **al termine del processo**.  
  
 **Page**  
 Selezionare questa opzione per inviare un messaggio di posta elettronica al cercapersone di un operatore al completamento del processo. Dopo aver selezionato questa opzione, specificare l'operatore da notificare e la condizione che attiverà tale notifica: **Quando il processo ha esito positivo**; **Quando il processo ha esito negativo**; oppure **al termine del processo**.  
  
 **Net Send**  
 Selezionare questa opzione se al completamento del processo si desidera inviare la notifica all'operatore tramite Net Send. Dopo aver selezionato questa opzione, specificare l'operatore da notificare e la condizione che attiverà tale notifica: **Quando il processo ha esito positivo**; **Quando il processo ha esito negativo**; oppure **al termine del processo**.  
  
 **Scrivi nel registro eventi applicazioni di Windows**  
 Selezionare questa opzione per scrivere una voce nel registro degli eventi dell'applicazione al completamento del processo. Dopo aver selezionato questa opzione, specificare la condizione che causerà la scrittura della voce: **Quando il processo ha esito positivo**; **Quando il processo ha esito negativo**; oppure **al termine del processo**.  
  
 **Elimina il processo automaticamente**  
 Selezionare questa opzione per eliminare il processo dopo il completamento. Dopo aver selezionato questa opzione, specificare la condizione che attiverà l'eliminazione del processo: **Quando il processo ha esito positivo**; **Quando il processo ha esito negativo**; oppure **al termine del processo**.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di processi](implement-jobs.md)   
 [Configurare Posta elettronica di SQL Server Agent per l'uso di Posta elettronica database](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
