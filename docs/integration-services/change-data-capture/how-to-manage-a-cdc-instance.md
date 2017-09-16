---
title: Come gestire un'istanza di CDC | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d368fcacfb8e548647785c8b5f6ef5b73b4ef10b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="how-to-manage-a-cdc-instance"></a>Procedura di gestione di un'istanza di CDC
  In questa procedura viene illustrato come utilizzare CDC Designer Console per gestire le operazioni dell'istanza di CDC al runtime.  
  
### <a name="to-manage-cdc-instance-operations"></a>Per gestire le operazioni dell'istanza di CDC  
  
1.  Scegliere **CDC Designer Console** dal menu **Start**.  
  
2.  Nel riquadro sinistro espandere **Change Data Capture** , quindi espandere il servizio che contiene l'istanza che si desidera visualizzare.  
  
3.  Selezionare il nome di un'istanza che si desidera utilizzare.  
  
4.  Nel riquadro **Actions** sul lato destro di CDC Designer Console, fare clic sull'operazione che si desidera eseguire.  
  
     È anche possibile fare clic con il pulsante destro del mouse sul nome dell'istanza nel riquadro sinistro e selezionare l'operazione che si desidera eseguire.  
  
     È possibile eseguire le attività seguenti:  
  
    -   **Start**: avvio dell'acquisizione delle modifiche.  
  
    -   **Stop**: arresto dell'acquisizione delle modifiche  
  
    -   **Reset**: fare clic su **Reset** per reimpostare l'istanza di CDC sullo stato iniziale (vuoto). Questa opzione diventa disponibile dopo che l'istanza di CDC è stata interrotta. Tutte le modifiche presenti nelle tabelle delle modifiche e lo stato interno dell'istanza di CDC vengono eliminati. Al successivo avvio dell'istanza di CDC, l'acquisizione delle modifiche verrà avviata da quel momento e includerà solo le transazioni avviate dopo l'avvio dell'istanza di CDC.  
  
    -   **Delete**: eliminazione dell'istanza di CDC.  
  
    -   **Oracle Logging Script**: fare clic su **Oracle Logging Script** per visualizzare la finestra di dialogo Oracle Logging Script contenente lo script della registrazione supplementare Oracle. Per informazioni sulle operazioni che è possibile eseguire in questa finestra di dialogo, vedere [Oracle Supplemental Logging Script](../../integration-services/change-data-capture/oracle-supplemental-logging-script.md).  
  
         **Nota**: quando si eseguono gli script di registrazione supplementare, viene visualizzata la finestra di dialogo Oracle Credentials for Running Script in cui immettere un nome utente e una password Oracle validi. Per informazioni su come fornire le credenziali Oracle appropriate, vedere [Oracle Credentials for Running Script](../../integration-services/change-data-capture/oracle-credentials-for-running-script.md).  
  
    -   **CDC Instance Deployment**: generazione di uno script di distribuzione per l'istanza di CDC. Per informazioni su questa finestra di dialogo, vedere [CDC Instance Deployment Script](../../integration-services/change-data-capture/cdc-instance-deployment-script.md).  
  
     Per ulteriori informazioni su queste attività, vedere [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
 È inoltre possibile selezionare **Properties** per modificare le proprietà di configurazione dell'istanza di CDC. Per ulteriori informazioni sulla modifica delle proprietà dell'istanza di CDC, vedere [Edit Instance Properties](../../integration-services/change-data-capture/edit-instance-properties.md).  
  
  