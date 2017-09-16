---
title: Modificare le icone degli indicatori e i set di indicatori (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7e9b0deb3a240607b3df2612622803d62749f521
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a>Modificare le icone degli indicatori e dei set di indicatori (Generatore report e SSRS)
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vengono forniti set di indicatori preconfigurati per report impaginati che potrebbero non raffigurare sempre i dati in maniera efficace né funzionare bene nel report recapitato. In questo argomento vengono illustrate le procedure per modificare l'aspetto delle icone degli indicatori e i set di indicatori in modo da includere differenti icone degli indicatori o per aumentarne o ridurne il numero.  
  
 Opzioni come i colori possono essere impostate tramite espressioni. Per altre informazioni, vedere [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
## <a name="to-change-the-color-of-an-indicator-icon"></a>Per modificare il colore di un'icona dell'indicatore  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da modificare e scegliere **Proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Fare clic sulla freccia in giù nella colonna **Colore** accanto all'icona che si desidera modificare e scegliere il colore da usare, **Nessun colore**o **Altri colori**.  
  
     Se lo si desidera, fare clic sul pulsante **Espressione** (*fx*) per modificare un'espressione che imposta il valore dell'opzione **Colore** .  
  
     Se è stato selezionato **Altri colori**, viene visualizzata la finestra di dialogo **Seleziona colore** in cui è possibile scegliere da un'ampia matrice di colori. Per altre informazioni sulle opzioni, vedere [Finestra di dialogo Seleziona colore &#40;Generatore report e SSRS&#41;](http://msdn.microsoft.com/library/ac7089a3-5c7b-4f53-8348-180610e86da2). Fare clic su **OK** per chiudere la finestra di dialogo **Seleziona colore**.  
  
4.  Scegliere **OK**.  
  
## <a name="to-change-the-icon"></a>Per modificare l'icona  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da modificare e scegliere **Proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Fare clic sulla freccia in giù accanto all'icona che si desidera cambiare e selezionarne una diversa.  
  
     Se lo si desidera, fare clic sul pulsante **Espressione** (*fx*) per modificare un'espressione che consente di impostare il valore dell'opzione **Icona** .  
  
4.  Scegliere **OK**.  
  
## <a name="to-use-a-custom-image-as-an-indicator-icon"></a>Per utilizzare un'immagine personalizzata come icona dell'indicatore  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da modificare e scegliere **Proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Fare clic sulla freccia in giù accanto all'icona che si desidera cambiare e selezionare **Immagine**.  
  
4.  Nell'elenco **Selezionare l'origine dell'immagine** scegliere **Esterno**, **Incorporato**o **Database**.  
  
5.  In base all'origine dell'immagine, eseguire una delle operazioni seguenti:  
  
    -   Per usare un'immagine archiviata all'esterno del report, fare clic su **Sfoglia** e individuare l'immagine. Nel report verrà incluso un riferimento all'immagine.  
  
    -   Per usare un'immagine incorporata nel report, fare clic su **Importa** e individuare l'immagine. L'immagine sarà aggiunta alla definizione del report e salvata insieme a quest'ultima.  
  
    -   Per usare un'immagine presente in un database, nell'elenco **Utilizza questo campo** . selezionare il campo dall'elenco, quindi nell'elenco **Utilizza questo tipo MIME** selezionare il tipo MIME dell'immagine.  
  
6.  Scegliere **OK**.  
  
## <a name="to-add-an-icon-to-the-indicator-set"></a>Per aggiungere un'icona al set di indicatori  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da modificare e scegliere **Proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Scegliere **Aggiungi**. Viene aggiunto un indicatore per cui vengono usati l'icona predefinita e l'opzione **Nessun colore** .  
  
     Configurare l'indicatore in modo da utilizzare l'icona e il colore desiderati. Nelle procedure riportate in precedenza in questo argomento vengono illustrati i passaggi che consentono di effettuare queste operazioni.  
  
4.  Scegliere **OK**.  
  
## <a name="to-delete-an-icon-to-the-indicator-set"></a>Per eliminare un'icona dal set di indicatori  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da modificare e scegliere **Proprietà indicatore**.  
  
2.  Scegliere **Valori e stati** dal riquadro sinistro.  
  
3.  Selezionare l'icona da eliminare e scegliere **Elimina**.  
  
4.  Scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Indicatori &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  