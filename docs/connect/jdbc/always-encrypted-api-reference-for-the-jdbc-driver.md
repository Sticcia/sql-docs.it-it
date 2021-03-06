---
title: Informazioni di riferimento sull'API Always Encrypted per il driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66f659f5fbb2daa0b0a9969c3e7cde75dccc53d0
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361671"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>Informazioni di riferimento sull'API Always Encrypted per il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Always Encrypted consente ai client di eseguire la crittografia dei dati sensibili all'interno delle applicazioni client e non rivelare le chiavi di crittografia di SQL Server. Un driver abilitato Always Encrypted installato nel computer client usa questa funzionalità eseguendo automaticamente la crittografia e la decrittografia dei dati sensibili nell'applicazione client di SQL Server. Il driver esegue la crittografia dei dati in colonne riservate prima di passare i dati a SQL Server e riscrive automaticamente le query in modo da mantenere la semantica per l'applicazione. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati archiviati in colonne crittografate del database presenti nei risultati della query. Per altre informazioni, vedere [Always Encrypted (motore di Database)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) e [utilizzo di Always Encrypted con il Driver JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Always Encrypted è supportato solo da Microsoft JDBC Driver 6.0 o versione successiva per SQL Server con SQL Server 2016.  
  
 ## <a name="always-encrypted-api-references"></a>Riferimento all'API di Always Encrypted
 
 Esistono diverse nuove funzionalità e modifiche all'API del driver JDBC da utilizzare in applicazioni client che utilizzano Always Encrypted.  
  
 **Classe SQLServerConnection**  
  
|nome|Descrizione|  
|----------|-----------------|  
|Nuova parola chiave della stringa di connessione:<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled abilita la funzionalità Always Encrypted per la connessione e columnEncryptionSetting=Disabled la disabilita. I valori accettati sono Enabled/Disabled. Il valore predefinito è Disabled.|  
|Nuovi metodi:<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|Consente di impostare, aggiornare o rimuovere un elenco di percorsi principali attendibili per un server di database. Se durante l'elaborazione di una query dell'applicazione, il driver riceve il percorso di una chiave che non è presente nell'elenco, la query ha esito negativo. Questa proprietà garantisce una maggiore protezione da attacchi alla sicurezza in cui un'istanza compromessa di SQL Server invia falsi percorsi delle chiavi, causando potenzialmente la perdita delle credenziali dell'archivio di chiavi.|  
|Nuovo metodo:<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|Restituisce un elenco di percorsi attendibili delle chiavi per un server di database.|  
|Nuovo metodo:<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|Consente di registrare provider personalizzati per gli archivi delle chiavi. È un dizionario che esegue il mapping dei nomi dei provider degli archivi delle chiavi per le implementazioni del provider dell'archivio delle chiavi.<br /><br /> Per usare l'archivio chiavi JVM è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionJVMKeyStoreProvider con le credenziali keystore di JVM e registrarla con il driver. Il nome per questo provider deve essere 'MSSQL_JVM_KEYSTORE'.<br /><br /> Per usare l'archivio di Azure Key Vault, è necessario creare un'istanza di un oggetto SQLServerColumnEncryptionAzureKeyStoreProvider e registrarlo con il driver. Il nome per questo provider deve essere 'AZURE_KEY_VAULT'.|
|`public final boolean getSendTimeAsDatetime()`|Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|

 **Classe SQLServerConnectionPoolProxy**
 
|nome|Descrizione|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | Restituisce l'impostazione della proprietà di connessione sendTimeAsDatetime.|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | Modifica l'impostazione della proprietà di connessione sendTimeAsDatetime.|
     
  
 **Classe SQLServerDataSource**  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|Abilita/disabilita la funzionalità Always Encrypted per l'oggetto di origine dati.<br /><br /> Il valore predefinito è Disabled.|  
