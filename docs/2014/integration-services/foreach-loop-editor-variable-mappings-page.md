---
title: Editor ciclo foreach (pagina mapping variabili) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f2d95909e76c6b5c3665926783fb42ff247d1ba9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894059"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Editor ciclo Foreach (pagina Mapping variabili)
  Utilizzare la pagina **Mapping variabili** della finestra di dialogo **Editor ciclo Foreach** per eseguire il mapping delle variabili al valore della raccolta. Il valore della variabile viene aggiornato con i valori della raccolta in ogni iterazione del ciclo.  
  
 Per informazioni sull'utilizzo del contenitore Ciclo Foreach in un pacchetto di Integration Services, vedere [Foreach Loop Container](control-flow/foreach-loop-container.md) . Per informazioni su come configurarlo, vedere [Configurazione di un contenitore Ciclo Foreach](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 Nell'esercitazione di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per la creazione di un pacchetto ETL semplice è inclusa una lezione in cui vengono descritte le procedure di aggiunta e di configurazione di un ciclo Foreach.  
  
## <a name="options"></a>Opzioni  
 **Variabile**  
 Selezionare una variabile esistente oppure fare clic su \<**Nuova variabile**> per creare una nuova variabile.  
  
> [!NOTE]  
>  Dopo il mapping di una variabile, viene aggiunta automaticamente una nuova riga all'elenco **Variabile**.  
  
 **Argomenti correlati**: [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Aggiungere una variabile](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 Se si utilizza l'enumeratore Foreach Item, specificare l'indice della colonna nel valore della raccolta di cui eseguire il mapping alla variabile. Per altri tipi di enumeratore, l'indice è di sola lettura.  
  
> [!NOTE]  
>  L'indice è in base 0.  
  
 **Argomenti correlati**: [Esecuzione di un ciclo su file e tabelle di Excel usando un contenitore Ciclo Foreach](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Elimina**  
 Selezionare una variabile e quindi fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor ciclo foreach &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor ciclo foreach &#40;pagina della raccolta&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)   
 [Contenitore Ciclo For](control-flow/for-loop-container.md)  
  
  
