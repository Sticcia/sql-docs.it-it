---
title: Connettersi a Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3b02eb586db5bc18ffa96c8a24037d48fbe4695a
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728916"
---
# <a name="connect-to-oracle"></a>Connettersi a Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Quando si aggiungono o modificano le tabelle utilizzate nell'istanza di CDC per la prima volta, è possibile che venga richiesto di connettersi al database Oracle. Immettere le credenziali di un utente Oracle che può accedere allo schema delle tabelle da acquisire. Immettere quanto segue nella finestra di dialogo:  
  
 **Autenticazione**  
  
 Selezionare una delle opzioni seguenti:  
  
-   **Windows Authentication**: selezionare questa opzione per utilizzare le credenziali del dominio Windows correnti. È possibile utilizzare questa opzione solo se il database Oracle è configurato per l'utilizzo dell'autenticazione di Windows.  
  
-   **Oracle Authentication**: se si seleziona questa opzione, è necessario digitare il **nome utente** e la **password** dell'utente nel database Oracle a cui si effettua la connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere tabelle a un'istanza di CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
