---
title: Editor trasformazione script (pagina Script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d03f6d705707683195ad58b8562d2b964955b8e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889311"
---
# <a name="script-transformation-editor-script-page"></a>Editor trasformazione Script (pagina Script)
  Usare la scheda **Script** della finestra di dialogo **Editor trasformazione Script** per specificare uno script e le proprietà correlate.  
  
 Per altre informazioni sul componente Script, vedere [componente Script](data-flow/transformations/script-component.md) e [configurazione del componente Script nell'Editor del componente di Script](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Per una panoramica sulla programmazione del componente Script, vedere [Estensione del flusso di dati con il componente script](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Opzioni  
 **Proprietà**  
 Consente di visualizzare e modificare le proprietà della trasformazione Script. Molte delle proprietà visualizzate sono di sola lettura. È possibile modificare le proprietà seguenti:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Descrizione**|Consente di descrivere gli scopi della trasformazione Script.|  
|**LocaleID**|Consente di stabilire le impostazioni locali per specificare informazioni sul paese/area geografica relative all'ordinamento e alla conversione di data e ora.|  
|**Nome**|Consente di digitare un nome descrittivo per il componente.|  
|**ValidateExternalMetadata**|Consente di specificare se la trasformazione Script convalida i metadati delle colonne in fase di progettazione utilizzando origini dei dati esterne. Il valore `false` consente di ritardare la convalida fino al momento dell'esecuzione.|  
|**ReadOnlyVariables**|Consente di digitare un elenco delimitato da virgole delle variabili per l'accesso di sola lettura da parte della trasformazione Script.<br /><br /> Nota: Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.|  
|**ReadWriteVariables**|Consente di digitare un elenco delimitato da virgole delle variabili per l'accesso di lettura/scrittura da parte della trasformazione Script.<br /><br /> Nota: Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.|  
|**ScriptLanguage**|Selezionare il linguaggio di scripting che deve essere utilizzato dal componente Script.<br /><br /> Per impostare il linguaggio di scripting predefinito per componenti Script e attività Script, usare l'opzione **Linguaggio di scripting** nella pagina **Generale** della finestra di dialogo **Opzioni** . Per ulteriori informazioni, vedere [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Specifica la classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> e l'assembly `Microsoft.SqlServer.TxScript` che supportano l'infrastruttura [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
 **Modifica script**  
 Usare [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) per creare o modificare uno script.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Seleziona tipo componente script](../../2014/integration-services/select-script-component-type.md)   
 [Editor trasformazione Script &#40;pagina Colonne di input&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Editor trasformazione Script &#40;pagina Input e output&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Editor trasformazione Script &#40;pagina Gestioni connessioni&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Ulteriori esempi di componente script](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
