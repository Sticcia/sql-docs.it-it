---
title: Usare il formato carattere per importare o esportare dati (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], character
- character formats [SQL Server]
ms.assetid: d925e66a-1a73-43cd-bc06-1cbdf8174a4d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e25c975dca01ee2787a598afbe1a67f09fbab0ce
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065764"
---
# <a name="use-character-format-to-import-or-export-data-sql-server"></a>Utilizzo del formato carattere per l'importazione o l'esportazione di dati (SQL Server)
  È consigliabile adottare il formato carattere per l'esportazione bulk in file di testo utilizzati in altri programmi o per l'importazione bulk da file di testo creati in altri programmi.  
  
> [!NOTE]  
>  Quando si esegue il trasferimento bulk dei dati tra le istanze di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il file di dati contiene dati di tipo carattere Unicode ma nessun carattere esteso o DBCS, usare il formato carattere Unicode. Per altre informazioni, vedere [Usare il formato carattere Unicode per importare o esportare dati &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 Quando si utilizza il formato carattere, in tutte le colonne viene applicato il formato dati di tipo carattere. L'archiviazione in formato carattere risulta utile quando i dati vengono utilizzati in altri programmi, ad esempio in un foglio di calcolo, o quando è necessario copiare in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i dati di database di altri fornitori, ad esempio Oracle.  
  
## <a name="considerations-for-using-character-format"></a>Considerazioni sull'utilizzo del formato carattere  
 Quando si utilizza il formato carattere, è necessario tenere presenti i fattori seguenti:  
  
-   Per impostazione predefinita, quando si esegue l'utilità **bcp** i campi dei dati di tipo carattere vengono separati da un carattere di tabulazione e alla fine dei record viene inserito un carattere di nuova riga. Per informazioni su come specificare caratteri di terminazione alternativi, vedere [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
-   Per impostazione predefinita, prima dell'esportazione o dell'importazione bulk di dati in modalità carattere, vengono eseguite le conversioni seguenti:  
  
    |Direzione dell'operazione bulk|Conversione|  
    |---------------------------------|----------------|  
    |Esportazione|I dati vengono convertiti in rappresentazione dei caratteri. Se richiesto in modo esplicito, la conversione viene eseguita in base alla tabella codici specificata per le colonne di tipo carattere. Se non è stata specificata alcuna tabella codici, i dati di tipo carattere vengono convertiti in base alla tabella codici OEM del computer client.|  
    |Importa|I dati di tipo carattere vengono convertiti in rappresentazione nativa, se necessario, e tradotti dalla tabella codici del client alla tabella codici delle colonne di destinazione.|  
  
-   Per impedire eventuali perdite di caratteri estesi durante la conversione, utilizzare il formato di carattere Unicode o specificare una tabella codici.  
  
-   I dati `sql_variant` archiviati in un file in formato carattere risultano privi di metadati. Ogni valore viene convertito nel formato `char` in base alle regole di conversione dei dati implicita. I dati importati in colonne `sql_variant` risultano di tipo `char`. I dati importati in colonne con tipo di dati diverso da `sql_variant` vengono convertiti dal tipo di dati `char` tramite una conversione implicita. Per altre informazioni sulla conversione dei dati, vedere [Conversione del tipo di dati &#40;Motore di database&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
-   Il **bcp** esportazioni utilità `money` valori come file di dati in formato carattere con quattro cifre dopo il separatore decimale e senza alcun simbolo di raggruppamento cifre, quali i separatori. Ad esempio, una colonna `money` contenente il valore 1,234,567.123456 viene copiata in un file di dati come stringa di caratteri 1234567.1235 tramite l'esportazione bulk.  
  
## <a name="command-options-for-character-format"></a>Opzioni del comando per il formato carattere  
 È possibile importare dati in formato carattere in una tabella con **bcp**, BULK INSERT o INSERT. SELECT \* FROM OPENROWSET(BULK...). Per un comando **bcp** o un'istruzione BULK INSERT, è possibile specificare il formato dati nella riga di comando. Per un'istruzione INSERT ... SELECT * FROM OPENROWSET(BULK...) è necessario specificare il formato dei dati in un file di formato.  
  
 Il formato carattere è supportato dalle opzioni della riga di comando seguenti:  
  
|Comando|Opzione|Descrizione|  
|-------------|------------|-----------------|  
|**bcp**|**-c**|Fa sì che il **bcp** utilità usare dati di tipo carattere.<sup> 1</sup>|  
|BULK INSERT|DATAFILETYPE **='char'**|Durante l'importazione bulk dei dati viene applicato il formato carattere.|  
  
 <sup>1</sup> per caricare il carattere (**- c**) dei dati in un formato compatibile con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client, utilizzare il **-V** passare. Per altre informazioni, vedere [Importare dati in formato nativo e carattere da versioni precedenti di SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Per altre informazioni, vedere [Utilità bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) o [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  In alternativa, è possibile definire la formattazione di ogni singolo campo in un file di formato. Per altre informazioni, vedere [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano come eseguire l'esportazione bulk dei dati di tipo carattere con l'utilità **bcp** e l'importazione bulk degli stessi dati con l'istruzione BULK INSERT.  
  
### <a name="sample-table"></a>Tabella di esempio  
 Negli esempi si presuppone la presenza della tabella **myTestCharData** all'interno dello schema **dbo** del database di esempio **AdventureWorks**. Prima di eseguire le procedure illustrate negli esempi, è necessario creare la tabella. A tale scopo, nell'editor di query di SQL [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] eseguire il codice seguente:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Per popolare la tabella e visualizzare il contenuto risultante, eseguire le istruzioni seguenti:  
  
```  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestCharData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData  
  
```  
  
### <a name="using-bcp-to-bulk-export-character-data"></a>Esportazione bulk di dati di tipo carattere tramite bcp  
 Per esportare i dati dalla tabella al file di dati, usare **bcp** con l'opzione **out** e i qualificatori seguenti:  
  
|Qualificatori|Descrizione|  
|----------------|-----------------|  
|**-c**|Specifica il formato carattere.|  
|**-t** `,`|Specifica la virgola (`,`) come carattere di terminazione del campo.<br /><br /> Nota: Il valore predefinito è il carattere di tabulazione (\t). Per altre informazioni, vedere [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).|  
|**-T**|Specifica che l'utilità **bcp** si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una connessione trusted che usa la sicurezza integrata. Se non si specifica **-T**, è necessario specificare **-U** e **-P** per eseguire correttamente l'accesso.|  
  
 Nell'esempio seguente viene eseguita l'esportazione bulk di dati in formato carattere dalla tabella `myTestCharData` a un nuovo file di dati denominato `myTestCharData-c.Dat` in cui il carattere di terminazione dei campi è la virgola (,). Al prompt dei comandi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows digitare:  
  
```  
bcp AdventureWorks..myTestCharData out C:\myTestCharData-c.Dat -c -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-character-data"></a>Importazione bulk di dati di tipo carattere tramite BULK INSERT  
 Nell'esempio seguente si utilizza BULK INSERT per importare i dati dal file di dati `myTestCharData-c.Dat` nella tabella `myTestCharData`. Nell'editor di query di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] eseguire:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestCharData   
   FROM 'C:\myTestCharData-c.Dat'   
   WITH (  
      DATAFILETYPE='char',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per utilizzare formati di dati per l'importazione o l'esportazione bulk**  
  
-   [Importare dati in formato nativo e carattere da versioni precedenti di SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utilizzo del formato nativo per importare o esportare dati &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo del formato carattere Unicode per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato Unicode nativo per importare o esportare dati &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Importare dati in formato nativo e carattere da versioni precedenti di SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
  
