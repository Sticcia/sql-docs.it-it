---
title: 'Passaggio 4: Testare il pacchetto della lezione 5 | Microsoft Docs'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fc67c0a145b1ec32dc14cae8d56e538f14c2808e
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65721547"
---
# <a name="lesson-5-4-test-the-lesson-5-package"></a>Lezione 5-4: Testare il pacchetto della lezione 5

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In fase di esecuzione il pacchetto ottiene il valore della proprietà **Directory** da una variabile di configurazione anziché dal nome della directory specificato quando è stato creato il pacchetto. Il valore della variabile proviene dal file **SSISTutorial.dtsConfig**.  
  
Per verificare se il pacchetto aggiorna la proprietà **Directory** con il nuovo valore in fase di esecuzione, eseguire il pacchetto. Poiché nella nuova directory sono presenti solo tre file di dati di esempio, il flusso di dati viene eseguito solo tre volte.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
Prima di testare il pacchetto, verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 5 siano simili agli oggetti visualizzati nelle figure seguenti:  
  
**Flusso di controllo**  
  
![Flusso di controllo nel pacchetto](../integration-services/media/task4lesson2control.gif "Flusso di controllo nel pacchetto")  
  
**Flusso di dati**  
  
![Flusso di dati nel pacchetto](../integration-services/media/task9lesson1data.gif "Flusso di dati nel pacchetto")  
  
## <a name="test-the-lesson-5-package"></a>Testare il pacchetto della lezione 5  
  
1.  Selezionare **Avvia debug** dal menu **Debug**.  
  
2.  Al termine dell'esecuzione del pacchetto, selezionare **Arresta debug** dal menu **Debug**.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 6: Usare parametri con il modello di distribuzione del progetto in SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
  
