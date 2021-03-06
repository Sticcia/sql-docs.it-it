---
title: Modificare la finestra di dialogo Impostazioni (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e549e9b4121d116adc627c34dad017b85099a825
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62681168"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Cambia impostazioni (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Cambia impostazioni** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] e in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per cambiare le impostazioni mediante le quali viene controllata l'elaborazione degli oggetti elencati nella finestra di dialogo **Elabora** . Per visualizzare la finestra di dialogo **Cambia impostazioni** , è possibile fare clic su **Cambia impostazioni** nella finestra di dialogo **Elabora** .  
  
> [!NOTE]  
>  Le impostazioni specificate in questa finestra di dialogo sostituiscono le impostazioni predefinite ereditate dal database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] relative agli oggetti elencati nella finestra di dialogo **Elabora** .  
  
## <a name="options"></a>Opzioni  
 **Opzioni di elaborazione**  
 Utilizzare questa scheda per modificare le impostazioni relative all'ordine di elaborazione, alla tabella writeback e agli oggetti interessati nell'ambito dell'operazione di elaborazione. Nella scheda sono incluse le opzioni seguenti:  
  
 **Parallel**  
 Fare clic su questa opzione per elaborare gli oggetti in parallelo.  
  
 **Numero massimo attività parallele**  
 Consente di selezionare il numero massimo di attività eseguite in parallelo nell'ambito dell'operazione di elaborazione o di scegliere **Dipendente dal server** per consentire a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di selezionare il numero ottimale di attività parallele.  
  
 **Sequential**  
 Fare clic su questa opzione per elaborare gli oggetti in modo sequenziale.  
  
 **Modalità transazione**  
 Consente di scegliere la modalità di transazione utilizzata quando gli oggetti vengono elaborati in ordine sequenziale.  
  
-   **Una sola transazione** elabora tutti gli oggetti nella medesima transazione.  
  
-   **Transazioni separate** elabora tutti gli oggetti, inclusi quelli dipendenti, in transazioni separate.  
  
> [!NOTE]  
>  Questa opzione è attivata solo se si seleziona **Sequenziale** .  
  
 **Opzione tabella writeback**  
 Selezionare l'opzione utilizzata per gestire una tabella writeback:  
  
-   **Crea** determina la creazione di una tabella writeback nel caso questa non esista Se esiste già una tabella writeback, si verifica un errore.  
  
-   **Crea sempre** crea una tabella writeback nel caso questa non esista oppure sovrascrive quella esistente.  
  
-   **Usa tabella esistente** utilizza la tabella writeback esistente. Se non esiste alcuna tabella writeback, si verifica un errore.  
  
 **Elabora oggetti interessati**  
 Selezionare questa opzione per includere ed elaborare gli oggetti dipendenti da oggetti inclusi nell'operazione di elaborazione.  
  
 **Errori chiave dimensione**  
 Utilizzare questa scheda per modificare le impostazioni relative alla configurazione degli errori per l'operazione di elaborazione. Nella scheda sono incluse le opzioni seguenti:  
  
 **Usa configurazione errori predefinita**  
 Selezionare questa opzione per utilizzare la configurazione errori predefinita per gli oggetti nell'operazione di elaborazione.  
  
 **Usa configurazione errori personalizzata**  
 Selezionare questa opzione per definire la configurazione degli errori relativa agli oggetti inclusi nell'operazione di elaborazione.  
  
 **Azione per errore chiave**  
 Consente di scegliere una delle azioni seguenti da eseguire quando viene rilevata una nuova chiave che non può essere ricercata durante l'elaborazione:  
  
-   **Converti in sconosciuta** aggrega le informazioni relative al record nel membro sconosciuto.  
  
-   **Scarta record** esclude le informazioni relative al record dall'elaborazione dell'oggetto.  
  
 **Ignora conteggio errori**  
 Fare clic su questa opzione per ignorare qualsiasi eventuale errore che si verifichi durante l'elaborazione.  
  
 **Arresta in caso di errore**  
 Fare clic su questa opzione per arrestare l'elaborazione in caso di errori. Questa opzione implica l'attivazione delle impostazioni **Numero di errori** e **Azione in caso di errore** .  
  
 **Numero di errori**  
 Consente di immettere il numero di errori che verranno ignorati prima di arrestare l'elaborazione.  
  
 **Azione in caso di errore**  
 Consente di scegliere una delle azioni seguenti da eseguire se il numero di errori supera il valore impostato in **Numero di errori**:  
  
-   **Arresta elaborazione** termina l'operazione di elaborazione.  
  
-   **Arresta registrazione** arresta la registrazione degli errori senza però interrompere l'elaborazione.  
  
 **Chiave non trovata**  
 Specificare una delle azioni seguenti da eseguire quando non viene trovata una chiave durante l'elaborazione di un oggetto:  
  
-   **Ignora errore** ignora l'errore.  
  
-   **Segnala e continua** segnala l'errore e continua l'operazione di elaborazione.  
  
-   **Segnala e arresta** segnala l'errore e arresta l'operazione di elaborazione.  
  
 **Chiave duplicata**  
 Specificare una delle azioni seguenti da eseguire se viene trovata una chiave duplicata durante l'elaborazione di un oggetto:  
  
-   **Ignora errore** ignora l'errore.  
  
-   **Segnala e continua** segnala l'errore e continua l'operazione di elaborazione.  
  
-   **Segnala e arresta** segnala l'errore e arresta l'operazione di elaborazione.  
  
 **Chiave Null convertita in sconosciuta**  
 Consente di specificare una delle azioni seguenti da eseguire se viene aggiunta una chiave membro Null a un membro sconosciuto durante l'elaborazione di un oggetto.  
  
-   **Ignora errore** ignora l'errore.  
  
-   **Segnala e continua** segnala l'errore e continua l'operazione di elaborazione.  
  
-   **Segnala e arresta** segnala l'errore e arresta l'operazione di elaborazione.  
  
 **Chiave Null non consentita**  
 Consente di specificare una delle azioni seguenti da eseguire se viene individuata una chiave Null non consentita durante l'elaborazione di un oggetto:  
  
-   **Ignora errore** ignora l'errore.  
  
-   **Segnala e continua** segnala l'errore e continua l'operazione di elaborazione.  
  
-   **Segnala e arresta** segnala l'errore e arresta l'operazione di elaborazione.  
  
 **Percorso log degli errori**  
 Consente di digitare il percorso completo e il nome del file di log degli errori.  
  
 **Sfoglia**  
 Fare clic su questo pulsante per visualizzare la finestra di dialogo **Apri** e selezionare il nome e il percorso completo del file di log degli errori.  
  
 **Elabora oggetti interessati**  
 Fare clic su questa opzione per elaborare gli oggetti dipendenti da altri oggetti selezionati nella finestra di dialogo **Elabora** .  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Elaborare la finestra di dialogo &#40;Analysis Services - dati multidimensionali&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
