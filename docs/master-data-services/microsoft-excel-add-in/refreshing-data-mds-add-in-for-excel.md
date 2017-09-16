---
title: Aggiornamento dei dati (componente aggiuntivo MDS per Excel) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58dbe99a-288d-4f1c-9cd5-704d6836c945
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6159c4b30b0cd2c4f718efaddc7c915f1fb43dfd
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="refreshing-data-mds-add-in-for-excel"></a>Aggiornamento dei dati (Componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], aggiornare i dati quando si desidera ottenere le informazioni più recenti dal repository MDS senza aprire un nuovo foglio di lavoro. È possibile aggiornare tutte le celle o una selezione di celle. Questo può essere utile quando sono state inserite colonne con formule personalizzate o altri dati che non sono gestiti in MDS e che si desidera mantenere.  
  
## <a name="when-you-can-refresh-mds-managed-data"></a>Quando è possibile aggiornare i dati gestiti da MDS  
 È possibile aggiornare i dati gestiti da MDS in un foglio di lavoro attivo se il foglio di lavoro attivo già contiene i dati gestiti da MDS. Se sono stati modificati valori di attributo o aggiunti membri al foglio di lavoro, è necessario pubblicare le modifiche prima di eseguire l'aggiornamento.  
  
## <a name="refreshing-a-selection"></a>Aggiornamento di una selezione  
 È possibile aggiornare tutte le celle o solo le celle selezionate. Le celle selezionate devono essere contigue. Se viene selezionato un set di celle contigue, tutte le celle gestite da MDS nel set verranno aggiornate per visualizzare i valori attualmente archiviati nel server. L'operazione non ha alcun effetto su righe e colonne non modificate che non sono gestite da MDS.  
  
## <a name="what-happens-when-you-refresh-mds-managed-data"></a>Cosa accade quando si aggiornano i dati gestiti da MDS  
 Quando si aggiornano dati in [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], ciò che accade ai dati gestiti da MDS nel foglio dipende da quale modifica è stata apportata nel repository MDS dall'ultimo caricamento dei dati.  
  
-   Se i nuovi membri sono stati aggiunti al repository, vengono aggiunti alla fine del foglio di lavoro e sono evidenziati in verde.  
  
-   Se i membri sono eliminati dal repository, vengono eliminati dal foglio di lavoro.  
  
-   Se un valore dell'attributo è stato modificato nel repository MDS, il valore nel foglio di lavoro viene aggiornato con il valore presente nel repository MDS. Il colore della cella non viene modificato.  
  
> [!WARNING]  
>  -   Nel foglio di lavoro attivo, se esistono dati non gestiti nelle righe al di sotto dei dati gestiti da MDS, è possibile che i dati non gestiti vengano sovrascritti. Ciò si verifica quando si aggiorna il foglio e vengono aggiunte nuove righe dei dati gestiti da MDS, che si sovrappongono ai dati non gestiti.  
> -   Quando si effettua l'aggiornamento, vengono eliminati i commenti sulle celle gestite da MDS.  
  
## <a name="how-to-refresh-mds-managed-data"></a>Come aggiornare i dati gestiti da MDS  
 Nel gruppo **Connetti e carica** sulla barra multifunzione il pulsante **Aggiorna** ha due opzioni **Aggiorna tutto** e **Aggiorna selezione**. L'azione predefinita del pulsante della barra multifunzione è **Aggiorna tutto**. Per aggiornare l'intero foglio con i valori dal server, fare clic sul pulsante **Aggiorna** o scegliere l'opzione **Aggiorna tutto** . Per aggiornare solo alcune delle celle in un foglio, selezionare le celle eseguendo una selezione contigua e scegliere l'opzione **Aggiorna selezione** .  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare una connessione a un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].|[Connettersi a un repository MDS &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Caricare dati MDS in Excel.|[Esportare dati in Excel da Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Connessioni &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Panoramica: Esportazione dei dati in Excel &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Componente aggiuntivo Master Data Services per Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  