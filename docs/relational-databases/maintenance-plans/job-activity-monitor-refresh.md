---
title: Aggiornamento di Monitoraggio attività processi | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e7156808f0b13d095f32adaf7cf12f96795cfb47
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217109"
---
# <a name="job-activity-monitor-refresh"></a>Aggiornamento di Monitoraggio attività processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare la finestra di dialogo **Impostazioni aggiornamento** per configurare la frequenza di acquisizione di nuove informazioni sull'attività del server da parte di Monitoraggio attività processi. Monitoraggio attività processi deve eseguire query sul server monitorato per ottenere informazioni per la griglia Monitoraggio attività processi. Quando l'intervallo di aggiornamento automatico è impostato su un valore inferiore a 30 secondi, il tempo impiegato per eseguire queste query può ridurre le prestazioni del server.  
  
 Per aprire questa finestra di dialogo fare clic su **Visualizza impostazioni di aggiornamento**nella sezione **Stato** di Monitoraggio attività processi.  
  
## <a name="options"></a>Opzioni  
 **Aggiorna automaticamente ogni**  
 Selezionare questa opzione per iniziare l'aggiornamento automatico delle informazioni di Monitoraggio attività. Questa opzione è deselezionata per impostazione predefinita.  
  
 **secondi**  
 Il numero di secondi che intercorrono tra i tentativi di aggiornamento automatici. Il valore predefinito è 60 secondi. Quando questa opzione è impostata su un valore uguale o inferiore a 5 l'aggiornamento viene eseguito comunque ogni 5 secondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio delle attività del processo](../../ssms/agent/monitor-job-activity.md)  
  
  
