---
title: Dimensioni padre-figlio | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f9990103da1de5107ceaf3432f4da2a9a4486c4
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510207"
---
# <a name="parent-child-dimension"></a>Dimensione padre-figlio
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Una gerarchia padre-figlio è una gerarchia in una dimensione standard contenente un attributo padre. Un attributo padre descrive una *relazione autoreferenziale*, o *self join*, in una tabella della dimensione principale. Le gerarchie padre-figlio vengono create da un unico attributo padre. A una gerarchia padre-figlio viene assegnato un solo livello, in quanto i livelli presenti nella gerarchia sono derivati dalle relazioni padre-figlio tra i membri associati all'attributo padre. La posizione di un membro in una gerarchia padre-figlio è determinata dalle proprietà **KeyColumns** e **RootMemberIf** dell'attributo padre, mentre la posizione di un membro in un livello è determinata dalla proprietà **OrderBy** dell'attributo padre. Per altre informazioni sulle proprietà degli attributi, vedere [Attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
 A causa delle relazioni padre-figlio tra livelli in una gerarchia padre-figlio, alcuni membri non foglia potrebbero includere anche dati derivati dalle origini dei dati sottostanti oltre ai dati aggregati dai membri figlio.  
  
## <a name="dimension-schema"></a>Schema della dimensione  
 Lo schema della dimensione di una gerarchia padre-figlio dipende da una relazione autoreferenziale presente nella tabella della dimensione principale. Nella figura seguente, ad esempio, viene illustrata la tabella principale della dimensione **DimOrganization** nel database di esempio [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] .  
  
 ![Join autoreferenziale nella tabella DimOrganization](../../analysis-services/multidimensional-models/media/dimorganization.gif "join autoreferenziale nella tabella DimOrganization")  
  
 In questa tabella della dimensione, nella colonna **dbo.xdbcdc_databases** è inclusa una relazione di chiave esterna con la colonna chiave primaria **OrganizationKey** . In altri termini, ogni record di questa tabella può essere messo in relazione a un altro record della tabella tramite una relazione padre-figlio. Questo tipo di self join viene in genere utilizzato per rappresentare dati entità dell'organizzazione, ad esempio la struttura di gestione dei dipendenti in un reparto.  
  
## <a name="hierarchies-and-levels"></a>Gerarchie e livelli  
 Nelle dimensioni che non dispongono di una relazione padre-figlio le gerarchie vengono create raggruppando e ordinando gli attributi. Queste dimensioni derivano i nomi dei livelli delle relative gerarchie dai nomi degli attributi.  
  
 Nelle dimensioni padre-figlio, tuttavia, le gerarchie vengono create analizzando i dati contenuti nella tabella della dimensione principale e quindi valutando le relazioni padre-figlio tra i record della tabella. Per altre informazioni sulle gerarchie padre-figlio, vedere [Gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).  
  
 Le gerarchie padre-figlio non derivano i nomi dei livelli in una gerarchia padre-figlio dagli attributi utilizzati per creare la gerarchia. Invece di creare nomi di livello tali dimensioni automaticamente usando un'espressione di modello, ovvero una stringa dei nomi è possibile specificare a livello di attributo padre che controlla di controllare l'attributo la gerarchia dell'attributo. Per altre informazioni sull'impostazione del modello di denominazione per un attributo padre, vedere [Attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## <a name="data-members"></a>Membri dei dati  
 In genere, i membri foglia di una dimensione contengono dati derivati direttamente dalle origini dei dati sottostanti, mentre i membri non foglia contengono dati derivati dalle aggregazioni eseguite sui membri figlio.  
  
 Nelle gerarchie padre-figlio potrebbero tuttavia essere presenti membri non foglia contenenti dati derivati dalle origini dei dati sottostanti oltre ai dati aggregati dai membri figlio. Per questi membri non foglia di una gerarchia padre-figlio, è possibile creare membri figlio speciali generati dal sistema contenenti i dati della tabella dei fatti sottostante. Questi membri figlio speciali, denominati *membri dei dati*, contengono un valore associato direttamente a un membro non foglia e indipendente dal valore di riepilogo calcolato dai discendenti del membro non foglia. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi nelle gerarchie padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)   
 [Proprietà delle dimensioni del database](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
