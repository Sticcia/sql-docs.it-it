---
title: Sono state rilevate estensioni obsolete nel computer del server di report (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6188ddab466ccbb27e121e5500a9af68ecbd71fb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067610"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a>Sono state rilevate estensioni obsolete nel computer del server di report (Upgrade Advisor)
  Sono state rilevate una o più estensioni per il rendering non più disponibili nella versione corrente.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  Modalità nativa di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] &#124; Modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Descrizione  
 Il server di report è configurato per l'utilizzo di una o più estensioni che non sono più disponibili in questa versione. Di seguito vengono riportate le estensioni non più utilizzate:  
  
-   Estensione per il rendering HTML OWC  
  
-   Estensione per il rendering HTML 3.2  
  
 L'aggiornamento può continuare, ma la funzionalità non supportata non sarà più disponibile sul server di report aggiornato.  
  
 Se queste estensioni sono necessarie, non eseguire l'aggiornamento fino a quando non sono state individuate soluzioni alternative. Potrebbe essere necessario ottenere o compilare un'estensione per il rendering personalizzata con la stessa funzionalità o una analoga.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Valutare il set corrente di caratteristiche incluse in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per determinare se la funzionalità supportata soddisfa i requisiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
