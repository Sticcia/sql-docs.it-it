---
title: Metodo updateNClob (java.lang.String, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ad5c8d9b-f8c8-4ddf-85c8-23420bba54ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f82cbfee67acdb914263bd2fe70e0388f86a7f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695089"
---
# <a name="updatenclob-method-javalangstring-javaioreader-long"></a>Metodo updateNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata usando l'oggetto **Reader** specificato, che contiene il numero specificato di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.io.Reader reader,  
                        long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Valore **String** che indica l'etichetta della colonna.  
  
 *reader*  
  
 Oggetto lettore.  
  
 *length*  
  
 Numero di caratteri nei dati dei parametri.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateNClob viene specificato dal metodo updateNClob nell'interfaccia ResultSet.  
  
 Questo metodo è supportato solo sul **nvarchar (max)**, **ntext**, e **xml** colonne. L'utilizzo di questo metodo su qualsiasi altro tipo di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
