---
title: Metodo setTrustStore (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustStore Method (SQLServerDataSource)
apilocation:
- setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8deaaf006698018764eb67dc27e3f7cdb372e04a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687767"
---
# <a name="settruststore-method-sqlserverdatasource"></a>Metodo setTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il percorso (incluso il nome file) del file trustStore del certificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustStore*  
  
 Una **stringa** contenente il percorso, nome file incluso, del file trustStore del certificato.  
  
## <a name="remarks"></a>Remarks  
 Quando la proprietà trustStore non è specificata o è impostata su Null, per determinare l'archivio certificati da utilizzare in [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] vengono utilizzate le regole di ricerca della factory del responsabile dell'attendibilità. Tramite l'istanza predefinita di TrustManagerFactory SunX509 viene eseguito un tentativo di individuare il materiale attendibile nelle posizioni seguenti in base all'ordine indicato:  
  
-   1. Un file specificato dalla proprietà di sistema JVM (Java Virtual Machine) "javax.net.ssl.trustStore".  
  
-   2. "\<java-home >/lib/security/jssecacerts" file.  
  
-   3. "\<java-home >/lib/security/cacerts" file.  
  
 Per ulteriori informazioni, vedere la documentazione relativa all'interfaccia TrustManager SunX509 nel sito Web Sun Microsystems.  
  
 Se la proprietà trustStore è impostata su una stringa o una stringa vuota "", tale valore verrà utilizzato dal driver per trovare il file trustStore e convalidare il certificato SSL del server.  
  
 È possibile specificare la proprietà trustStorePassword insieme alla proprietà trustStore in modo da utilizzarne il valore per aprire il file trustStore. Per ulteriori informazioni, vedere [setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