|`public String getColumnEncryptionSetting()`|Recupera l'impostazione della funzionalità Always Encrypted per l'oggetto di origine dati.|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|Imposta il nome che identifica un archivio chiavi. Unico valore supportato è il **JavaKeyStorePassword** per identificare la Store chiave Java.<br/><br/>Il valore predefinito è Null.|
|`public String getKeyStoreAuthentication()`|Ottiene il valore dell'impostazione keyStoreAuthentication per l'oggetto origine dati.|
|`public void setKeyStoreSecret(String keyStoreSecret)`|Imposta la password dell'archivio chiavi Java. La password per l'archivio chiavi e la chiave deve essere lo stesso. Si noti che keyStoreAuthentication deve essere impostata con **JavaKeyStorePassword**.|
|`public void setKeyStoreLocation(String keyStoreLocation)`|Imposta il percorso, incluso il nome del file dell'archivio chiavi Java. Si noti che keyStoreAuthentication deve essere impostata con **JavaKeyStorePassword**.|
|`public String getKeyStoreLocation()`|Recupera il keyStoreLocation per Store la chiave di Java.|
  
 **Classe SQLServerColumnEncryptionJavaKeyStoreProvider**  
  
 Implementazione del provider dell'archivio chiavi per l'archivio chiavi Java. Questa classe consente l'utilizzo di certificati archiviati nell'archivio chiavi Java come chiavi master della colonna.  
  
 Costruttori  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|Provider dell'archivio chiavi per la Store chiave Java.|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|Consente di effettuare la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato deve essere crittografato utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Sostituisce SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|Consente di eseguire la crittografia di una column encryption key utilizzando il certificato con il percorso della chiave specificato e l'algoritmo specificato.<br /><br /> **Il formato del percorso della chiave deve essere uno dei seguenti:**<br /><br /> Thumbprint:<certificate_thumbprint><br /><br /> Alias:<certificate_alias><br /><br /> (Sostituisce SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).)|  
|`public void setName (String name)`|Imposta il nome di questo provider dell'archivio chiavi.|
|`public String getName ()`|Ottiene il nome di questo provider dell'archivio chiavi.|
  
 **Classe SQLServerColumnEncryptionAzureKeyVaultProvider**  
  
 Implementazione del provider dell'archivio chiavi per Azure Key Vault. Questa classe consente di usare le chiavi archiviate in Azure Key Vault come chiavi master della colonna.  
  
 Costruttori  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Provider dell'archivio chiavi per Azure Key Vault.  È necessario specificare l'identificatore e la chiave del client richiede il token per l'autenticazione ad Azure Key Vault.|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Decryptes una chiave di crittografia di colonna crittografata (CEK). La decrittografia verrà eseguita mediante un algoritmo di crittografia RSA che usa la chiave asimmetrica specificata dal percorso della chiave master.<br />(Sostituisce SQLServerColumnEncryptionKeyStoreProvider. decryptColumnEncryptionKey(String, String, Byte[]).) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | Crittografa una chiave di crittografia di colonna, fornendo la chiave master della colonna specificata per l'algoritmo specificato.<br />(Sostituisce SQLServerColumnEncryptionKeyStoreProvider. encryptColumnEncryptionKey(String, String, Byte[]).) |  
|`public void setName (String name)`|Imposta il nome di questo provider dell'archivio chiavi.|
|`public String getName ()`|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
  
 **Interfaccia SQLServerKeyVaultAuthenticationCallback**  
  
 Questa interfaccia contiene un metodo per l'autenticazione di Azure Key Vault, che deve essere implementata dall'utente.  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|Il metodo deve essere sottoposto a override. Il metodo viene usato per ottenere l'accesso token da Azure Key Vault.|  
  
 **Classe SQLServerColumnEncryptionKeyStoreProvider**  
  
 Estendere questa classe per implementare un provider personalizzato dell’archivio delle chiavi.  
  
|nome|Descrizione|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|Classe base per tutti i provider degli archivi delle chiavi. Un provider personalizzato deve derivare da questa classe ed eseguire l'override delle relative funzioni membro e quindi registrarlo usando SQLServerConnection. registerColumnEncryptionKeyStoreProviders().|  
  
 Metodi  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|Metodo della classe base per eseguire la decrittografia del valore crittografato specificato di una column encryption key. Il valore crittografato dovrebbe essere crittografato utilizzando la chiave master della colonna con il percorso della chiave specificato e l'algoritmo specificato.|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|Metodo della classe base per eseguire la crittografia di una column encryption key utilizzando la column master key con il percorso della chiave specificato e l'algoritmo specificato.|
