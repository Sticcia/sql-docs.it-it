---
title: "Utilizzare il correttore ortografico DQS | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65e4e53e-2699-4cae-a9e0-fe78547755b5
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Utilizzare il correttore ortografico DQS
  Il correttore ortografico di [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) consente di controllare la sintassi, l'ortografia e la struttura della frase dei valori stringa in un dominio. Il correttore ortografico è una funzionalità autonoma lato client che non viene integrata con i motori lato server e non influisce sui flussi o gli stati correnti. Il correttore ortografico identifica i valori stringa che considera errori potenziali, quindi li contrassegna con una sottolineatura rossa nella stessa posizione in cui vengono apportate le altre modifiche manuali ai valori del dominio. Queste posizioni includono:  
  
-   Pagina **Gestisci valori di dominio** dell'attività **Individuazione informazioni**  
  
-   Il **i valori di dominio** pagina o **relazioni basate su termini** pagina del **Domain Management** attività  
  
-   Pagina **Gestisci e visualizza risultati** dell'attività **Pulizia**  
  
 Il correttore ortografico funziona solo sui singoli domini con tipo di dati stringa. Tutti valori in un singolo dominio con tipo di dati stringa vengono inviati al correttore ortografico per la convalida. Il correttore ortografico non funziona per un dominio composito e non funziona per i domini con tipi di dati diversi da stringa, valori misti (quali lettere e numeri senza spazio), numeri romani, singoli caratteri e valori costituiti solo da lettere maiuscole.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 Per eseguire il correttore ortografico, è necessario avere una Knowledge Base e un dominio aperti nell'attività Individuazione informazioni o Gestione dominio, è necessario che il correttore ortografico sia abilitato per il dominio e nella pagina in cui viene eseguito ed è necessario che sia specificata la proprietà Lingua per il dominio.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per eseguire il correttore ortografico, è necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN.  
  
##  <a name="Enable"></a> Abilitare il correttore ortografico  
  
1.  Per abilitare il correttore ortografico nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], aprire la Knowledge Base nell'attività **Gestione dominio** , selezionare il dominio desiderato e fare clic su **Abilita correttore ortografico** nella pagina **Proprietà dominio** . In **Lingua**selezionare la lingua da utilizzare con il correttore ortografico.  
  
2.  Il correttore ortografico è abilitato nelle proprietà del dominio, viene abilitato nel **Gestisci valori di dominio** pagina, il **i valori di dominio** pagina o **relazioni basate su termini** pagina e **Gestisci e Visualizza risultati** pagina. Per disabilitare il correttore ortografico in queste pagine, fare clic sui **Abilita/Disabilita correttore ortografico** icona. Fare clic sull'icona per modificare lo stato del correttore ortografico nella pagina. Analogamente, se il **Abilita correttore ortografico** proprietà per il dominio è disabilitata, fare clic sui **Abilita/Disabilita correttore ortografico** icona Abilita il correttore ortografico nella pagina. Se si esce dalla pagina e quindi vi si torna, lo stato del pulsante viene determinato di nuovo dalla proprietà del dominio **Abilita correttore ortografico** .  
  
##  <a name="Use"></a> Utilizzare il correttore ortografico  
  
1.  Spostarsi in una delle pagine seguenti:  
  
    -   Pagina **Gestisci valori di dominio** dell'attività **Individuazione informazioni**  
  
    -   Il **i valori di dominio** pagina o **relazioni basate su termini** pagina del **Domain Management** attività  
  
    -   Pagina **Gestisci e visualizza risultati** dell'attività **Pulizia**  
  
2.  Visualizzare i valori appropriati nella tabella **Valore** applicando un filtro o eseguendo una ricerca.  
  
3.  Analizzare le righe nella tabella **Valore** per determinare se un valore nelle colonne **Valore** o **Correggi in** è contrassegnato con una sottolineatura rossa ondulata.  
  
4.  Fare clic con il pulsante destro del mouse su un valore contrassegnato con una sottolineatura rossa. Fare clic su uno dei valori di sostituzione elencati se è preferibile al valore originale.  
  
5.  Se non è preferibile alcun valore tra quelli visualizzati ed è presente un pulsante **Ulteriori suggerimenti** che indica l'esistenza di ulteriori valori, selezionarlo. Scegliere uno dei valori aggiuntivi se è preferibile al valore originale.  
  
6.  Se si desidera aggiungere il valore al dizionario, fare clic su **Aggiungi al dizionario**. La sottolineatura rossa scomparirà dal valore.  
  
##  <a name="FollowUp"></a> Completamento: fasi successive all'utilizzo del correttore ortografico  
 Dopo avere eseguito il correttore ortografico, completare l'attività in cui si trova il dominio per utilizzare le correzioni suggerite dal correttore ortografico. Se il dominio si trova nell'attività di individuazione delle informazioni, gestione del dominio o criteri di corrispondenza, pubblicare la Knowledge Base per rendere disponibili i risultati dell'analisi del correttore ortografico e consentirne l'utilizzo nella Knowledge Base. Per ulteriori informazioni, vedere [eseguire l'individuazione delle informazioni](../data-quality-services/perform-knowledge-discovery.md), [gestione di un dominio](../data-quality-services/managing-a-domain.md), o [creare un criterio di corrispondenza](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="How"></a> Funzionamento del correttore ortografico  
 Il correttore ortografico DQS contrassegna qualsiasi errore potenziale dei valori stringa con una sottolineatura rossa visualizzata per l'intero valore. Se ad esempio "New York" è stato erroneamente digitato come "Neu York", la sottolineatura rossa verrà visualizzata sotto "Neu York" e non solo sotto "Neu". Se si fa clic con il pulsante destro del mouse sul valore, verranno visualizzate le correzioni suggerite per l'intero valore. È inoltre possibile fare clic su **Ulteriori suggerimenti** se sono presenti più di cinque suggerimenti. È possibile scegliere uno dei suggerimenti o aggiungere un valore al dizionario (a livello di account utente) da visualizzare per il valore originale. I valori aggiunti al dizionario sono validi per tutti i domini. La correzione verrà effettuata nel dominio solo se il suggerimento viene specificato esplicitamente. Quando si seleziona un suggerimento dal menu di scelta rapida del correttore ortografico, il tipo di valore diventa (o rimane) in errore. Il suggerimento selezionato verrà aggiunto alla colonna della correzione. Si noti che un valore può contenere **Corretti** come **Tipo** e continuare a essere contrassegnato come errore potenziale dal correttore ortografico.  
  
 I suggerimenti per i valori verranno forniti sia nella colonna **Valore** che nella colonna **Correggi in** della tabella **Valore** . Quando si seleziona un suggerimento nella colonna **Valore** , il tipo di valore viene impostato su **Errori**e il suggerimento viene copiato nella colonna **Correggi in** , come se fosse stato inserito manualmente. Se è presente una correzione esistente, diventa un suggerimento. Quando si seleziona un suggerimento nella colonna **Correggi in** della pagina **Gestisci e visualizza risultati** dell'attività **Pulizia** , il valore attualmente selezionato verrà sostituito con la selezione e il valore attualmente selezionato diventerà un suggerimento. Nel **Gestisci e Visualizza risultati** pagina il **pulizia** attività, viene indicato alcun suggerimento del livello di record (nella griglia inferiore).  
  
  