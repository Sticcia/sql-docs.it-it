---
title: Selezione dei server da configurare (Configurazione guidata sicurezza mirroring del database) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f1353f53b663648e5f672f508b6ab86c8562eede
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a>Selezione dei server da configurare (Configurazione guidata sicurezza mirroring del database)
  Utilizzare questa pagina per specificare le istanze del server che si desidera configurare. Prima di proseguire con la procedura guidata è necessario selezionare almeno un'istanza del server.  
  
 Se si deseleziona la casella di controllo corrispondente a un'istanza del server, la procedura guidata non apporterà alcuna modifica a tale istanza. Verrà chiesto tuttavia di immettere informazioni sull'istanza, che verranno salvate come parte della configurazione delle altre istanze del server. Se ad esempio si deseleziona la casella di controllo corrispondente all'istanza del server di controllo del mirroring, la procedura guidata chiederà di immettere l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del server di controllo del mirroring, perché è necessario creare tale account di accesso come parte della configurazione di sicurezza salvata nelle istanze del server principale e del server mirror.  
  
 **Per configurare il mirroring del database tramite SQL Server Management Studio**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Avvio della Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Opzioni  
 **Istanza server principale**  
 Consente di configurare la sicurezza per il server principale.  
  
 **Istanza server mirror**  
 Consente di configurare la sicurezza per il server mirror.  
  
 **Istanza server di controllo del mirroring**  
 Consente di configurare la sicurezza per il server di controllo del mirroring, se presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del database &#40;Pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  