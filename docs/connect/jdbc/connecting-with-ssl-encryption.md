---
title: La connessione tramite la crittografia SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14f33ac9e6ab8d17954039f4ae0fca1f11e46af5
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737132"
---
# <a name="connecting-with-ssl-encryption"></a>Connessione tramite la crittografia SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Gli esempi di questo argomento descrivono come usare le proprietà della stringa di connessione che consentono alle applicazioni di usare la crittografia SSL (Secure Sockets Layer) in un'applicazione Java. Per altre informazioni sulle nuove proprietà della stringa di connessione, ad esempio **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** e **hostNameInCertificate**, vedere [Impostazione delle proprietà delle connessioni](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Se la proprietà **encrypt** è impostata su **true** e la proprietà **trustServerCertificate** è impostata su **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] non convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ciò è in genere necessario per consentire le connessioni in ambienti di test, ad esempio nel caso in cui l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abbia solo un certificato autofirmato.  
  
 L'esempio di codice seguente illustra come impostare la proprietà **trustServerCertificate** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Se la proprietà **encrypt** è impostata su **true** e la proprietà **trustServerCertificate** è impostata su **false**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. Per la convalida del certificato del server è necessario che in fase di connessione venga fornito il materiale relativo all'attendibilità usando in modo esplicito le proprietà di connessione **trustStore** e **trustStorePassword** oppure usando in modo implicito l'archivio di scopi predefinito di JVM (Java Virtual Machine) sottostante.  
  
 La proprietà **trustStore** specifica il percorso (incluso il nome file) del file trustStore, che contiene l'elenco di certificati considerati attendibili dal client. La proprietà **trustStorePassword** specifica la password usata per verificare l'integrità dei dati del file trustStore. Per altre informazioni sull'uso di archivio di attendibilità predefinito di JVM, vedere la [configurazione del Client per la crittografia SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 L'esempio di codice seguente illustra come impostare le proprietà **trustStore** e **trustStorePassword** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Il driver JDBC è dotato di una proprietà aggiuntiva, **hostNameInCertificate**, che specifica il nome host del server. Il valore di questa proprietà deve corrispondere alla proprietà relativa al soggetto del certificato.  
  
 L'esempio di codice seguente illustra come usare la proprietà **hostNameInCertificate** in una stringa di connessione:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  In alternativa, è possibile impostare il valore delle proprietà di connessione usando i metodi **setter** appropriati offerti dalla classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Se il **crittografare** è impostata su **true** e il **trustServerCertificate** è impostata su **false** e se il server nome nel stringa di connessione non corrisponde al nome di server nel certificato SSL, verrà generato l'errore seguente: `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`. A partire dalla versione 7.2, il driver supporta la corrispondenza dei caratteri jolly nell'etichetta più a sinistra del nome del server nel certificato SSL.
## <a name="see-also"></a>Vedere anche  
 [Uso della crittografia SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
