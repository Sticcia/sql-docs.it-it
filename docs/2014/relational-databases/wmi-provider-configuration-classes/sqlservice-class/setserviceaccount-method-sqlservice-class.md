---
title: Metodo SetServiceAccount (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 65f9c926a75ae4d64e54d6f600aba2a70f0482cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63218101"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Metodo SetServiceAccount (classe SqlService)
  Tenta di modificare il nome utente e la password con cui è in esecuzione l'istanza del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
#### <a name="parameters"></a>Parametri  
 *ServiceStartName*  
 Valore string che specifica il nome dell'account con cui è in esecuzione il servizio. A seconda del tipo di servizio, il nome dell'account potrebbe essere nel formato NomeDominio\NomeUtente. Durante l'esecuzione il processo del servizio viene registrato utilizzando uno di due formati:  
  
-   Se l'account appartiene al dominio predefinito, è possibile specificare \Nomeutente.  
  
-   Se viene specificato NULL, il servizio verrà eseguito l'accesso come il **LocalSystem** account.  
  
 Per i driver a livello di sistema, o kernel *StartName* contiene il nome dell'oggetto driver, \FileSystem\Rdr o \Driver\Xns, che usa il sistema dei / o per caricare il driver di dispositivo. Se viene specificato NULL, il driver viene eseguito con un nome dell'oggetto predefinito creato dal sistema I/O in base sul nome del servizio, ad esempio DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Valore stringa che specifica la password per il nome dell'account nel *StartName* parametro. Specificare NULL se non si modifica la password. Specificare una stringa vuota se il servizio non dispone di password.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `uint32` che è 0 se il servizio è stato modificato correttamente 0 1 se la richiesta non è supportata. Qualsiasi altro numero indica un errore.  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
