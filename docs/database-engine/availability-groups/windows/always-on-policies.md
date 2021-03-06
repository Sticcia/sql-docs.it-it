---
title: Valutare l'integrità del gruppo di disponibilità usando i criteri di gruppo
description: Informazioni su come visualizzare i criteri di sistema dei gruppi che il dashboard Always On usa per presentare informazioni sull'integrità del gruppo di disponibilità.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d049d012c9447eeb79cd2d64435d37223540adb5
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044607"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Valutare l'integrità del gruppo di disponibilità Always On usando i criteri di gruppo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  I criteri di sistema dei gruppi di disponibilità Always On vengono usati dal dashboard Always On per comunicare all'utente informazioni sullo stato di integrità dei gruppi di disponibilità. Sono molto utili per le attività iniziali di risoluzione dei problemi operativi con un gruppo di disponibilità. Questi criteri possono essere estesi e utilizzati per personalizzare il dashboard Always On o eseguiti immediatamente per segnalare le informazioni di integrità desiderate.  
  
 Esistono 14 criteri di sistema per i gruppi di disponibilità. Per informazioni dettagliate su ogni criterio, vedere [Criteri Always On per problemi operativi con gruppi di disponibilità Always On (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Visualizzare o valutare i criteri di sistema dei gruppi di disponibilità  
 Per visualizzare o eseguire i criteri di sistema dei gruppi di disponibilità in SQL Server Management Studio (SSMS), eseguire le operazioni seguenti:  
  
1.  In **Esplora oggetti** espandere **Gestione**, **Gestione criteri**, **Criteri** e quindi **Criteri di sistema**.  
  
2.  Fare clic con il pulsante destro su uno dei criteri e fare clic su **Valuta**. Se l'intenzione era valutare il criterio selezionato, l'operazione è conclusa. Fare clic su **Visualizza** nella casella **Dettagli destinazione** per visualizzare i dettagli dei risultati della valutazione.  
  
3.  Per visualizzare tutti i criteri di sistema dei gruppi di disponibilità, fare clic su **Selezione** nel riquadro **Seleziona una pagina**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Il modello di integrità Always On, parte 2: Estensione del modello di integrità](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx).   
  
  
