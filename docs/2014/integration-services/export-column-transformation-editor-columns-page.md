---
title: Editor trasformazione Esportazione colonna (pagina colonne) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d7682e3c22885b50e1516a8f30cce468852ae2c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898331"
---
# <a name="export-column-transformation-editor-columns-page"></a>Editor trasformazione Esportazione colonna (pagina Colonne)
  Utilizzare la pagina **Colonne** della finestra di dialogo **Editor trasformazione Esportazione colonna** per specificare le colonne nel flusso di dati da estrarre in file. È possibile indicare se la trasformazione Esporta colonna deve accodare i dati a un file oppure sovrascrivere un file esistente.  
  
 Per ulteriori informazioni sulla trasformazione Esportazione colonna, vedere [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonna estrazione**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti dati di tipo text o image. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Colonna percorso file**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti nomi e percorsi di file. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Consenti accodamento**  
 Consente di indicare se la trasformazione accoderà i dati ai file esistenti. Il valore predefinito è `false`.  
  
 **Forza troncamento**  
 Consente di indicare se la trasformazione eliminerà il contenuto di file esistenti prima di scrivere i dati. Il valore predefinito è `false`.  
  
 **Scrivi indicatore ordine byte**  
 Consente di specificare se scrivere un indicatore ordine byte (BOM) nel file. L'indicatore dell'ordine byte viene scritto solo se i dati hanno tipo di dati `DT_NTEXT` o DT_WSTR e non sono accodati a un file di dati esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Esportazione colonna &#40;pagina Output degli errori&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
