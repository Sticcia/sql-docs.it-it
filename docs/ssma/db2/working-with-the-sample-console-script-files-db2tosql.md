---
title: Lavorare con i file di Script di esempio Console (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5c3080c3-d074-4f99-a5f5-219ebeddc474
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dc7976fae322dddc24eda7cf6ef84ef20a7a9e61
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259007"
---
# <a name="working-with-the-sample-console-script-files-db2tosql"></a>Lavorare con i file di Script di esempio Console (DB2ToSQL)
Alcuni file di esempio sono stati forniti insieme al prodotto per il riferimento all'utente e l'utilizzo. In questa sezione descrive il modo con facilità personalizzare questi script per soddisfare le esigenze degli utenti finali.  
  
## <a name="sample-console-script-files"></a>File di Script di esempio Console  
I seguenti file script di esempio console relativi a diversi scenari sono stati forniti i riferimenti all'utente:  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
1.  **ServersConnectionFileSample.xml:**  
  
    -   In questo esempio offre diverse modalità di connessione disponibili per il database di origine e destinazione e l'utente può selezionare qualsiasi modalità in base al requisito. In questo esempio contiene le definizioni di Server.  
  
    -   L'utente può connettersi al database obbligatorio modificando semplicemente i valori per l'origine necessari e le definizioni dei server di destinazione. Nell'esempio fornito tutti i valori sono stati forniti valori come variabili che sono disponibili nel **VariableValueFileSample.xml**.  Tutti gli altri parametri di connessione possono essere rimosso dal file di connessione server di lavoro dell'utente.  
  
    -   Per altre informazioni sulla connessione al server di origine e di destinazione, vedere [creazione di file di connessione del Server &#40;DB2ToSQL&#41; ](../../ssma/db2/creating-the-server-connection-files-db2tosql.md) .  
  
2.  **VariableValueFileSample.xml:** Tutte le variabili che sono state utilizzate nella console di esempio i file di script e `ServersConnectionFileSample.xml` sono stati confrontati in questo file. Per eseguire gli script di esempio console che l'utente deve semplicemente sostituire la variabile di esempio i valori con l'utente definito quelle e passare questo file come un argomento della riga di comando aggiuntivi insieme al file di script.  
  
    Per altre informazioni sul File con valori variabili, vedere [creazione di file di valore variabile &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md).  
  
3.  **AssessmentReportGenerationSample.xml:** In questo esempio consente all'utente generare un report di valutazione di xml che può essere utilizzato dall'utente per l'analisi prima che inizi a convertire e la migrazione dei dati.  
  
    Nel `generate-assessment-report` l'utente deve modificare obbligatoriamente includere il valore della variabile di comando (fare riferimento **VariableValueFileSample.xml**) nella `object-name` attributo al nome di database da in uso dall'utente. A seconda del tipo dell'oggetto specificato, il `object-type` valore dovrà inoltre essere modificato.  
  
    Se l'utente dispone valutare più oggetti / database è possibile specificare più `metabase-object` nodi come illustrato nella `generate-assessment-report` 4 di esempio del comando del file di script di esempio console.  
  
    Per altre informazioni sulla generazione di report, vedere [generazione di report &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
    **Note:**  
  
    Assicurarsi che l'argomento della riga di comando file valore della variabile viene passato all'applicazione console e VariableValueFileSample.xml viene aggiornato con l'utente specificato i valori.  
  
    Assicurarsi che l'argomento della riga di comando file connessione server viene passato all'applicazione console e il ServersConnectionFileSample.xml viene aggiornata con i valori dei parametri server corretto.  
  
4.  **SqlStatementConversionSample.xml:** In questo esempio consente all'utente genera il corrispondente `t-sql` script per database di origine `sql` comando fornito come input.  
  
    Nel `convert-sql-statement` l'utente deve modificare obbligatoriamente includere il valore della variabile di comando (fare riferimento **VariableValueFileSample.xml**) nel `context` attributo al nome del database che è in corso in uso dall'utente. L'utente sarà inoltre necessario modificare il `sql` valore dell'attributo per il database di origine `sql` comando che può richiedere da convertire.  
  
    L'utente può anche fornire i file sql da convertire. Questa operazione è stata illustrata nel `convert-sql-statement` 4 di esempio del comando del file di script di esempio console.  
  
    > [!NOTE]  
    > Assicurarsi che l'argomento della riga di comando file valore della variabile viene passato all'applicazione console e VariableValueFileSample.xml viene aggiornato con l'utente specificato i valori.  
  
5.  **ConversionAndDataMigrationSample.xml:** In questo esempio consente all'utente di eseguire una migrazione end-to-end dalla conversione per la migrazione dei dati. L'elenco di valori di attributo obbligatorio che dovranno cambiare è elencato di seguito:  
  
    |Nome del comando|Descrizione|attribute|  
    |----------------|---------------|-------------|  
    |`map-schema`|Mapping dello schema del database di origine allo schema di destinazione.|`source-schema:` Specifica il database di origine che richiede da convertire.<br /><br />`sql-server-schema`: Specifica il database di destinazione che deve essere eseguita la migrazione a|  
    |`convert-schema`|Esegue la conversione dello schema di origine allo schema di destinazione.<br /><br />Se l'utente dispone valutare più oggetti / database è possibile specificare più `metabase-object` nodi come illustrato nella `convert-schema` 4 di esempio del comando del file di script di esempio console.|`object-name`: Specificare il database di origine / nome che richiede la conversione dell'oggetto. Assicurarsi che la corrispondente `object-type` viene modificato in base al tipo di oggetto specificato di `object-name`|  
    |`synchronize-target`|Sincronizza gli oggetti di destinazione con il database di destinazione.<br /><br />Se l'utente dispone valutare più oggetti / database è possibile specificare più `metabase-object` nodi come illustrato nella `synchronize-target` 3 di esempio del comando del file di script di esempio console.|`object-name:` Specificare il database di sql server / nome che richiede la creazione dell'oggetto. Assicurarsi che la corrispondente `object-type` viene modificato in base al tipo di oggetto specificato di `object-name`|  
    |`migrate-data`|Esegue la migrazione dei dati di origine alla destinazione.<br /><br />Se l'utente dispone valutare più oggetti / database è possibile specificare più `metabase-object` nodi come illustrato nella `migrate-data` 2 di esempio del comando del file di script di esempio console.|`object-name:` Specifica il database di origine / nome che è necessario eseguire la migrazione di tabelle. Assicurarsi che la corrispondente `object-type` viene modificato in base al tipo di oggetto specificato di `object-name`|  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di file di valore della variabile &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
[Creazione di file di connessione del Server &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
[Generating Reports &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)  
  
