---
title: Testare le autorizzazioni di un utente (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 38d4b1e7f9bd3e76c00bb4228e53e09416ed8557
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488096"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Testare le autorizzazioni di un utente (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile creare un utente test e accedere all'applicazione Web per testare le autorizzazioni, Quando un utente tenta di accedere all'URL di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , le credenziali dell'utente vengono autenticate. In Internet Explorer le impostazioni di sicurezza controllano se l'autenticazione viene eseguita automaticamente o se l'utente deve immettere nome utente e password. Per modificare queste impostazioni, effettuare i passaggi seguenti:  
  
### <a name="to-test-a-users-security"></a>Per testare la sicurezza di un utente  
  
1.  In Internet Explorer 7 o versione successiva scegliere **Opzioni Internet**dal menu **Strumenti**, quindi fare clic sulla scheda **Sicurezza** .  
  
2.  Fare clic su **Intranet locale** e quindi sul pulsante **Livello personalizzato** .  
  
3.  Nella sezione **Autenticazione utente** scegliere **Richiedi nome utente e password**.  
  
4.  Alla successiva apertura della finestra del browser, verrà richiesto di immettere un nome utente e una password.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
