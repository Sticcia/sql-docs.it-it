---
title: srv_pfieldex (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_pfieldex
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 76e8d3991b4154e929b6b05a96e1b3f816c61b3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="srvpfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API delle stored procedure estese)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce un puntatore ai dati che contengono il campo SRV_PROC richiesto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *field*  
 Specifica il campo *srvproc* da restituire.  
  
|Campo|Description|Tipo restituito|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|LCDI di messaggio della sessione corrente.|ULONG*|  
|SRV_INSTANCENAME|Nome dell'istanza (se si tratta di un'istanza denominata); in caso contrario, restituisce NULL.|WCHAR*|  
  
 *len*  
 Puntatore a una variabile **int** che contiene la lunghezza in byte del valore *field* restituito. Se *len* è NULL, la lunghezza non viene restituita. Quando viene restituito NULL, **len* è impostato su 0.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Un puntatore ai dati il cui tipo dipende da *field*. Viene restituito NULL se *len* è NULL o *srvproc* è NULL. Se *field* non è noto, viene restituito NULL. Quando viene restituito NULL, **len* è impostato su 0.  
  
> [!IMPORTANT]  
>  Il buffer restituito dal server deve essere di sola lettura. In caso contrario, lo stato del server può risultare danneggiato.  
  
## <a name="remarks"></a>Remarks  
 **Nota sulla sicurezza** È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  