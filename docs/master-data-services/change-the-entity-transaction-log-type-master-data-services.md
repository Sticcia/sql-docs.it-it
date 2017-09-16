---
title: "Modificare il tipo di log delle transazioni dell'entità (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
caps.latest.revision: 10
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: c3a7d334b324abc757040b36ea6643f5b1836fcc
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>Modificare il tipo di log delle transazioni dell'entità (Master Data Services)
  È possibile modificare il tipo di log delle transazioni di un'entità in attributo, membro o nessuno.  
  
|Tipo di log delle transazioni|Description|  
|--------------------------|-----------------|  
|Attribute|I log di modifica dell'entità vengono salvati al livello di attributo.<br /><br /> Il log delle transazioni viene salvato perché è per [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].|  
|Membro|I log di modifica dell'entità vengono salvati al livello di riga.<br /><br /> Tutte le modifiche dell'attributo attivano una nuova revisione di riga.<br /><br /> Quando si usa il tipo di log delle transazioni di riga, l'entità viene archiviata come dimensione a modifica lenta di tipo 4. Le viste sottoscrizione di tipo 2 e di tipo 4 (cronologia) sono supportate. Per altre informazioni, vedere [Formati di vista sottoscrizioni &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)<br /><br /> Fornisce prestazioni migliori.|  
|Nessuno|Non vengono salvati log di modifica.<br /><br /> Fornisce le prestazioni migliori.|  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessaria l'autorizzazione per accedere all'area funzionale Amministrazione sistema. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Deve essere presente l'entità. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 **Per modificare il tipo di log delle transazioni**  
  
1.  In Gestione dati master fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare la riga per il modello dell'entità da modificare, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga per l'entità da aggiornare, quindi fare clic su **Modifica**.  
  
4.  Scegliere il tipo di log delle transazioni nell'elenco a discesa.  
  
5.  Fare clic su **Salva**.  
  
  