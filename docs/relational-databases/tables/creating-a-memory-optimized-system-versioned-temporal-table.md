---
title: Creazione di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 05/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c1fc682-bf5b-4096-a0ff-3235d71c205a
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 32df29be26fb5e26217a09bbb20b9cef39539aee
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="creating-a-memory-optimized-system-versioned-temporal-table"></a>Creazione di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Come per la creazione di una tabella di cronologia basata su disco, è possibile creare una tabella temporale con ottimizzazione per la memoria in diversi modi.  
  
> [!NOTE]  
>  Per creare tabelle con ottimizzazione per la memoria, è necessario innanzitutto creare [il filegroup con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md).  
  
 Creare una tabella temporale con una tabella di cronologia predefinita è una soluzione comoda quando si vuole controllare la denominazione e al tempo stesso lasciare che sia il sistema a creare la tabella di cronologia con la configurazione predefinita. L'esempio seguente illustra una nuova tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria collegata a una nuova tabella di cronologia basata su disco.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH   
    (  
        MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,  
            SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )   
    );  
```  
  
 La creazione di una tabella temporale collegata a una tabella di cronologia esistente è utile quando si vuole aggiungere il controllo delle versioni di sistema usando una tabella esistente, ad esempio quando si vuole eseguire la migrazione di una soluzione temporale personalizzata al supporto predefinito. Nell'esempio seguente viene creata una nuova tabella temporale collegata a una tabella di cronologia esistente.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (  
        SYSTEM_VERSIONING = ON  
            (  
                HISTORY_TABLE = dbo.Department_History  
                , DATA_CONSISTENCY_CHECK = ON   
            )  
        , MEMORY_OPTIMIZED = ON  
        , DURABILITY = SCHEMA_AND_DATA  
    );  
```  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
 Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Creating%20a%20Memory-Optimized%20System-Versioned%20Temporal%20Table%20page)  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Utilizzo di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Monitoraggio di una tabella temporale con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Considerazioni sulle prestazioni con le tabelle temporali con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)   
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)   
 [Verifiche di coerenza del sistema della tabella temporale](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Funzioni e viste per i metadati delle tabelle temporali](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
