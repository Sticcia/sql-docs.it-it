---
title: "Proprietà pubblicazione, Elenco accesso pubblicazione | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
ms.assetid: 9587bb9e-c66c-4e70-8171-09b943ec2d50
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d088078d9f36e1ca6fc0bc49cb324f95dd2f1db2
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="publication-properties-publication-access-list"></a>Proprietà pubblicazione, Elenco accesso pubblicazione
  La pagina **Elenco accesso pubblicazione** della finestra di dialogo **Proprietà pubblicazione** consente di aggiungere e rimuovere account di accesso, account e gruppi dall'elenco di accesso alla pubblicazione. L'elenco di accesso alla pubblicazione costituisce il principale sistema di sicurezza del server di pubblicazione. Quando si crea una pubblicazione, la replica crea un elenco di accesso alla pubblicazione per la pubblicazione creata. L'elenco di accesso alla pubblicazione opera in modo analogo all'elenco di controllo di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] e include un elenco di account di accesso, account e gruppi ai quali viene consentito l'accesso alla pubblicazione.  
  
 Quando un Sottoscrittore si connette al server di pubblicazione o al server di distribuzione e richiede l'accesso alla pubblicazione, l'account di accesso del Sottoscrittore viene confrontato con le informazioni di autenticazione contenute nell'elenco di accesso alla pubblicazione. Ciò garantisce un maggior livello di sicurezza del server di pubblicazione, impedendo che gli account di accesso del server di pubblicazione e del server di distribuzione vengano utilizzati da uno strumento client per apportare modifiche direttamente nel server di pubblicazione. Per altre informazioni, vedere [Proteggere il server di pubblicazione](../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="options"></a>Opzioni  
 **Aggiungi**  
 Consente di aggiungere una nuova voce all'elenco. È possibile aggiungere solo gli account di accesso, gli account o i nomi dei gruppi già definiti sia nel server di pubblicazione sia nel server di distribuzione. Tali account di accesso, account e nomi di gruppi vengono definiti in entrambi i server nei casi in cui si utilizzino account di dominio o siano stati creati account locali in entrambi i server.  
  
 **Rimuovi**  
 Consente di rimuovere la voce selezionata dall'elenco.  
  
 **Rimuovi tutto**  
 Consente di rimuovere tutte le voci dall'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  