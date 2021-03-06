---
title: Creare un'entità (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 686c3f487207a430136feac2588e4b4b2dda9b1f
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476995"
---
# <a name="create-an-entity-master-data-services"></a>Creare un'entità (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]creare un'entità in cui siano contenuti i membri e i relativi attributi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che sia presente un modello. Per altre informazioni, vedere [Creare un modello &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>Per creare un'entità  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare dalla griglia il modello per cui si vuole creare l'entità e quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** fare clic su **Aggiungi**.  
  
4.  Nella casella **Nome** digitare il nome dell'entità.  
  
5.  Facoltativamente, nel campo **Descrizione** digitare la descrizione dell'entità.  
  
6.  Facoltativamente, nella casella **Nome per le tabelle di staging** digitare un nome per la tabella di staging.  
  
     Se questo campo non viene completato, viene usato il nome entità.  
  
    > [!TIP]  
    >  Usare il nome del modello come parte del nome della tabella di staging, ad esempio *Nomemodello_Nomeentità*. In questo modo risulta più agevole trovare le tabelle nel database. Per altre informazioni sulle tabelle di staging, vedere [Panoramica: Importazione di dati da tabelle &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md).
    > [!TIP]
    > Se si usano i nomi predefiniti per le tabelle di staging, MDS aggiungerà automaticamente gli identificatori (ad esempio, 1, 2) ai nomi delle tabelle di staging, se esiste un'entità con lo stesso nome in un altro modello.
  
7.  Per il campo **Tipo di log delle transazioni** scegliere il tipo di log delle transazioni nell'elenco a discesa.  
  
     Per altre informazioni, vedere [Modificare il tipo di log delle transazioni dell'entità &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
8.  Facoltativo. Selezionare la casella di controllo **Crea valori Code automaticamente** . Per altre informazioni, vedere [Creazione di codice automatica &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md).  
  
9. Facoltativo. Selezionare la casella di controllo **Abilita compressione dei dati** . La compressione di riga è attivata per impostazione predefinita. Per altre informazioni, vedere [Compressione dei dati](../relational-databases/data-compression/data-compression.md).  
  
10. Fare clic su **Salva**.  
  
## <a name="grid-columns"></a>Colonne della griglia  
 Per ogni entità creata, viene aggiunta alla griglia una riga con tredici colonne. Di seguito sono elencate le colonne.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Stato|Stato dell'entità. Quando si fa clic su **Salva** , viene visualizzata l'immagine seguente che indica che l'entità è in fase di aggiornamento.<br /><br /> ![Icona di aggiornamento dello stato](../master-data-services/media/mds-statusicon-updating.png "Icona di aggiornamento dello stato")<br /><br /> Se si verificano errori durante la creazione o la modifica di un'entità, viene visualizzata l'immagine seguente.<br /><br /> ![Icona di errore](../master-data-services/media/mds-statusicon-error.png "Icona di errore")<br /><br /> Se lo stato è OK, viene visualizzata l'immagine seguente.<br /><br /> ![Icona dello stato OK](../master-data-services/media/mds-statusicon-ok.png "Icona dello stato OK")|  
|Nome|Nome dell'entità.|  
|Descrizione|Descrizione dell'entità.|  
|Tabella di gestione temporanea|Nome di prefisso della tabella usata per l'archiviazione dei dati.|  
|Tipo di log delle transazioni|Tipo di log delle transazioni dell'entità.|  
|Creazione di codice automatica|Specifica se è abilitata la creazione automatica di codice.|  
|Compressione dei dati|Specifica se la compressione dei dati è abilitata per l'entità.|  
|Destinazione di sincronizzazione|Specifica se l'entità rappresenta la destinazione di una relazione di sincronizzazione.|  
|Abilitata per le gerarchie|Specifica se l'entità è abilitata per le operazioni con le gerarchie esplicite. Questa colonna mostra Sì se almeno una gerarchia esplicita viene creata per l'entità.|  
|Creato da|Nome utente dell'utente che ha creato l'entità.|  
|Data creazione|Data e ora di creazione dell'entità.|  
|Aggiornato da|Nome utente dell'ultimo utente che ha aggiornato l'entità.|  
|Data aggiornamento|Data e ora dell'ultimo aggiornamento dell'entità.|  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Creare un attributo di file &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Entità &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)   
 [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Modificare un'entità &#40;Master Data Services&#41;](../master-data-services/edit-an-entity-master-data-services.md)   
 [Eliminare un'entità &#40;Master Data Services&#41;](../master-data-services/delete-an-entity-master-data-services.md)  
  
  
