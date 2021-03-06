---
title: Impostazioni (migrazione) (DB2ToSQL) del progetto | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4fe3619ae24f8dbee774aef95abc37ad57ca6e19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63266533"
---
# <a name="project-settings-migration-db2tosql"></a>Impostazioni progetto (migrazione) (DB2ToSQL)
La pagina di migrazione del **impostazioni del progetto** finestra di dialogo contiene impostazioni che consentono di personalizzare la modalità SSMA viene eseguita la migrazione dei dati da DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Il riquadro di migrazione è disponibile in entrambe la **impostazioni del progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **Versione di destinazione della migrazione** elenco a discesa fare clic su **generali** nella parte inferiore del riquadro a sinistra e quindi fare clic su **migrazione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **le impostazioni del progetto**, fare clic su **generale** nella parte inferiore del riquadro di sinistra e quindi fare clic su **Migrazione**.  
  
## <a name="migration-engine"></a>Modulo di migrazione  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modulo di migrazione**|Specifica il motore di database utilizzato durante la migrazione dei dati. Migrazione dei dati lato client fa riferimento al client SSMA recupero dei dati dall'origine e inserimento bulk che i dati in SQL Server. Migrazione dei dati lato server fa riferimento al motore di migrazione di dati SSMA (programma di copia bulk) in esecuzione nella finestra di SQL Server come un processo SQL Agent, il recupero dei dati dall'origine e inserimento direttamente in SQL Server, evitando in tal modo un ulteriore client-hop (prestazioni).<br /><br />**Modalità predefinita**:  Modulo di migrazione dei dati lato client<br /><br />**La modalità ottimistico**:  Modulo di migrazione dei dati lato client<br /><br />**Modalità intero**:  Modulo di migrazione dei dati lato client|  
  
> [!IMPORTANT]  
> Quando la **modulo di migrazione** opzione è impostata su **modulo di migrazione dei dati lato Server**, un nuovo progetto, impostare l'opzione **modulo di migrazione dei dati lato Server utilizzare 32 Bit** viene visualizzato . Specifica se l'utilità di Strumentazione gestione Windows (BCP, Bulk Copy Program) a 32 bit o a 64 bit viene utilizzato per la migrazione dei dati.  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
  
|Nome|Definizione|  
|--------|--------------|  
|**Dimensioni del batch**|Specifica il batch di dimensioni usate durante la migrazione dei dati.<br /><br />**Modalità predefinita**:  10000<br /><br />**La modalità ottimistico**:  10000<br /><br />**Modalità intero**:  10000|  
|**Vincoli CHECK**|Specifica se SSMA deve verificare i vincoli durante l'inserimento dei dati in tabelle SQL Server.<br /><br />**Modalità predefinita**:  False<br /><br />**La modalità ottimistico**:  False<br /><br />**Modalità intero**:  False|  
|**Timeout di migrazione dati**|Specifica il timeout utilizzato durante la migrazione dei dati<br /><br />**Modalità predefinita**:  15<br /><br />**La modalità ottimistico**:  15<br /><br />**Modalità intero**:  15|  
|**Opzioni di migrazione dati estesi**|Mostra le opzioni di migrazione dati aggiuntivi per ogni tabella nella scheda Dettagli separato.<br /><br />**Modalità predefinita**:  Nascondi<br /><br />**La modalità ottimistico**:  Nascondi<br /><br />**Modalità intero**:  Nascondi|  
|**Attive trigger**|Specifica se SSMA deve attivare i trigger di inserimento quando aggiunge dati alle tabelle di SQL Server.<br /><br />**Modalità predefinita**:  False<br /><br />**La modalità ottimistico**:  False<br /><br />**Modalità intero**:  False|  
|**Mantieni valori Identity**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati in SQL Server, indipendentemente dai valori predefiniti che vengono specificati in SQL Server.<br /><br />**Modalità predefinita**:  True<br /><br />**La modalità ottimistico**:  True<br /><br />**Modalità intero**:  False|  
|**Mantieni valori Null**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati in SQL Server, indipendentemente dai valori predefiniti che vengono specificati in SQL Server.<br /><br />**Modalità predefinita**:  True<br /><br />**La modalità ottimistico**:  True<br /><br />**Modalità intero**:  True|  
|**Contrassegnare l'operazione di taglio di stringa con errore**|Se le dimensioni di colonna di destinazione sono minore della lunghezza di stringa di origine, il valore verrà tagliato e contrassegnato come errore.<br /><br />**Modalità predefinita**:  Yes<br /><br />**La modalità ottimistico**:  Yes<br /><br />**Modalità intero**:  Yes|  
|**In caso di errore**|Interrompe la migrazione dei dati quando si verifica un errore. Sono disponibili tre opzioni:<br /><br />**Interrompere la migrazione:** Operazione di migrazione dei dati viene arrestata<br /><br />**Passare alla tabella riportata di seguito:** Interrompe la migrazione dei dati alla tabella corrente e procede a quella successiva<br /><br />**Procedere al batch successivo:** Interrompe la migrazione dei dati per il batch corrente e procede a quella successiva<br /><br />**Modalità predefinita**: Passare al batch successivo<br /><br />**La modalità ottimistico**: Passare al batch successivo<br /><br />**Modalità intero**: Passare al batch successivo|  
|**Sostituire le date non supportate**|Specifica se SSMA necessario correggere date precedenti a non appena possibile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** data (01 gennaio 1753).<br /><br />Per mantenere i valori di data corrente, selezionare **non eseguono alcuna operazione**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non accetta le date precedenti 01 gennaio 1753 in una colonna datetime. Se si usano le date precedenti, è necessario convertire i valori datetime ai valori di carattere.<br /><br />Per convertire le date precedenti 01 gennaio 1753 su NULL, selezionare **sostituire con un valore NULL**.<br /><br />Per sostituire le date precedenti 01 gennaio 1753 con una data supportata, selezionare **sostituire con più vicino data supportati**.<br /><br />**Modalità predefinita**: Non eseguire alcuna operazione<br /><br />**La modalità ottimistico**: Non eseguire alcuna operazione<br /><br />**Modalità intero**: Sostituire con più vicino data supportati|  
|**Blocco a livello di tabella**|Specifica se SSMA consente di bloccare le tabelle durante l'aggiunta di dati alle tabelle durante la migrazione dei dati. Ottiene un blocco di aggiornamento bulk per la durata dell'operazione di copia bulk. Se il valore è False, viene impostato un blocco a livello di riga.<br /><br />**Modalità predefinita**:  True<br /><br />**La modalità ottimistico**:  True<br /><br />**Modalità intero**:  True|  
  
## <a name="parallel-data-migration"></a>Migrazione parallela dei dati  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modalità di migrazione dati paralleli**|Specifica la modalità usata per i thread fork per abilitare la migrazione di dati paralleli. In modalità Auto, SSMA sceglie il numero di thread (10 per impostazione predefinita) duplicato per la migrazione dei dati. Nella modalità personalizzata, utente può specificare il numero di thread forked per eseguire la migrazione dei dati (valore minimo è 1 e valore massimo è 100). Modulo di migrazione client solo i dati sul lato supporta attualmente la migrazione dei dati parallelo.<br /><br />**Modalità predefinita**:  Auto<br /><br />**La modalità ottimistico**:  Auto<br /><br />**Modalità intero**:  Auto|  
  
> [!IMPORTANT]  
> Quando il **paralleli in modalità di migrazione dati** opzione è impostata su **Custom**, un nuovo progetto, impostare l'opzione **conteggio dei Thread** viene visualizzato. Numero di thread usati per la migrazione dei dati specifica.  
  
