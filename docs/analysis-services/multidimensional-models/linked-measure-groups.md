---
title: Gruppi di misure collegato | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a18e61e3c59a36fbeea576234e90ce2f54123a9b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023768"
---
# <a name="linked-measure-groups"></a>Gruppi di misure collegati
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Un gruppo di misure collegato si basa su un altro gruppo di misure in un cubo diverso all'interno dello stesso database o in un database di Analysis Services diverso. È possibile usare un gruppo di misure collegato se si desidera riusare un set di misure e i valori di dati corrispondenti in più cubi.  
  
 Microsoft consiglia che i gruppi di misure collegati e originali risiedano in soluzioni eseguite sullo stesso server. È prevista la deprecazione del collegamento a un gruppo di misure in un server remoto nelle versioni future, vedere [Funzionalità di Analysis Services deprecate in SQL Server 2016](../../analysis-services/deprecated-analysis-services-features-in-sql-server-2016.md).  
  
> [!IMPORTANT]  
>  I gruppi di misure collegati sono di sola lettura. Per visualizzare le modifiche più recenti, è necessario eliminare e ricreare tutti i gruppi di misure collegati basati sull'oggetto di origine modificato. Per questo motivo, copiare e incollare gruppi di misure tra progetti è un approccio alternativo da prendere in considerazione qualora siano necessarie modifiche future al gruppo di misure.  
  
## <a name="usage-limitations"></a>Limitazioni all'utilizzo  
 Come indicato in precedenza, un vincolo importante all'utilizzo delle misure collegate è rappresentato dall'impossibilità di personalizzare direttamente una misura collegata. Le modifiche al tipo di dati, al formato, all'associazione dati e alla visibilità nonché all'appartenenza degli elementi nel gruppo di misure stesso, sono tutte modifiche che devono essere apportate nel gruppo di misure originale.  
  
 Sotto il profilo operativo, i gruppi di misure collegati sono identici agli altri gruppi di misure in termini di accesso da parte di applicazioni client, nonché per l'esecuzione di query.  
  
 Quando si esegue una query su un cubo contenente un gruppo di misure collegato, il collegamento viene stabilito e risolto durante la prima sessione di calcolo del cubo di destinazione. A causa di questo comportamento, qualsiasi calcolo archiviato nel gruppo di misure collegato non può essere risolto prima della valutazione della query. In altri termini, le misure e le celle calcolate devono essere ricreate nel cubo di destinazione, anziché essere ereditate dal cubo di origine.  
  
 Nell'elenco seguente vengono riepilogate le limitazioni all'utilizzo.  
  
-   Non è possibile creare un gruppo di misure collegato da un altro gruppo di misure collegato.  
  
-   Non è possibile aggiungere o rimuovere misure in un gruppo di misure collegato. L'appartenenza viene definita solo nel gruppo di misure originale.  
  
-   Nei gruppi di misure collegati non è supportato il writeback.  
  
-   I gruppi di misure collegati non possono essere utilizzati in più relazioni molti-a-molti, soprattutto quando tali relazioni sono in cubi diversi. Questa operazione può generare aggregazioni ambigue. Per altre informazioni, vedere [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](http://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)(Quantità errate per le misure collegate nei cubi che contengono relazioni molti-a-molti).  
  
 Le misure contenute in un gruppo di misure collegato possono essere organizzate direttamente solo lungo dimensioni collegate recuperate dallo stesso database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . È tuttavia possibile usare membri calcolati per correlare le informazioni di gruppi di misure collegati alle altre dimensioni non collegate del cubo, nonché usare una relazione indiretta, ad esempio un riferimento o una relazione molti-a-molti, per correlare dimensioni non collegate a un gruppo di misure collegato.  
  
## <a name="create-or-modify-a-linked-measure"></a>Creare o modificare una misura collegata  
 Utilizzare [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] per creare un gruppo di misure collegato.  
  
1.  Finalizzare ora tutte le modifiche al gruppo di misure originale nel cubo di origine, in modo tale che successivamente non sia necessario ricreare i gruppi di misure collegati nei cubi successivi. È possibile rinominare un oggetto collegato, ma non è possibile modificare altre proprietà.  
  
2.  In Esplora soluzioni fare doppio clic sul cubo a cui si sta aggiungendo il gruppo di misure collegato. Questo passaggio apre il cubo in Progettazione cubi.  
  
3.  Nel riquadro Misure o Dimensioni di Progettazione cubi fare clic con il pulsante destro del mouse in un punto qualsiasi del riquadro, quindi scegliere **Nuovo oggetto collegato**. Verrà avviato il Collegamento guidato oggetti.  
  
4.  Nella prima pagina specificare l'origine dati. In questo passaggio viene specificata la posizione del gruppo di misure originale. Per impostazione predefinita viene utilizzato il cubo corrente nel database corrente, ma è anche possibile scegliere un database di Analysis Services diverso.  
  
5.  Nella pagina successiva selezionare il gruppo di misure o le dimensioni da collegare. Le dimensioni e gli oggetti cubo, ad esempio i gruppi di misure, vengono elencati separatamente. Sono disponibili solo gli oggetti non ancora presenti nel cubo corrente.  
  
6.  Fare clic su **Fine** per creare l'oggetto collegato. Gli oggetti collegati verranno visualizzati nel riquadro Misure e Dimensioni, indicati dall'icona di collegamento.  
  
## <a name="secure-a-linked-measure"></a>Proteggere una misura collegata  
 Dopo avere definito il collegamento, l'accesso alle misure in un gruppo di misure collegato viene gestito così come l'accesso agli altri gruppi di misure. Un oggetto collegato viene visualizzato insieme alle relative controparti non collegate in Progettazione ruoli. Per altre informazioni sulla gestione della sicurezza per un gruppo di misure, vedere [Concedere le autorizzazioni per un cubo o un modello &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
 Per definire o usare un gruppo di misure collegato, è necessario che l'account del servizio di Windows per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] appartenga a un ruolo di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] con diritti di accesso **ReadDefinition** e **Lettura** nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di origine per il cubo e il gruppo di misure di origine o che appartenga al ruolo Administrators di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di origine.  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione delle dimensioni collegate](../../analysis-services/multidimensional-models/define-linked-dimensions.md)  
  
  
