---
title: Metodo setPortNumber (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15e0ff764637869428945ab3eb4b6c44b055b436
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728199"
---
# <a name="setportnumber-method-sqlserverdatasource"></a>Metodo setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di porta da usare per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parametri  
 *portNumber*  
  
 Valore **int** contenente il numero di porta.  
  
## <a name="remarks"></a>Remarks  
 Il numero di porta è il numero di porta TCP/IP usato quando si apre una connessione socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se la proprietà portNumber non è impostata, il metodo [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) restituisce il valore predefinito 1433.  
  
> [!NOTE]  
>  Il metodo setPortNumber non esegue alcun controllo sul valore di porta passato di intervallo. È possibile passare un numero di porta che non è valido, come 99999, senza generare un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
