---
title: Impostare o modificare le regole di confronto del server | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2019
ms.prod: sql
ms.reviewer: carlrab
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2bb8afe1e20e71245beea8f9482ff0aec4b047ba
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671138"
---
# <a name="set-or-change-the-server-collation"></a>Impostazione o modifica di regole di confronto del server

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Le regole di confronto del server costituiscono le regole di confronto predefinite per tutti i database di sistema installati con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e per ogni database utente creato successivamente. È consigliabile scegliere con attenzione le regole di confronto a livello di server perché interessano:
 - Regole di ordinamento e confronto in `=`, `JOIN`, `ORDER BY` e in altri operatori di confronto dei dati testuali.
 - Regole di confronto delle colonne `CHAR`, `VARCHAR`, `NCHAR` e `NVARCHAR` di viste di sistema, funzioni di sistema e oggetti in TempDB (ad esempio, tabelle temporanee).
 - Nomi di variabili, cursori ed etichette `GOTO`. Le variabili @pi e @PI vengono considerate variabili diverse se le regole di confronto a livello di server fanno distinzione tra maiuscole e minuscole, ma vengono considerate la stessa variabile se le regole di confronto a livello di server non fanno questa distinzione.
  
## <a name="setting-the-server-collation-in-sql-server"></a>Impostazione delle regole di confronto in SQL Server

  Le regole di confronto del server vengono specificate durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le regole di confronto predefinite corrispondono a **SQL_Latin1_General_CP1_CI_AS**. Regole di confronto solo Unicode non possono essere specificate come regole di confronto a livello di server. Per altre informazioni, vedere [Collation and Unicode Support](collation-and-unicode-support.md).
  
## <a name="changing-the-server-collation-in-sql-server"></a>Modifica delle regole di confronto in SQL Server

 La modifica delle regole di confronto predefinite per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere un'operazione complessa e richiede i passaggi seguenti:  
  
- Assicurarsi che siano disponibili tutte le informazioni o gli script necessari per ricreare i database utente e tutti gli oggetti in essi contenuti.  
  
- Esportare tutti i dati usando uno strumento come [l'utilità bcp](../../tools/bcp-utility.md). Per altre informazioni, vedere [Importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
- Eliminare tutti i database utente.  
  
- Ricompilare il database master specificando le nuove regole di confronto nella proprietà SQLCOLLATION del comando **setup** . Esempio:  
  
    ```sql  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]
    /SQLCOLLATION=CollationName  
    ```  
  
     Per altre informazioni, vedere [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md).  
  
- Creare tutti i database e tutti gli oggetti in essi contenuti.  
  
- Importare tutti i dati.  
  
> [!NOTE]  
> Anziché modificare le regole di confronto predefinite di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile specificare regole di confronto predefinite per ogni nuovo database creato.  
  
## <a name="setting-the-server-collation-in-managed-instance"></a>Impostazione delle regole di confronto del server in Istanza gestita

È possibile specificare regole di confronto a livello di server in Istanza gestita di database SQL di Azure (anteprima) durante la creazione dell'istanza, ma non è possibile cambiarle in seguito. È possibile impostare regole di confronto a livello di server tramite il [portale di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started#create-a-managed-instance) o tramite [PowerShell e il modello di Resource Manager ](https://docs.microsoft.com/azure/sql-database/scripts/sql-managed-instance-create-powershell-azure-resource-manager-template) durante la creazione dell'istanza. Le regole di confronto predefinite corrispondono a **SQL_Latin1_General_CP1_CI_AS**. Regole di confronto solo Unicode e nuove regole di confronto UTF-8 a livello di server non possono essere specificate come regole di confronto a livello di server.
Se si sta eseguendo la migrazione di database da SQL Server a Istanza gestita, controllare le regole di confronto del server nel database SQL Server di origine tramite la funzione `SERVERPROPERTY(N'Collation')` e creare un'Istanza gestita che corrisponda alle regole di confronto di SQL Server. La migrazione di un database da SQL Server a Istanza gestita con regole di confronto a livello di server non corrispondenti può causare diversi errori imprevisti nell'esecuzione di query. Non è possibile modificare le regole di confronto a livello di server nell'Istanza gestita esistente.

## <a name="see-also"></a>Vedere anche

 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Impostare o modificare le regole di confronto del database](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Impostare o modificare le regole di confronto delle colonne](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md)  
 
