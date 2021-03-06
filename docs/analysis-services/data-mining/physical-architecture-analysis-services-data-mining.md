---
title: Architettura fisica (Analysis Services - Data Mining) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99e2cf7386bdf395ac82f05cc0b94f3e2b5e3123
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62668518"
---
# <a name="physical-architecture-analysis-services---data-mining"></a>Architettura fisica (Analysis Services – Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usa componenti server e client per fornire funzionalità di data mining alle applicazioni di Business Intelligence:  
  
-   Il componente server viene implementato come un servizio di Microsoft Windows. È possibile avere più istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sullo stesso computer, ognuna delle quali viene implementata come istanza separata del servizio di Windows.  
  
-   I client comunicano con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante lo standard pubblico XML for Analysis (XMLA), un protocollo basato su SOAP per l'esecuzione di comandi e la ricezione di risposte che viene esposto come un servizio Web. Tramite XMLA vengono inoltre offerti modelli a oggetti client a cui è possibile accedere usando un provider gestito, ad esempio ADOMD.NET, o un provider OLE DB nativo.  
  
-   I comandi di query possono essere eseguiti utilizzando il linguaggio DMX (Data Mining Extensions), un linguaggio di query standard orientato al data mining, e il linguaggio ASSL (Analysis Services Scripting Language), che consente di gestire gli oggetti di database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="architectural-diagram"></a>Diagramma dell'architettura  
 Un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene eseguita come un servizio autonomo e la comunicazione con il servizio avviene tramite XML for Analysis (XMLA), usando HTTP o TCP.  
  
 AMO è un livello tra l'applicazione utente e l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che fornisce accesso agli oggetti amministrativi di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . AMO è una libreria di classi che accetta i comandi da un'applicazione client e li converte in messaggi XMLA per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . AMO presenta oggetti dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] come classi all'applicazione dell'utente finale, coi membri dei metodi che eseguono i comandi e i membri delle proprietà che utilizzano i dati per gli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Nell'illustrazione seguente sono illustrati i componenti dell'architettura [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , inclusi i servizi nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e i componenti utente che interagiscono con essa.  
  
 L'illustrazione mostra inoltre che il solo modo di accedere all'istanza è tramite il listener di XML for Analysis (XMLA), utilizzando HTTP o TCP.  
  
> [!WARNING]  
>  DSO è deprecato. Non utilizzare DSO per sviluppare soluzioni.  
  
 ![Diagramma dell'architettura di sistema di Analysis Services](../../analysis-services/data-mining/media/analysisservicessystemarchitecture.gif "diagramma dell'architettura di sistema di Analysis Services")  
  
## <a name="server-configuration"></a>Configurazione server  
 Un'istanza del server è in grado di supportare più database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ognuno con la propria istanza del servizio [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che risponde alle richieste client ed elabora oggetti.  
  
 È necessario installare istanze separate se si desidera utilizzare sia modelli tabulari sia modelli di data mining e/o multidimensionali. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta l'installazione side-by-side di istanze in esecuzione in modalità tabulare, che usa il motore di analisi in memoria xVelocity (VertiPaq), e istanze in esecuzione in una delle configurazioni OLAP, MOLAP o ROLAP convenzionali. Per altre informazioni, vedere [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
 Per tutte le comunicazioni tra un client e il server Analysis Services viene utilizzato XMLA, un protocollo indipendente da piattaforma e linguaggio. Quando viene ricevuta una richiesta da un client, Analysis Services determina se tale richiesta è correlata a OLAP o al data mining, quindi la indirizza nel modo appropriato. Per altre informazioni sui componenti server, vedere [Componenti del server del motore OLAP](../../analysis-services/multidimensional-models/olap-physical/olap-engine-server-components.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura logica &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)  
  
  
