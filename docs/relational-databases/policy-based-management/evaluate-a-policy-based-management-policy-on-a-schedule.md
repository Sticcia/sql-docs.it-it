---
title: Valutare i criteri della gestione basata su criteri in una pianificazione | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: dc78ec53189ff3f9deae1a95895c12ac33cd25d7
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588616"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a>Valutare i criteri della gestione basata su criteri in una pianificazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento verrà descritto come valutare i criteri della gestione basata su criteri in una pianificazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per valutare i criteri in una pianificazione tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a>Per valutare i criteri in una pianificazione  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente la pianificazione dei criteri da valutare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Criteri** .  
  
5.  Fare clic con il pulsante destro del mouse sui criteri di cui si desidera valutare la pianificazione, quindi scegliere **Proprietà**.  
  
6.  Nella finestra di dialogo **Apri criteri -**_nome_criterio_ selezionare **Su pianificazione** nell'elenco **Modalità di valutazione**.  
  
7.  In **Pianificazione**fare clic su **Seleziona** per specificare una pianificazione esistente o su **Nuova** per creare una nuova pianificazione.  
  
8.  Al termine, fare clic su **OK**.  
  
  
