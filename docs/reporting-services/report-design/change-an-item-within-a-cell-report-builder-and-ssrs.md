---
title: Change an Item Within a Cell (Report Builder and SSRS) (Modificare un elemento in una cella (Generatore report e SSRS)) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cc13f82453349b16e4c9fc00b8f0f083652daa75
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581743"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a>Modificare un elemento in una cella (Generatore report e SSRS)
Nei report impaginati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile sostituire con un nuovo elemento del report solo un elemento non contenitore, ad esempio una casella di testo, una linea o un'immagine. È ad esempio possibile trascinare una tabella in una casella di testo per sostituire quest'ultima con la tabella stessa.  
  
 Se nella cella è incluso un elemento contenitore, ad esempio un rettangolo, un elenco, una tabella o una matrice, il nuovo elemento verrà aggiunto all'elemento contenitore invece di sostituirlo. Per sostituire un elemento contenitore con un nuovo elemento, eliminare il contenitore. L'eliminazione dell'elemento contenitore ne provoca la sostituzione con una casella di testo, che potrà essere sostituita in seguito con un altro elemento.  
  
 Per impostazione predefinita, tutte le celle di un'area dati tabella, matrice o elenco contengono una casella di testo.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-an-item-within-a-cell"></a>Per modificare un elemento all'interno di una cella  
  
-   Nel gruppo **Aree dati** o **Elementi del report** della scheda **Inserisci** fare clic sull'elemento che si desidera aggiungere al report, quindi selezionare il report. L'elemento verrà aggiunto al report.  
  
> [!NOTE]  
>  Quando si trascina un elemento del report immagine in una cella, viene visualizzata la finestra di dialogo **Proprietà immagine** in cui è possibile impostare le proprietà, ad esempio l'origine dell'immagine, prima che l'immagine venga aggiunta alla cella.  
  
## <a name="see-also"></a>Vedere anche  
 [Immagini, caselle di testo, rettangoli e linee &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
