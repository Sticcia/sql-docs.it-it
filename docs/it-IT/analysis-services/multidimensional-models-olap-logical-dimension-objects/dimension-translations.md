---
title: Dimensione traduzioni | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8fbaaf3619b5a359de71299d1e5246e5670d5d7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimension-translations"></a>Traduzioni delle dimensioni
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Una traduzione è un semplice meccanismo che consente di modificare la lingua delle etichette e delle didascalie visualizzate. Ogni traduzione è definita come una coppia di valori: una stringa con il testo tradotto e un numero con l'ID della lingua. Le traduzioni sono disponibili per tutti gli oggetti in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nel caso delle dimensioni è possibile tradurre anche i valori di attributo. L'applicazione client è responsabile della ricerca dell'impostazione della lingua definita dall'utente e del passaggio alla visualizzazione di tutte le didascalie e le etichette nella lingua in questione. Un oggetto può disporre di un numero illimitato di traduzioni.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Translation> semplice è composto dal numero ID della lingua e dalla didascalia tradotta. Il numero di ID di lingua è un **intero** con l'ID di lingua. La didascalia tradotta è il testo tradotto.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], una traduzione della dimensione è una rappresentazione specifiche della lingua del nome di una dimensione, il nome di un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetto o uno dei relativi membri, ad esempio una didascalia, membro o la gerarchia di livello. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta anche conversioni di oggetti del cubo.  
  
 Le traduzioni offrono supporto server per applicazioni client in grado di supportare più lingue. I cubi e le relative dimensioni spesso vengono visualizzati da utenti di paesi diversi. La possibilità di tradurre vari elementi di un cubo e le relative dimensioni in un'altra lingua consente a tali utenti di visualizzare e comprendere il cubo. Un utente aziendale in Francia, ad esempio, può accedere a un cubo da una workstation in cui vengono utilizzate le impostazioni locali francesi e visualizzare i valori delle proprietà dell'oggetto in francese. Tuttavia, un utente aziendale in Germania che accede allo stesso cubo da una workstation in cui vengono utilizzate le impostazioni locali tedesche visualizzerà gli stessi valori delle proprietà dell'oggetto in tedesco.  
  
 Le informazioni sulle regole di confronto e sulla lingua per il computer client sono archiviate in forma di identificatore delle impostazioni locali (LCID). Al momento della connessione, il client passa l'identificatore delle impostazioni locali all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. che utilizza tale valore per determinare il set di traduzioni in cui restituire i metadati relativi agli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Se un oggetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non contiene la traduzione specificata, per restituire il contenuto al client viene utilizzata la lingua predefinita.  
  
## <a name="see-also"></a>Vedere anche  
 [Traduzioni di cubi](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)   
 [Supporto delle traduzioni in Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Suggerimenti per la globalizzazione e procedure consigliate & #40; Analysis Services & #41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  