---
title: Sviluppo di un'interfaccia utente per un provider di log personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3834457421187b8186042e169e939c76bfa6e05d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768557"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Sviluppo di un'interfaccia utente per un provider di log personalizzato
  Molti provider di log di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] hanno un'interfaccia utente personalizzata che implementa <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> e sostituisce la casella di testo **Configurazione** nella finestra di dialogo **Configura log SSIS** con un elenco a discesa filtrato di gestioni connessioni disponibili. Tuttavia, le interfacce utente personalizzate per i provider di log personalizzati non sono implementate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
![Icona di Integration Services (piccola)](../../media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services**<br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un provider di log personalizzato](creating-a-custom-log-provider.md)   
 [Scrittura del codice di un provider di log personalizzato](coding-a-custom-log-provider.md)  
  
  
