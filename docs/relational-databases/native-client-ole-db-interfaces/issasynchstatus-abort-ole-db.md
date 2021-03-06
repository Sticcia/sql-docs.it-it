---
title: 'Issasynchstatus:: Abort (OLE DB) | Documenti di Microsoft'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e105db14e9b22b34439050ae6e08d5094f397b17
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514583"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Annulla un'operazione di esecuzione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hChapter*[in]  
 Handle del capitolo per il quale interrompere l'operazione. Se l'oggetto chiamato non è un oggetto set di righe o l'operazione non è applicabile a un capitolo, il chiamante deve impostare *hChapter* su DB_NULL_HCHAPTER.  
  
 *eOperation*[in]  
 Operazione da interrompere. Deve corrispondere al valore seguente:  
  
 DBASYNCHOP_OPEN: la richiesta di annullamento si applica all'apertura o al popolamento asincrono di un set di righe o all'inizializzazione asincrona di un oggetto origine dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 La richiesta di annullare l'operazione asincrona è stata elaborata. Questo non garantisce che l'operazione stessa sia stata annullata. Per determinare se è stata effettivamente annullata, il consumer deve chiamare [ISSAsynchStatus::GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) e verificare DB_E_CANCELED. È tuttavia possibile che non venga restituito nella chiamata successiva.  
  
 DB_E_CANTCANCEL  
 Non è stato possibile annullare l'operazione asincrona.  
  
 DB_E_CANCELED  
 La richiesta di interrompere l'operazione asincrona è stata annullata durante le notifiche. L'operazione viene ancora eseguita in modo asincrono.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider.  
  
 E_INVALIDARG  
 Il *hChapter* parametro non è DB_NULL_HCHAPTER oppure *eOperation* non è DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **Issasynchstatus:: Abort** è stato chiamato su un oggetto origine dati in cui **IDBInitialize:: Initialize** non è stato chiamato, o non è stata completata.  
  
 **ISSAsynchStatus::Abort** è stato chiamato su un oggetto origine dati su cui **IDBInitialize::Initialize** è stato chiamato ma successivamente annullato prima dell'inizializzazione o ha raggiunto il timeout. L'oggetto origine dati è ancora non inizializzato.  
  
 **Issasynchstatus:: Abort** è stato chiamato su un set di righe in cui **ITransaction:: commit** oppure **ITransaction:: Abort** è stato chiamato in precedenza, e il set di righe non vengono conservati dopo il commit o interrompere ed è in uno stato non valido.  
  
 **ISSAsynchStatus::Abort** è stato chiamato su un set di righe annullato in modo asincrono nella fase di inizializzazione. Il set di righe si trova in uno stato non valido.  
  
## <a name="remarks"></a>Note  
 L'interruzione dell'inizializzazione di un set di righe o di un oggetto origine dati potrebbe lasciare il set di righe o l'oggetto origine dati in uno stato non valido e determinare la restituzione di E_UNEXPECTED da parte di tutti i metodi ad eccezione di **IUnknown**. Quando ciò accade, l'unica azione possibile per il consumer consiste nel rilasciare il set di righe o l'oggetto origine dati.  
  
 Se si chiama **ISSAsynchStatus::Abort** e si passa un valore per *eOperation* diverso da DBASYNCHOP_OPEN, viene restituito S_OK. Questo non implica che l'operazione sia stata completata o annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
