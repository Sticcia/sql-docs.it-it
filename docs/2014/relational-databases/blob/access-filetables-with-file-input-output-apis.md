---
title: Accedere alle tabelle FileTable con API di input/output dei file | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with file APIs
ms.assetid: fa504c5a-f131-4781-9a90-46e6c2de27bb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8c12736694451d1a6fd1dff34c4f883cb45694e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876913"
---
# <a name="access-filetables-with-file-input-output-apis"></a>Accedere alle tabelle FileTable con API di Input-Output dei file
  Viene descritto il funzionamento dell'I/O del file system in una tabella FileTable.  
  
##  <a name="accessing"></a> Iniziare a utilizzare le API di I/O dei file con tabelle FileTable  
 L'utilizzo principale delle tabelle FileTable avviene tramite il file system di Windows e l'API di I/O dei file. Le tabelle FileTable supportano l'accesso non transazionale tramite la vasta gamma di API di I/O dei file disponibili.  
  
1.  L'accesso dell'API di l'I/O dei file inizia in genere con l'acquisizione di un percorso UNC logico per il file o la directory. Le applicazioni possono usare un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] con la funzione [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql) per ottenere il percorso logico per il file o la directory. Per altre informazioni, vedere [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).  
  
2.  Nell'applicazione viene utilizzato quindi questo percorso logico per ottenere un handle al file o alla directory ed eseguire un'operazione sull'oggetto. Il percorso può essere passato a qualsiasi funzione dell'API del file system supportata, ad esempio CreateFile() o CreateDirectory() per creare o aprire un file e ottenere un handle. L'handle può essere quindi utilizzato per trasmettere dati, enumerare o organizzare directory, ottenere o impostare attributi di file, eliminare file o directory e così via.  
  
##  <a name="create"></a> Creazione di file e directory in una tabella FileTable  
 È possibile creare un file o una directory in una tabella FileTable chiamando un'API di I/O dei file quale CreateFile o CreateDirectory.  
  
-   Sono supportati tutti i flag di creazione di disposizioni e tutte le modalità di condivisione e di accesso. Sono incluse la creazione, l'eliminazione e la modifica sul posto dei file. Sono supportati anche gli aggiornamenti dello spazio dei nomi dei file, ad esempio le operazioni di creazione o eliminazione, ridenominazione e spostamento di directory.  
  
-   La creazione di un nuovo file o di una nuova directory corrisponde alla creazione di una nuova riga nella tabella FileTable sottostante.  
  
-   Per i file, i dati del flusso vengono archiviati nella colonna **file_stream** , mentre questa colonna è Null per le directory.  
  
-   Per i file la colonna **is_directory** contiene **false**. Per le directory questa colonna contiene **true**.  
  
-   La condivisione e la concorrenza dell'accesso vengono applicate quando più operazioni di I/O di file simultanee o operazioni [!INCLUDE[tsql](../../includes/tsql-md.md)] influiscono sullo stesso file o sulla stessa directory della gerarchia.  
  
##  <a name="read"></a> Lettura di file e directory in una tabella FileTable  
 La semantica dell'isolamento Read Committed viene applicata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per tutte le operazioni di accesso I/O dei file sui dati del flusso e degli attributi.  
  
##  <a name="write"></a> Scrittura e aggiornamento di file e directory in una tabella FileTable  
  
-   Tutte le operazioni di scrittura o aggiornamento I/O di file su tabelle FileTable non sono transazionali. Ciò significa che a queste operazioni non è associata alcuna transazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che non vi sono garanzie ACID.  
  
-   Tutti gli aggiornamenti sul posto o del flusso di I/O dei file sono supportati per la tabella FileTable.  
  
-   Gli aggiornamenti di dati o di attributi FILESTREAM tramite API di I/O dei file comportano l'aggiornamento delle colonne **file_stream** e degli attributi dei file corrispondenti nella tabella FileTable.  
  
##  <a name="delete"></a> Eliminazione di file e directory in una tabella FileTable  
 Tutta la semantica delle API di I/O dei file di Windows viene applicata quando si elimina un file o una directory.  
  
-   L'eliminazione di una directory non riesce se la directory contiene sottodirectory di file.  
  
