---
title: Connetti al server (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64c565c45288de157a3ba4c6c367ae7f8849dfee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808702"
---
# <a name="connect-to-server-integration-services"></a>Connetti al server (Integration Services)
  Usare questa finestra di dialogo per visualizzare o specificare le opzioni per la connessione a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Tipo server**  
 Per la registrazione di un server da Esplora oggetti, selezionare il tipo di server a cui connettersi, ovvero [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da Server registrati, la casella Tipo server è di sola lettura e corrisponde al tipo di server visualizzato nel componente Server registrati. Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti Server registrati prima di avviare la registrazione di un nuovo server.  
  
 **Nome server**  
 Consente di selezionare il server a cui connettersi. Per impostazione predefinita verrà visualizzata l'ultima istanza del server a cui è stata effettuata la connessione.  
  
> [!NOTE]  
>  Non utilizzare  *\<nomeserver >*\\*\<NomeIstanza >* perché [!INCLUDE[ssIS](../includes/ssis-md.md)] non supporta più istanze in un computer.  
  
 **Autenticazione**  
 Solo l'autenticazione di [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows è disponibile per [!INCLUDE[ssIS](../includes/ssis-md.md)]. Tale modalità consente di connettersi tramite un account utente di Windows.  
  
 **Nome utente**  
 Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../includes/ssis-md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
 **Password**  
 Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../includes/ssis-md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
 **Connect**  
 Fare clic su questo pulsante per connettersi al server selezionato.  
  
 **Opzioni**  
 Fare clic su questo pulsante per visualizzare ulteriori opzioni per la connessione al server, come le opzioni per la registrazione di un server e la memorizzazione della password.  
  
  
