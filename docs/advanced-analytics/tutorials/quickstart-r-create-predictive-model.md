---
title: Guida introduttiva per creare un modello predittivo con R - SQL Server Machine Learning
description: Questa Guida introduttiva descrive come compilare un modello in R con dati di SQL Server per tracciare le stime.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 278eba1189b376b57f2dec7249a378832c18095c
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046864"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Guida introduttiva: Creare un modello predittivo tramite R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa Guida introduttiva, si sarà informazioni su come eseguire il training di un modello usando R e quindi salvare il modello in una tabella in SQL Server. Il modello è un semplice modello lineare generalizzato (GLM) che consente di prevedere probabilità che un veicolo è stato dotato di una trasmissione manuale. Si userà il `mtcars` set di dati incluso in R.

## <a name="prerequisites"></a>Prerequisiti

Una Guida introduttiva precedente [R verificare esiste nel Server SQL](quickstart-r-verify.md), vengono fornite informazioni e collegamenti per configurare l'ambiente R necessario per questa Guida introduttiva.

## <a name="create-the-source-data"></a>Creare i dati di origine

Creare prima di tutto una tabella in cui salvare i dati di training.

```sql
CREATE TABLE dbo.MTCars(
    mpg decimal(10, 1) NOT NULL,
    cyl int NOT NULL,
    disp decimal(10, 1) NOT NULL,
    hp int NOT NULL,
    drat decimal(10, 2) NOT NULL,
    wt decimal(10, 3) NOT NULL,
    qsec decimal(10, 2) NOT NULL,
    vs int NOT NULL,
    am int NOT NULL,
    gear int NOT NULL,
    carb int NOT NULL
);
```

Successivamente, inserire i dati dalla compilazione di set di dati `mtcars`.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Alcuni utenti preferiscono usare le tabelle temporanee, ma tenere presente che alcuni client R disconnettere le sessioni tra i batch.

+ Nel runtime R sono inclusi diversi set di dati di piccole e grandi dimensioni. Per ottenere un elenco di set di dati installati con R, digitare `library(help="datasets")` da un prompt dei comandi R.

## <a name="create-a-model"></a>Creare un modello

I dati di velocità delle auto contengono due colonne, entrambe numeriche, potenza (`hp`) e il peso (`wt`). Da questi dati, si creerà un modello lineare generalizzato (GLM) che stima la probabilità che un veicolo è stato dotato di una trasmissione manuale.

Per compilare il modello, definire la formula all'interno del codice R e passare i dati come parametro di input.

```sql
DROP PROCEDURE IF EXISTS generate_GLM;
GO
CREATE PROCEDURE generate_GLM
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'carsModel <- glm(formula = am ~ hp + wt, data = MTCarsData, family = binomial);
        trained_model <- data.frame(payload = as.raw(serialize(carsModel, connection=NULL)));'
    , @input_data_1 = N'SELECT hp, wt, am FROM MTCars'
    , @input_data_1_name = N'MTCarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model VARBINARY(max)));
END;
GO
```

+ Il primo argomento `glm` è il *formula* parametro, che definisce `am` come dipendenti nella `hp + wt`.
+ I dati di input vengono archiviati nella variabile `MTCarsData`, popolata dalla query SQL. Se non si assegna un nome specifico ai dati di input, il nome predefinito della variabile sarà _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Creare una tabella per il modello

Quindi, archiviare il modello in modo che è possibile ripetere il training o usarlo per la stima. L'output di un pacchetto R che crea un modello è in genere un **oggetto binario**. Pertanto, la tabella in cui si archivia il modello deve contenere una colonna di **varbinary (max)** tipo.

```sql
CREATE TABLE GLM_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
```

## <a name="save-the-model"></a>Salvare il modello

Per salvare il modello, eseguire l'istruzione Transact-SQL seguente per chiamare la stored procedure, generare il modello e salvarlo in una tabella.

```sql
INSERT INTO GLM_models(model)
EXEC generate_GLM;
```

Si noti che se si esegue questo codice una seconda volta, viene visualizzato questo errore:

```sql
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Un modo per evitare questo errore consiste nell'aggiornare il nome di ogni nuovo modello. È ad esempio possibile sostituire il nome con uno più descrittivo e includere il tipo di modello, il giorno della creazione e così via.

```sql
UPDATE GLM_models
SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="next-steps"></a>Passaggi successivi

Ora che si dispone di un modello, nella Guida introduttiva finale, si apprenderà come generare le stime da esso e tracciare i risultati.

> [!div class="nextstepaction"]
> [Guida introduttiva: Stimare e creare un tracciato dal modello](quickstart-r-predict-from-model.md)