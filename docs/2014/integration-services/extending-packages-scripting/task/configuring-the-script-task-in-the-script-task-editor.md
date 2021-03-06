---
title: Configurazione dell'attività Script nell'editor attività Script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8e9e1ebbf8a6ba8186d30063bd377f95b8e286d9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894745"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>Configurazione dell'attività Script nell'editor attività Script
  Prima di scrivere codice personalizzato nell'attività Script, configurarne le principali proprietà nelle tre pagine di **Editor attività Script**. È possibile configurare proprietà di attività aggiuntive che non sono specifiche dell'attività Script utilizzando la finestra Proprietà.  
  
> [!NOTE]  
>  A differenza delle versioni precedenti in cui era possibile indicare se gli script erano precompilati o meno, a partire da [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] tutti gli script sono precompilati.  
  
## <a name="general-page-of-the-script-task-editor"></a>Pagina Generale dell'editor attività Script  
 Nella pagina **Generale** di **Editor attività Script** è possibile assegnare un nome univoco e una descrizione per l'attività Script.  
  
## <a name="script-page-of-the-script-task-editor"></a>Pagina Script dell'editor attività Script  
 Nella pagina **Script** di **Editor attività Script** vengono visualizzate le proprietà personalizzate dell'attività Script.  
  
### <a name="scriptlanguage-property"></a>Proprietà ScriptLanguage  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supporta i linguaggi di programmazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Dopo aver creato uno script nell'attività Script, non è possibile modificare il valore della proprietà **ScriptLanguage**.  
  
 Per impostare il linguaggio di scripting predefinito per le attività Script e i componenti script, usare la proprietà **ScriptLanguage** nella pagina **Generale** della finestra di dialogo **Opzioni**. Per ulteriori informazioni, vedere [General Page](../../general-page-of-integration-services-designers-options.md).  
  
### <a name="entrypoint-property"></a>Proprietà EntryPoint  
 La proprietà `EntryPoint` specifica il metodo nella classe `ScriptMain` nel progetto VSTA chiamato dal runtime di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] come punto di ingresso nel codice dell'attività Script. La classe `ScriptMain` è la classe predefinita generata dai modelli di script.  
  
 Se si modifica il nome del metodo nel progetto VSTA, è necessario modificare il valore della proprietà `EntryPoint`.  
  
### <a name="readonlyvariables-and-readwritevariables-properties"></a>Proprietà ReadOnlyVariables e ReadWriteVariables  
 È possibile immettere elenchi delimitati da virgole di variabili esistenti come valori di queste proprietà per rendere le variabili disponibili per l'accesso di sola lettura o di lettura/scrittura all'interno del codice dell'attività Script. Le variabili di entrambi i tipi sono accessibili nel codice tramite la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> dell'oggetto `Dts`. Per altre informazioni, vedere [Utilizzo di variabili nell'attività Script](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).  
  
> [!NOTE]  
>  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
 Per selezionare le variabili, fare clic sui puntini di sospensione (**...**) accanto al campo della proprietà. Per altre informazioni, vedere [Pagina Seleziona variabili](../../control-flow/select-variables-page.md).  
  
### <a name="edit-script-button"></a>Pulsante Modifica script  
 Il pulsante **Modifica script** avvia l'ambiente di sviluppo di VSTA in cui scrivere lo script personalizzato. Per altre informazioni, vedere [Scrittura di codice e debug dell'attività Script](coding-and-debugging-the-script-task.md).  
  
## <a name="expressions-page-of-the-script-task-editor"></a>Pagina Espressioni dell'editor attività Script  
 Nella pagina **Espressioni** di **Editor attività Script** è possibile usare espressioni per fornire valori per le proprietà dell'attività Script descritte in precedenza e per molte altre proprietà di attività. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md).  
  
![Icona di Integration Services (piccola)](../../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services**<br /> Per i download, gli articoli, gli esempi e i video [!INCLUDE[msCoName](../../../includes/msconame-md.md)] più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] su MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di codice e debug dell'attività Script](coding-and-debugging-the-script-task.md)  
  
  
