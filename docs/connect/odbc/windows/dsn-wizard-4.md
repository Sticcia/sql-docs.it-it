---
title: Origine di dati guidata schermata 4 (Driver ODBC per SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c8a5a785f7c208d8543f9ec3a27d34b34f7a918
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724369"
---
# <a name="data-source-wizard-screen-4"></a>Creazione guidata origine dati - Schermata 4

Specificare la lingua da usare per i messaggi di SQL Server, la traduzione dei set di caratteri e se il driver ODBC per SQL Server deve usare impostazioni internazionali. È inoltre possibile controllare la registrazione di query con esecuzione prolungata e le impostazioni delle statistiche del driver.

## <a name="options"></a>Opzioni

### <a name="change-the-language-of-sql-server-system-messages-to"></a>Visualizza i messaggi di sistema di SQL Server in

Ogni istanza di SQL Server può avere più set di messaggi di sistema, con ogni set in una lingua diversa, ad esempio inglese, spagnolo, francese e così via. Se un'origine dati è definita rispetto a un server che dispone di più set di messaggi di sistema, è possibile specificare quale lingua si desidera utilizzare per i messaggi di sistema. Selezionare la lingua desiderata nell'elenco. Questa opzione non è disponibile se in SQL Server è installata una sola lingua.

### <a name="use-strong-encryption-for-data"></a>Usa crittografia avanzata per i dati

Se questa opzione è selezionata, i dati passati tramite connessioni stabilite utilizzando il DSN corrente saranno crittografati. Gli account di accesso sono crittografati per impostazione predefinita, anche se questa casella di controllo è deselezionata.

### <a name="trust-server-certificate"></a>Certificato server attendibile

Questa opzione è applicabile solo quando **Usa crittografia avanzata per i dati** è abilitata. Se selezionata, il certificato del server non verrà convalidato per avere il nome host corretto del server ed essere emesso da un'autorità di certificazione attendibile. 

### <a name="perform-translation-for-character-data"></a>Converti dati caratteri

Se questa casella di controllo è selezionata, il driver ODBC per SQL Server converte le stringhe ANSI inviate tra il computer client e SQL Server tramite Unicode. Il driver ODBC esegue a volte la conversione tra la tabella codici di SQL Server e Unicode nel computer client. A questo scopo, la tabella codici usata da SQL Server deve essere una delle tabelle codici disponibili nel computer client.

Se questa casella di controllo è deselezionata, la conversione dei caratteri estesi in stringhe di caratteri ANSI non viene eseguita quando tali caratteri vengono inviati tra l'applicazione client e il server. Se il computer client usa una tabella codici ANSI diversa dalla tabella codici di SQL Server, i caratteri estesi nelle stringhe di caratteri ANSI potrebbero essere interpretati in modo non corretto. Se il computer client usa la stessa tabella codici per la propria tabella codici ANSI usata da SQL Server, i caratteri estesi vengono interpretati correttamente.

### <a name="use-regional-settings-when-outputting-currency-numbers-dates-and-times"></a>Usa le impostazioni internazionali del sistema per visualizzare simboli di valuta, numeri, data e ora

Indica che il driver utilizza le impostazioni internazionali del computer client per la formattazione di valuta, numeri, date e ore nelle stringhe di caratteri di output. Vengono utilizzate le impostazioni internazionali predefinite per l'account di accesso dell'utente che si connette tramite l'origine dati. Selezionare questa opzione per le applicazioni che effettuano solo la visualizzazione dei dati, non per quelle che consentono di elaborare i dati.

### <a name="save-long-running-queries-to-the-log-file"></a>Salva query a lunga esecuzione nel seguente file di log

Specifica che il driver registra qualsiasi query con durata superiore al valore di **Durata query lunghe**. Le query con esecuzione prolungata sono registrate nel file specificato. Per specificare un file di log, digitare il percorso completo e il nome file nella casella oppure fare clic su **Sfoglia** per selezionare un file di log esplorando le directory di file esistenti.

### <a name="long-query-time-milliseconds"></a>Durata query lunghe (millisecondi)

Indica un valore soglia, espresso in millisecondi, per la registrazione delle query con esecuzione prolungata. Qualsiasi query con una durata superiore a questo numero di millisecondi viene registrata.

### <a name="log-odbc-driver-statistics-to-the-log-file"></a>Salva statistiche del driver ODBC nel seguente file di log

Indica che le statistiche verranno registrate nel file specificato. Per specificare un file di log, digitare il percorso completo e il nome file nella casella oppure fare clic su **Sfoglia** per selezionare un file di log esplorando le directory di file esistenti.

Il log delle statistiche è un file delimitato da tabulazioni che può essere analizzato in Microsoft Excel o in qualsiasi altra applicazione in grado di supportare i file delimitati da tabulazioni.

### <a name="connect-retry-count"></a>Conteggio tentativi di connessione

Specifica il numero di tentativi di un tentativo di connessione non riuscito.

### <a name="connect-retry-interval-seconds"></a>Intervallo tentativi di connessione (secondi)

Specifica il numero di secondi tra ogni tentativo di ripetizione dei tentativi di connessione. Per altre informazioni sul funzionamento di questo oggetto e il **conteggio tentativi di connessione** opzioni, vedere [resilienza della connessione nel Driver ODBC Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).

### <a name="back"></a>Indietro

Fare clic su questo pulsante per tornare alla pagina precedente della procedura guidata.

### <a name="finish"></a>Fine

Se le informazioni specificate in questa schermata sono state complete, è possibile fare clic su **fine**. Il DSN creato con tutti gli attributi specificati su questa e altre schermate della procedura guidata e l'utente ha la possibilità di testare il DSN appena creato.

## <a name="next-steps"></a>Passaggi successivi

[Creazione guidata origine dati - Schermata 3](../../../connect/odbc/windows/dsn-wizard-3.md)
