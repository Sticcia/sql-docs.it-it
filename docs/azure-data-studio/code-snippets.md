---
title: Creare frammenti di codice riutilizzabile
titleSuffix: Azure Data Studio
description: Informazioni su come creare e usare frammenti di codice SQL in Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 2c9e4b38fceedc9a2bfe7690cab759cdc77ea8f2
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105332"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-includename-sosincludesname-sos-shortmd"></a>Creare e usare i frammenti di codice per creare rapidamente script Transact-SQL (T-SQL) in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Frammenti di codice in [!INCLUDE[name-sos](../includes/name-sos-short.md)] sono modelli che semplificano la creazione di database e oggetti di database. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce diversi frammenti di T-SQL che aiutano a generare rapidamente la sintassi corretta. 

È anche possibile creare frammenti di codice definiti dall'utente.

## <a name="using-built-in-t-sql-code-snippets"></a>Uso di frammenti di codice T-SQL incorporati

1. Per accedere i frammenti disponibili, digitare *sql* nell'editor di query per aprire l'elenco:

   ![frammenti](media/code-snippets/sql-snippets.png)

1. Selezionare il frammento di codice che si desidera utilizzare e generare lo script T-SQL. Ad esempio, selezionare *sqlCreateTable*:

   ![Lista di frammenti di codice](media/code-snippets/create-table.png)

1. Aggiornare i campi evidenziati con valori specifici. Ad esempio, sostituire *TableName* e *Schema* con i valori per il vostro database:

   ![Sostituire il campo nel modello](media/code-snippets/table-from-snippet.png)

   Se il campo che si desidera modificare non è più evidenziato (ciò avviene quando si sposta il cursore nell'editor), premere il tasto destro del mouse sulla parola che si desidera aggiornare, quindi scegliere **Cambia tutte le occorrenze**:

   ![Sostituire il campo nel modello](media/code-snippets/change-all.png)

1. Aggiornare o aggiungere eventuali ulteriori parti di T-SQL per il frammento di codice selezionato. Ad esempio, aggiornare *Column1*, *Column2* e aggiungere altre colonne.


 
## <a name="creating-sql-code-snippets"></a>Creazione di frammenti di codice SQL 

È possibile definire frammenti personalizzati. Per aprire il file del frammento di codice SQL per la modifica:

1. Aprire il *riquadro comandi* (**Ctrl + MAIUSC + P**) e il tipo *snip*e selezionare **preferenze: Aprire i frammenti di codice utente**:

   ![Sostituire il campo nel modello](media/code-snippets/user-snippets.png)

1. Selezionare **SQL**:

   > [!NOTE]
   > [!INCLUDE[name-sos](../includes/name-sos-short.md)] eredita la funzionalità dei frammento di codice da Visual Studio Code. Questo articolo illustra in particolare l'utilizzo dei frammenti SQL. Per ulteriori informazioni, vedere [Creare frammenti personalizzati](https://code.visualstudio.com/docs/editor/userdefinedsnippets) nella documentazione di Visual Studio Code. 

   ![Sostituire il campo nel modello](media/code-snippets/select-sql.png)

1. Incollare il codice seguente nel *sql.json*:

   ```sql
   {
   "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "   $1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "   Column1 [NVARCHAR](50) NOT NULL,",
    "   Column2 [NVARCHAR](50) NOT NULL",
    "   -- specify more columns here",
    ");",
    "GO"
    ],
   "description": "User-defined snippet example 2"
   }
   }
   ```

1. Salvare il file sql.json.
1. Aprire una nuova finestra editor di query premendo **Ctrl+N**.
2. Digitare **sql** per visualizzare i frammenti di codice dei due utenti appena aggiunti: *sqlCreateTable2* e *sqlSelectTop5*.

Selezionare uno dei nuovi frammenti di codice e avviare un'esecuzione di prova.


## <a name="additional-resources"></a>Risorse aggiuntive

Per informazioni sull'editor SQL, vedere [esercitazione di editor di codice](tutorial-sql-editor.md).