-   L'eliminazione di un file o di una directory comporta la rimozione della riga corrispondente dalla tabella FileTable. Questa operazione equivale a eliminare la riga tramite un'operazione [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
##  <a name="supported"></a> Operazioni del file system supportate  
 Le tabelle FileTable supportano le API del file system correlate alle operazioni del file system seguenti:  
  
-   Gestione delle directory  
  
-   Gestione dei file  
  
 Le tabelle FileTable non supportano le operazioni seguenti:  
  
-   Gestione del disco  
  
-   Gestione dei volumi  
  
-   NTFS transazionale  
  
##  <a name="considerations"></a> Considerazioni aggiuntive relative all'accesso di I/O dei file in tabelle FileTable  
  
###  <a name="vnn"></a> Utilizzo di nomi di rete virtuale con i gruppi di disponibilità AlwaysOn  
 Quando il database che contiene dati FILESTREAM o FileTable appartiene a un gruppo di disponibilità AlwaysOn, quindi ogni accesso a dati FILESTREAM o FileTable tramite le API del file system deve utilizzare VNN anziché nomi computer. Per altre informazioni, vedere [FILESTREAM e FileTable con i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).  
  
###  <a name="partial"></a> Aggiornamenti parziali  
 Per eseguire aggiornamenti sul posto parziali del contenuto FILESTREAM è possibile usare un handle scrivibile ottenuto per i dati FILESTREAM in una tabella FileTable tramite la funzione [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql). Questo comportamento è diverso dall'accesso transazionale di FILESTREAM tramite un handle ottenuto chiamando **OpenSQLFILESTREAM()** e passando un contesto della transazione esplicito.  
  
###  <a name="trans"></a> Semantica transazionale  
 Quando si accede ai file di una tabella FileTable tramite le API di I/O dei file, queste operazioni non sono associate ad alcuna transazione utente e dispongono delle funzionalità aggiuntive seguenti:  
  
-   Poiché l'accesso non in transazioni a dati FILESTREAM in una tabella FileTable non è associato ad alcuna transazione, non dispone di alcuna semantica di isolamento specifica. Tuttavia è possibile che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzi transazioni interne per applicare la semantica di blocco o di concorrenza sui dati della tabella FileTable. Qualsiasi transazione interna di questo tipo viene eseguita con l'isolamento Read Committed.  
  
-   Non vi sono garanzie ACID per queste operazioni non in transazioni su dati FILESTREAM. Le garanzie di coerenza sono simili a quelle per gli aggiornamenti dei file eseguiti dalle applicazioni del file system.  
  
-   Il rollback di tali modifiche non è possibile.  
  
 È tuttavia possibile accedere alla colonna FILESTREAM in una tabella FileTable anche con l'accesso FILESTREAM transazionale chiamando **OpenSqlFileStream()**. Questo tipo di accesso può essere completamente transazionale e soddisferà tutti i livelli di coerenza delle transazioni attualmente supportati.  
  
###  <a name="concurrency"></a> Controllo della concorrenza  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applica il controllo della concorrenza per l'accesso alla tabella FileTable tra applicazioni del file system, nonché tra applicazioni del file system e applicazioni [!INCLUDE[tsql](../../includes/tsql-md.md)] . Questo controllo della concorrenza viene effettuato applicando blocchi appropriati nelle righe della tabella FileTable.  
  
###  <a name="triggers"></a> Trigger  
 La creazione, la modifica o l'eliminazione di file o directory o dei relativi attributi tramite il file system produce operazioni di inserimento, aggiornamento o eliminazione corrispondenti nella tabella FileTable. Tutti i trigger DML [!INCLUDE[tsql](../../includes/tsql-md.md)] associati vengono attivati come parte di tali operazioni.  
  
##  <a name="funclist"></a> Funzionalità del file system supportate nelle tabelle FileTable  
  
|Funzionalità|Supported|Commenti|  
|----------------|---------------|--------------|  
|**Blocchi opportunistici (oplock)**|Yes|È disponibile il supporto opportunistico per livello 1, livello 2, batch e filtri.|  
|**Attributi estesi**|No||  
|**Punti di analisi**|No||  
|**ACL persistenti**|No||  
|**Flussi denominati**|No||  
|**File sparse**|Yes|Il tipo sparse può essere impostato solo per i file e influisce sull'archiviazione del flusso dei dati. Poiché i dati FILESTREAM vengono archiviati in volumi NTFS, la funzionalità FileTable supporta file sparse inoltrando le richieste al file system NTFS.|  
|**Compressione**|Yes||  
|**Crittografia**|Yes||  
|**TxF**|No||  
|**ID file**|No||  
|**ID oggetto**|No||  
|**Collegamenti simbolici**|No||  
|**Collegamenti reali**|No||  
|**Nomi brevi**|No||  
|**Notifiche di modifica di directory**|No||  
|**Blocco di intervalli di byte**|Yes|Le richieste del blocco degli intervalli di byte vengono passate al file system NTFS.|  
|**File di cui è stato eseguito il mapping in memoria**|no||  
|**Annullamento I/O**|Yes||  
|**Sicurezza**|No|Vengono applicate la sicurezza a livello di condivisione di Windows e la sicurezza a livello di tabella e di colonna di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Journal USN**|No|Le modifiche ai metadati di file e directory in una tabella FileTable sono operazioni DML in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vengono pertanto registrate nel file di log del database corrispondente. Non vengono invece registrate nel journal USN NTFS, ad eccezione delle modifiche di dimensione.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per acquisire informazioni simili.|  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento di file in FileTable](load-files-into-filetables.md)   
 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)   
 [Accesso a tabelle FileTable tramite Transact-SQL](access-filetables-with-transact-sql.md)   
 [DDL FileTable, funzioni, stored Procedure e viste](../views/views.md)  
  
  
