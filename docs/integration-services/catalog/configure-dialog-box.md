---
title: Finestra di dialogo Configura | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.configure.f1
- sql13.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql13.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dbf1fba077d693b45cd20c0e9f683cda64bc03dd
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65729217"
---
# <a name="configure-dialog-box"></a>Finestra di dialogo Configura

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Utilizzare la finestra di dialogo **Configura** per configurare i parametri, le gestioni connessioni e i riferimenti agli ambienti per pacchetti e progetti.  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Configura](#open_dialog)  
  
-   [Impostare le opzioni nella pagina Parametri](#parameter)  
  
-   [Impostare le opzioni nella pagina Riferimenti](#references)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Configura  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Verrà eseguita la connessione all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database SSISDB.  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **SSISDB** .  
  
4.  Espandere la cartella contenente il pacchetto o il progetto che si desidera configurare.  
  
5.  Fare clic con il pulsante destro del mouse sul pacchetto o sul progetto, quindi scegliere **Configura**.  
  
##  <a name="parameter"></a> Impostare le opzioni nella pagina Parametri  
 Utilizzare la pagina **Parametri** per visualizzare i nomi dei parametri e i valori e per modificare i valori.  
  
 Selezionare l'ambito dei parametri visualizzato nelle schede **Parametri** e **Gestioni connessioni** nell'elenco a discesa **Ambito** .  
  
 Di seguito sono riportate le opzioni della scheda **Parametri** .  
  
 **Contenitore**  
 Viene elencato l'oggetto contenente il parametro.  
  
 **Nome**  
 Viene elencato il nome del parametro.  
  
 **Valore**  
 Viene elencato il valore del parametro. Fare clic sul pulsante con i puntini di sospensione per modificare il valore nella finestra di dialogo **Imposta valore parametro** .  
  
 Di seguito sono riportate le opzioni della scheda **Gestioni connessioni** . Utilizzare questa scheda per modificare i valori per le proprietà di gestione connessione. I parametri vengono automaticamente generati nel server SSIS per le proprietà.  
  
 **Contenitore**  
 Viene elencato l'oggetto contenente la gestione connessione.  
  
 **Nome**  
 Viene elencato il nome della gestione connessione.  
  
 **Nome proprietà**  
 Viene elencato il nome della proprietà della gestione connessione.  
  
 **Value**  
 Viene elencato il valore assegnato alla proprietà della gestione connessione. Fare clic sul pulsante con i puntini di sospensione per modificare il valore nella finestra di dialogo **Imposta valore parametro** . È possibile immettere un valore letterale, eseguire il mapping di una variabile di ambiente contenente il valore da utilizzare oppure utilizzare il valore predefinito dal pacchetto.  
  
##  <a name="references"></a> Impostare le opzioni nella pagina Riferimenti  
 Utilizzare la pagina **Riferimenti** per aggiungere e rimuovere i riferimenti agli ambienti e accedere alle proprietà dell'ambiente.  
  
 Un ambiente specifica i valori di runtime per i pacchetti contenuti nei progetti distribuiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 **Ambiente**  
 Elenca l'ambiente  
  
 **Cartella ambiente**  
 Elenca la cartella in cui è contenuto l'ambiente.  
  
 **Aprire**  
 Fare clic per aprire la finestra di dialogo **Proprietà ambiente** .  
  
 **Aggiungi**  
 Fare clic per aggiungere un riferimento a un ambiente. Nella finestra di dialogo **Sfoglia ambienti** fare clic su un ambiente, quindi fare clic su **OK**.  
  
 È possibile selezionare un ambiente contenuto in qualsiasi cartella del progetto nel nodo **SSISDB** .  
  
 **Rimuovi**  
 Fare clic su un ambiente elencato nell'area **Riferimenti** e quindi fare clic su **Rimuovi**.  
  
  
