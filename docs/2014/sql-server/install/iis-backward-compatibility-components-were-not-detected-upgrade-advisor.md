---
title: Compatibilità con le versioni precedenti di IIS componenti non sono stati rilevati (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- IIS [Reporting Services]
ms.assetid: e794185a-0a77-480a-9aea-d09f8760a6b8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae12d01dccc3999c90ceffb409767b67e992f660
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083891"
---
# <a name="iis-backward-compatibility-components-were-not-detected-upgrade-advisor"></a>Non sono stati rilevati componenti di compatibilità con le versioni precedenti di IIS (Upgrade Advisor)
  Non sono stati rilevati componenti e impostazioni IIS che forniscono le informazioni utilizzate dal programma di installazione per creare nuovi URL di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 IIS include componenti che forniscono informazioni sulle directory virtuali del server di report e di Gestione report. Tali componenti non sono installati nel computer del server di report. L'aggiornamento può continuare, ma gli URL per il server di report o per Gestione report non verranno ricreati con l'aggiornamento.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Dopo l'aggiornamento, utilizzare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per impostare gli URL per il server di report o Gestione report. Utilizzare Gestione IIS per rimuovere le directory virtuali non più necessarie.  
  
 Per altre informazioni, vedere [configurare un URL &#40;Gestione configurazione SSRS&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) nelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
