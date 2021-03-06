---
title: Estrarre, pubblicare e registrare file con estensione dacpac | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.DacTableChooser
- sql.data.tools.DacPublishDialog
- sql.data.tools.DacPropertiesDialog
- sql.data.tools.publishdacproject
- sql.data.tools.DacExtractDialog
ms.assetid: ed900f93-d3df-40f5-8e62-4d722595e041
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 21b22c1c3f26112cf6232eb314eeb8f8c330ee03
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090135"
---
# <a name="extract-publish-and-register-dacpac-files"></a>Estrarre, pubblicare e registrare file con estensione dacpac
Questo argomento descrive quattro procedure eseguibili facendo clic con il pulsante destro del mouse su un database connesso in Esplora oggetti di SQL Server:  
  
-   Pubblicare l'applicazione livello dati  
  
-   Estrarre l'applicazione livello dati  
  
-   Registrare l'applicazione livello dati  
  
-   Annullare la registrazione dell'applicazione livello dati  
  
## <a name="publish-data-tier-application"></a>Pubblicare l'applicazione livello dati  
È possibile pubblicare un file con estensione dacpac in un database. Tramite l'azione di pubblicazione viene aggiornato in modo incrementale uno schema del database affinché corrisponda allo schema di un file di origine con estensione dacpac. Se il database non esiste nel server, viene creato durante l'operazione di pubblicazione.  
  
Questa azione è disponibile anche selezionando il nodo Database.  
  
Selezionare il file con estensione dacpac. Dopo aver specificato un file con estensione dacpac, viene abilitato il pulsante **Proprietà DAC**. Nella finestra di dialogo **Proprietà DAC** vengono visualizzate le informazioni sul file con estensione dacpac.  
  
Specificare la stringa di connessione al server di database e, successivamente, il nome del database, se non incluso nella stringa di connessione.  
  
A questo punto i pulsanti **Pubblica** e **Genera script** sono abilitati. Se viene generato uno script, questo viene visualizzato in una finestra del documento e può essere salvato in base alle esigenze. Se si sceglie di pubblicare direttamente nel database, è possibile visualizzare un riepilogo dell'aggiornamento e dello script effettivo dalla finestra **Operazioni con strumenti dati**.  
  
Se è selezionata la casella di controllo **Registra come applicazione livello dati**, viene eseguita la registrazione del database risultante come applicazione livello dati nei metadati del server. Se il database in cui si sta eseguendo la pubblicazione viene registrato, è possibile che l'operazione di pubblicazione non venga completata se lo schema del database è diverso dal relativo file dacpac corrente registrato.  
  
La configurazione di pubblicazione aggiuntiva è disponibile nella finestra di dialogo **Impostazioni di pubblicazione avanzate** a cui è possibile accedere facendo clic sul pulsante **Avanzate**.  
  
## <a name="extract-data-tier-application"></a>Estrarre l'applicazione livello dati  
È possibile estrarre un file con estensione dacpac da un database. Tramite l'operazione di estrazione viene creato un file di snapshot di database (con estensione dacpac) da un database SQL di Azure o SQL Server attivo, che potrebbe contenere dati di tabelle utente, oltre allo schema del database.  
  
Specificare il file con estensione dacpac da creare. Il pulsante **Proprietà DAC** visualizza la finestra di dialogo **Proprietà DAC** che consente di specificare le proprietà del file con estensione dacpac.  
  
Modificare, in base alle esigenze, la configurazione del processo di estrazione. Nella sezione **Impostazioni di estrazione** è possibile scegliere di eseguire solo l'estrazione dello schema oppure, oltre a questa operazione, di includere anche i dati della tabella. Se si sceglie di estrarre lo schema e i dati, è possibile selezionare le tabelle per le quali si desidera eseguire l'estrazione dei dati.  
  
## <a name="register-data-tier-application"></a>Registrare l'applicazione livello dati  
È possibile registrare un database come applicazione livello dati (DAC) nell'istanza. In questo modo viene archiviata una rappresentazione dello stato corrente dello schema del database nei metadati di sistema.  
  
Nella finestra di dialogo **Registra applicazione livello dati** specificare le proprietà dell'applicazione livello dati registrata.  
  
## <a name="unregister-data-tier-application"></a>Annullare la registrazione dell'applicazione livello dati  
Tramite l'annullamento della registrazione è possibile rimuovere i metadata di un'applicazione livello dati registrata dall'istanza. L'annullamento della registrazione non comporta l'eliminazione del database registrato.  
  
## <a name="see-also"></a>Vedere anche  
[Sviluppo del database connesso](../ssdt/connected-database-development.md)  
  