|`public abstract void setName(String name)`|Imposta il nome di questo provider dell'archivio chiavi.|
|`public abstract String getName()`|Ottiene il nome di questo provider dell'archivio chiavi.|  
  
 I metodi di nuovo o sottoposto a overload in **SQLServerPreparedStatement** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|Questi metodi sono sottoposti a overload con una precisione o un argomento di scala o entrambi per il supporto di Always Encrypted per i tipi di dati specifici che richiedono la precisione e informazioni sulla scala.|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che l'oggetto esistente `setTimestamp()` metodo viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per i nuovi metodi di utilizzo di colonne datetime e smalldatetime crittografate `setDateTime()` e `setSmallDateTime()` rispettivamente.|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|Imposta il parametro designato sul valore Java specificato.<br /><br /> Se il forceEncrypt booleana è impostata su true, la query parametro sarà necessario impostare solo se la colonna di designazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|  
  
 I metodi di nuovo o sottoposto a overload in **SQLServerCallableStatement** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|Questi metodi sono sottoposti a overload con una precisione o un argomento di scala o entrambi per il supporto di Always Encrypted per i tipi di dati specifici che richiedono la precisione e informazioni sulla scala.|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro di tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che l'oggetto esistente `setTimestamp()` metodo viene utilizzato per l'invio di valori dei parametri per la colonna crittografata datetime2. Per i nuovi metodi di utilizzo di colonne datetime e smalldatetime crittografate `setDateTime()` e `setSmallDateTime()` rispettivamente.|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|Imposta il parametro designato sul valore Java specificato.<br /><br /> Se il forceEncrypt booleana è impostata su true, la query parametro sarà necessario impostare solo se la colonna di designazione è crittografata e Always Encrypted è abilitato per la connessione o per l'istruzione.<br /><br /> Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|
 

 I metodi di nuovo o sottoposto a overload in **SQLServerResultSet** classe  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |Questi metodi vengono aggiunti per supportare la crittografia sempre attiva per il denaro i tipi di dati, smallmoney, uniqueidentifier, datetime e smalldatetime. <br/><br/>Si noti che l'oggetto esistente `updateTimestamp()` metodo viene utilizzato per l'aggiornamento delle colonne datetime2 crittografato. Per i nuovi metodi di utilizzo di colonne datetime e smalldatetime crittografate `updateDateTime()` e `updateSmallDateTime()` rispettivamente.|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|Aggiornare la colonna designata sul valore java specificato.<br/><br/>Se il forceEncrypt booleana è impostata su true, la colonna verrà essere impostata solo se sono crittografati e Always Encrypted è abilitato per la connessione o per l'istruzione.<br/><br/>Se il forceEncrypt booleana è impostata su false, il driver non forza la crittografia sui parametri.|

  
Nuovi tipi nella **microsoft.sql.Types** classe

|nome|Descrizione|  
|----------|-----------------|  
|DATETIME, SMALLDATETIME, MONEY, SMALLMONEY, GUID|Usare questi tipi come tipi SQL di destinazione quando si inviano i valori dei parametri **crittografato** datetime, smalldatetime, money, smallmoney, utilizzando colonne di tipo uniqueidentifier `setObject()/updateObject()` metodi dell'API.|  
  
  
 **Enumerazione SQLServerStatementColumnEncryptionSetting**  
  
 Specifica come cui dati verranno inviati e ricevuti durante la lettura e scrittura alle colonne crittografate. A seconda della query specifica, l'impatto sulle prestazioni può essere ridotto ignorando l'elaborazione del driver sempre crittografato quando si usano colonne non crittografate. Si noti che queste impostazioni non possono essere usate per ignorare la crittografia e ottenere l'accesso ai dati di testo normale.  
  
 **Sintassi**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **Membri**  
  
|nome|Descrizione|  
|----------|-----------------|  
|UseConnectionSetting|Specifica che il comando deve essere predefinito per l'impostazione di Always Encrypted nella stringa di connessione.|  
|Abilitata|Abilita Always Encrypted per la query.|  
|ResultSetOnly|Specifica che solo i risultati del comando devono essere elaborati in base alla routine sempre crittografato nel driver. Utilizzare questo valore quando il comando non dispone di parametri che richiedono la crittografia.|  
|Disabilitata|Disabilita Always Encrypted per la query.|  
  
 L'impostazione del livello di istruzione per Always Encrypted viene aggiunto alla classe SQLServerConnection e alla classe SQLServerConnectionPoolProxy. I metodi seguenti di queste classi sono sottoposti a overload con la nuova impostazione.  
  
|nome|Descrizione|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crea un oggetto istruzione che genera oggetti con set di risultati con il tipo specificato, la concorrenza, trattenibilità e impostazione di crittografia di colonna.|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|Crea un oggetto CallableStatement con l'impostazione di crittografia di colonna specificata che consentono di generare oggetti set di risultati con il tipo specificato, concorrenza e la trattenibilità.|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che ha la possibilità di recuperare le chiavi generate automaticamente.|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti set di risultati con i nomi di colonna specificato.|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che genera gli oggetti set di risultati con gli indici di colonna specificato.|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|Crea un oggetto di impostazione PreparedStatement con l'impostazione di crittografia di colonna specificata che consentono di generare oggetti set di risultati con il tipo specificato, concorrenza e la trattenibilità.|  
  
> [!NOTE]  
>  Se Always Encrypted è disabilitato per una query e la query include parametri che devono essere crittografati (parametri che corrispondono alle colonne crittografate), la query avrà esito negativo.  
>   
>  Se Always Encrypted è disabilitato per una query e la query restituisce risultati dalle colonne crittografate, la query restituirà i valori crittografati. I valori crittografati avranno il tipo di dati varbinary.  
  
 ## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Always Encrypted con il JDBC Driver](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

