---
title: Aggiunta server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f3af2128d62e851e244509365504c361b596c5e5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>Aggiunta server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database)
  Utilizzare questa pagina per specificare se si desidera aggiungere un server di controllo del mirroring in questa configurazione di sicurezza per il mirroring del database.  
  
 **Per configurare il mirroring del database tramite SQL Server Management Studio**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Avvio della Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Opzioni  
 **Sì**  
 Fare clic su questo pulsante per aggiungere un'istanza del server di controllo del mirroring nella configurazione di sicurezza. Il server di controllo del mirroring è necessario per la modalità a disponibilità elevata con failover automatico, che supporta il failover automatico sull'istanza del server mirror in caso si verifichi un errore nell'istanza del server principale.  
  
 **No**  
 Fare clic su questo pulsante per impostare la configurazione di sicurezza senza un server di controllo del mirroring.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà database &#40;pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Server di controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  