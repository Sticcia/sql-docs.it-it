---
title: funzioni di supporto sqlrutils - servizi di SQL Server Machine Learning
description: Usare la libreria di funzione sqlrutils in SQL Server 2016 R Services e servizi di SQL Server 2017 Machine Learning con R per generare le stored procedure che contiene lo script R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7ccc3ad494658fc7a8f9c67472aecb1c4cddb7da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641748"
---
# <a name="sqlrutils-r-library-in-sql-server"></a>sqlrutils (libreria R in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il pacchetto **sqlrutils** fornisce un meccanismo che consente agli utenti di R di inserire gli script R in una stored procedure T-SQL, registrare la stored procedure con un database ed eseguirla da un ambiente di sviluppo R. 

Effettuando la conversione del codice R per consentirne l'esecuzione all'interno di una singola stored procedure, è possibile ottimizzare l'uso di SQL Server R Services. Per questo è necessario che uno script R sia incorporato come parametro in [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Il pacchetto **sqlrutils** consente di creare questo script R incorporato e di impostare i parametri correlati in modo appropriato.

Il pacchetto **sqlrutils** esegue queste attività:

- Salva lo script T-SQL generato come stringa all'interno di una struttura di dati R.
- Facoltativamente, genera un file con estensione sql per lo script T-SQL, che è possibile modificare o eseguire per creare una stored procedure.
- Registra la stored procedure creata con l'istanza di SQL Server dall'ambiente di sviluppo R.

È anche possibile eseguire la stored procedure da un ambiente R, passando i parametri corretti ed elaborando i risultati. In alternativa, è possibile usare la stored procedure da SQL Server per supportare scenari comuni di integrazione di database, ad esempio i processi di estrazione, trasformazione e caricamento (ETL, Extract, Transform, Load), il training di modelli e l'assegnazione di punteggi a grandi volumi di dati.

  > [!NOTE]
  > Se si intende eseguire la stored procedure da un ambiente R chiamando la funzione *executeStoredProcedure* , è necessario usare un provider ODBC 3.8, ad esempio ODBC Driver 13 for SQL Server.  
  
## <a name="full-reference-documentation"></a>Documentazione di riferimento complete

Il **sqlrutils** libreria distribuita in vari prodotti Microsoft, ma che utilizzo è lo stesso sia ottenere la libreria in SQL Server o un altro prodotto. Perché le funzioni sono gli stessi, [documentazione per le funzioni sqlrutils singoli](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) pubblicata in un'unica posizione sotto il [riferimento R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) per Microsoft Machine Learning Server. Qualsiasi prodotto specifico deve comportamenti esistono, verranno indicate nella pagina della Guida funzione discrepanze.

## <a name="functions-list"></a>Elenco di funzioni

La sezione seguente viene fornita una panoramica delle funzioni che è possibile chiamare dal **sqlrutils** incorporati di pacchetto per lo sviluppo di una stored procedure contenente codice R. Per informazioni dettagliate dei parametri per ogni metodo o funzione, vedere la Guida di R per il pacchetto: `help(package="sqlrutils")`

|Funzione | Descrizione |
|------|-------------|
|[executeStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/executestoredprocedure)| Eseguire una stored procedure SQL.|
|[getInputParameters](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/getinputparameters)| Ottenere un elenco di parametri di input per la stored procedure.| 
|[InputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputdata)| Definisce l'origine dei dati di SQL Server che verranno usati nel frame di dati R. Specificare il nome del frame di dati in cui archiviare i dati di input e una query per ottenere i dati o un valore predefinito. Sono supportate solo query SELECT. | 
|[InputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/inputparameter)| Definisce un singolo parametro di input che verrà incorporato nello script T-SQL. È necessario specificare il nome del parametro e il tipo di dati R corrispondente.| 
|[OutputData](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputdata)| Genera un oggetto dati intermedio che è necessario se la funzione R restituisce un elenco contenente un frame di dati. L'oggetto *OutputData* viene usato per archiviare il nome di un singolo frame di dati ottenuto dall'elenco.| 
|[OutputParameter](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/outputparameter) | Genera un oggetto dati intermedio che è necessario se la funzione R restituisce un elenco. L'oggetto *OutputParameter* archivia il nome e il tipo di dati di un singolo membro dell'elenco, presupponendo che tale membro **non** sia un frame di dati. |
|[registerStoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/registerstoredprocedure) | Registrare la stored procedure con un database.|
|[setInputDataQuery](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputdataquery)| Assegnare una query a un parametro di dati di input della stored procedure.| 
|[setInputParameterValue](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/setinputparametervalue)| Assegnare un valore a un parametro di input della stored procedure.| 
|[StoredProcedure](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/storedprocedure)| Un oggetto stored procedure.|


