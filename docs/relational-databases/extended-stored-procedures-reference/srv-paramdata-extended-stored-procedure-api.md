---
title: srv_paramdata (API Stored procedure estesa) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_paramdata
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d68a33d8d09114d6142ef10d45e1f92e349d92ea
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="srvparamdata-extended-stored-procedure-api"></a>srv_paramdata (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il valore di un parametro di chiamata a una stored procedure remota. Questa funzione è stata sostituita dalla funzione **srv_paraminfo**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la chiamata alla stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria delle stored procedure estese per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *n*  
 Indica il numero del parametro. Il primo parametro è 1.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Puntatore al valore di parametro. Se il parametro in posizione *n* è NULL o se non è presente alcun parametro in posizione *n* o non esiste alcuna stored procedure remota, restituisce NULL. Se il valore del parametro è una stringa, potrebbe non essere con terminazione Null. Usare **srv_paramlen** per determinare la lunghezza della stringa.  
  
 Questa funzione restituisce i valori seguenti, se il parametro è uno dei tipi di dati di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I dati puntatore indicano anche se il puntatore per il tipo di dati è valido (VP), NULL o non applicabile (N/A) e il contenuto dei dati a cui punta.  
  
|Nuovi tipi di dati|Lunghezza dei dati di input|  
|--------------------|-----------------------|  
|BITN|**NULL:** VP, NULL<br /><br /> **ZERO:** VP, NULL<br /><br /> **>=255:** N/D<br /><br /> **<255:** N/D|  
|BIGVARCHAR|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, NULL<br /><br /> **>=255:** VP, 255 caratteri<br /><br /> **<255:** VP, dati effettivi|  
|BIGCHAR|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, 255 spazi<br /><br /> **>=255:** VP, 255 caratteri<br /><br /> **<255:** VP, dati effettivi + riempimento (fino a 255)|  
|BIGBINARY|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, 255 0x00<br /><br /> **>=255:** VP, 255 byte<br /><br /> **<255:** VP, dati effettivi + riempimento (fino a 255)|  
|BIGVARBINARY|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, 0x00<br /><br /> **>=255:** VP, 255 byte<br /><br /> **<255:** VP, dati effettivi|  
|NCHAR|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, 255 spazi<br /><br /> **>=255:** VP, 255 caratteri<br /><br /> **<255:** VP, dati effettivi + riempimento (fino a 255)|  
|NVARCHAR|**NULL:** NULL, N/D<br /><br /> **ZERO:** VP, NULL<br /><br /> **>=255:** VP, 255 caratteri<br /><br /> **<255:** VP, dati effettivi|  
|NTEXT|**NULL:** N/D<br /><br /> **ZERO:** N/D<br /><br /> **>=255:** N/D<br /><br /> **\<255:** N/D|  
  
 \*   i dati non sono con terminazione Null e non viene generato alcun avviso di troncamento per i dati >255 caratteri.  
  
## <a name="remarks"></a>Osservazioni  
 Se si conosce il nome del parametro, è possibile usare **srv_paramnumber** per ottenerne il numero. Per determinare se un parametro è NULL, usare **srv_paramlen**.  
  
 Quando una chiamata alla stored procedure remota viene effettuata con i parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se invece viene effettuata con alcuni parametri passati per nome e altri passati per posizione, si verifica un errore. Se si verifica un errore, il gestore SRV_RPC viene chiamato comunque ma risulta che non sono presenti parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_rpcparams &#40;API delle stored procedure estese&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  