---
title: Metodo allTablesAreSelectable (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d605d9c9725c5819af595115292e1cc3752ec0c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>Metodo allTablesAreSelectable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Specifica se l'utente corrente disponga delle autorizzazioni per utilizzare tutte le tabelle restituite dal [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) metodo in un'istruzione SELECT.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'utente dispone delle autorizzazioni per utilizzare tutte le tabelle. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo allTablesAreSelectable viene specificato dal metodo allTablesAreSelectable nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  