## <a name="how-to-use-sqlrutils"></a>Come usare sqlrutils

Il **sqlrutils** funzioni della libreria è necessario eseguire in un computer con SQL Server Machine Learning con R. Se si lavora in una workstation client, impostare un contesto di calcolo remoto per l'esecuzione di MAIUSC a SQL Server. Il flusso di lavoro per l'uso di questo pacchetto include i passaggi seguenti:

+ Definire parametri di stored procedure (input, output o entrambi) 
+ Generare e registrare la stored procedure    
+ Eseguire la stored procedure  

In una sessione di R, caricare **sqlrutils** dalla riga di comando digitando `library(sqlrutils)`.

> [!Note]
> È possibile caricare la libreria in computer che non dispone di SQL Server (ad esempio, in un'istanza di R Client) se si modifica il contesto di calcolo di SQL Server ed eseguire il codice in tale contesto di calcolo.


### <a name="define-stored-procedure-parameters-and-inputs"></a>Definire i parametri della stored procedure e gli input

`StoredProcedure` è il costruttore principale usato per creare la stored procedure. Questo costruttore genera un oggetto *stored procedure di SQL Server* e, facoltativamente, crea un file di testo contenente una query che può essere usata per generare la stored procedure tramite un comando T-SQL. 

Facoltativamente, la funzione *StoredProcedure* può anche registrare la stored procedure con il database e l'istanza specificati.

+ Usare l'argomento `func` per specificare una funzione R valida. Tutte le variabili usate dalla funzione devono essere definite all'interno della funzione o specificate come parametri di input. Questi parametri possono includere al massimo un frame di dati.

+ La funzione R deve restituire un frame di dati, un elenco denominato o un valore NULL. Se la funzione restituisce un elenco, questo può contenere al massimo un frame di dati.

+ Usare l'argomento `spName` per specificare il nome della stored procedure che si vuole creare.

+ È possibile passare parametri di output e input facoltativi usando gli oggetti creati da queste funzioni helper: `setInputData`, `setInputParameter`e `setOutputParameter`.

+  Facoltativamente, usare `filePath` per specificare il percorso e il nome di un file con estensione sql da creare. È possibile eseguire questo file nell'istanza di SQL Server per generare la stored procedure mediante T-SQL.

+ Per definire il server e il database in cui verrà salvata la stored procedure, usare gli argomenti `dbName` e  `connectionString`.

+ Per ottenere l'elenco degli oggetti *InputData* e *InputParameter* usati per creare un oggetto *StoredProcedure* specifico, chiamare `getInputParameters`. 

+ Per registrare la stored procedure con il database specificato, usare `registerStoredProcedure`.

All'oggetto stored procedure non sono in genere associati dati o valori, a meno che non sia stato specificato un valore predefinito. I dati non vengono recuperati finché non viene eseguita la stored procedure. 

### <a name="specify-inputs-and-execute"></a>Specificare gli input ed eseguire

+ Usare `setInputDataQuery` per assegnare una query a un oggetto *InputParameter* . Se ad esempio è stato creato un oggetto stored procedure in R, è possibile usare `setInputDataQuery` per passare argomenti alla funzione *StoredProcedure* in modo da eseguire la stored procedure con gli input desiderati.

+ Usare `setInputValue` per assegnare valori specifici a un parametro archiviato come oggetto *InputParameter* . Passare quindi l'oggetto parametro e il valore assegnato relativo alla funzione *StoredProcedure* per eseguire la stored procedure con i valori impostati.

+ Usare `executeStoredProcedure` per eseguire una stored procedure definita come oggetto *StoredProcedure* . Chiamare questa funzione solo quando si esegue una stored procedure dal codice R. Non usarla quando si esegue la stored procedure da SQL Server mediante T-SQL.

> [!NOTE]
> La funzione *executeStoredProcedure* richiede un provider ODBC 3.8, ad esempio ODBC Driver 13 for SQL Server.  

## <a name="see-also"></a>Vedere anche

[Come creare una stored procedure con sqlrutils](how-to-create-a-stored-procedure-using-sqlrutils.md)

