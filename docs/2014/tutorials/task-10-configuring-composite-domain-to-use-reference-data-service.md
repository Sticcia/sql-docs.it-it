---
title: 'Attività 10: Configurazione del dominio composito per utilizzare il servizio dati di riferimento | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 525e0286d8d82f501981c9e936caca581886b9b4
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65481233"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Attività 10: Configurazione del dominio composito per usare il servizio dati di riferimento
  In questa attività si configura il **Address Validation** dominio composito per utilizzare il **Melissa Data - controllo indirizzo** servizio. In fase di esecuzione, durante l'attività di pulizia, tramite DQS i valori del dominio Address Validation vengono passati al servizio per la pulizia. Visualizzare [mappa dominio/dominio composito ai dati di riferimento](https://msdn.microsoft.com/library/hh213030.aspx) per altri dettagli.  
  
1.  Nella pagina principale del **Client DQS**, fare clic su **Suppliers (Domain Management)** sotto **Knowledge Base recenti** per avviare il **Gestione dominio**pagina.  
  
2.  Selezionare il **Address Validation** dominio composito nel **elenco di domini**.  
  
3.  Nel riquadro destro passare al **i dati di riferimento** scheda.  
  
     ![Scheda dati di riferimento](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "scheda dati di riferimento")  
  
4.  Fare clic su **esplorare** pulsante sulla barra degli strumenti.  
  
5.  Nel **catalogo di provider di dati di riferimento Online** finestra di dialogo **casella di controllo** accanto a **Melissa Data - controllo indirizzo**.  
  
     ![Selezione di Melissa Data - controllo indirizzo](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "selezionare Melissa Data - controllo indirizzo")  
  
6.  Nel riquadro di destra, nelle **Schema** sezione, eseguire il mapping **Address Line** dominio per il **Address Line (M)** elemento dello schema utilizzando l'elenco a discesa.  
  
     ![Eseguire il mapping di elementi dello Schema di servizi desktop remoto al dominio](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "mappare l'elemento dello Schema di servizi desktop remoto al dominio")  
  
7.  Fare clic su **Aggiungi voce di Schema (+)** pulsante sulla barra degli strumenti per creare una voce nell'elenco.  
  
     ![Aggiungere pulsante della barra degli strumenti di voce dello Schema](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "aggiungere pulsante della barra degli strumenti di voce dello Schema")  
  
8.  Eseguire il mapping dei domini DQS utilizzando gli elenchi a discesa come illustrato nella figura seguente.  
  
     ![Eseguire il mapping agli elementi dello Schema di servizi desktop remoto ai domini](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "mappare gli elementi dello Schema di servizi desktop remoto ai domini")  
  
9. Scegliere **OK** per chiudere la finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 11: Pubblicazione della Knowledge Base](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
