---
title: Database di distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6c0a98aa13b4453244c8ed565a950660a20e5a3c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721304"
---
# <a name="distributor"></a>Database di distribuzione
  La pagina **Server di distribuzione** viene visualizzata nella Configurazione guidata distribuzione e nella Creazione guidata nuova pubblicazione. Il server di distribuzione è il server che contiene il database di distribuzione e che gestisce l'archiviazione dei metadati e dei dati di cronologia per tutti i tipi di replica. Il server di distribuzione gestisce inoltre l'archiviazione delle transazioni per la replica transazionale. Il server di distribuzione può corrispondere al server di pubblicazione (server di distribuzione locale) o essere un server distinto (server di distribuzione remoto). Il ruolo del server di distribuzione varia in base al tipo di replica implementato. In generale, il ruolo del server di distribuzione è più rilevante per la replica transazionale rispetto a quanto non lo sia per la replica di tipo merge e snapshot. La replica di tipo merge e la replica snapshot utilizzano normalmente un server di distribuzione locale, mentre la replica transazionale in sistemi sottoposti a un utilizzo particolarmente intensivo possono trarre vantaggio dall'utilizzo di un server di distribuzione remoto.  
  
 Il server di distribuzione utilizza le risorse aggiuntive seguenti nel server in cui è installato:  
  
-   Maggiore spazio su disco se i file di snapshot per la pubblicazione sono archiviati al suo interno, così come avviene normalmente.  
  
-   Maggiore spazio su disco per l'archiviazione del database di distribuzione.  
  
-   Maggior utilizzo del processore da parte degli agenti di replica per le sottoscrizioni push in esecuzione nel server di distribuzione.  
  
 Nel server selezionato come server di distribuzione devono essere disponibili spazio su disco e capacità del processore sufficienti per il supporto delle attività di replica e di altre eventuali operazioni basate su tale server.  
  
## <a name="options"></a>Opzioni  
 **'\<NomeServer>' fungerà da database di distribuzione per se stesso. Verranno creati un database di distribuzione e un log**  
 Selezionare questa opzione per configurare il server a cui si è connessi come server di distribuzione.  
  
 **Usa il server seguente come server di distribuzione (nota: il server selezionato deve essere già stato configurato come server di distribuzione)**  
 Selezionare questa opzione e quindi fare clic sul nome di un server elencato per configurare un altro server come server di distribuzione.  
  
 **Aggiungi**  
 Se il server che si desidera utilizzare non è elencato come server di distribuzione, fare clic su **Aggiungi** per identificare il server e aggiungerlo all'elenco.  
  
> [!NOTE]  
>  Per utilizzare un server remoto come server di distribuzione è necessario che il server remoto sia già stato configurato come server di distribuzione. Il server sul quale è in esecuzione la procedura guidata deve essere stato abilitato come server di pubblicazione nel server di distribuzione specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Configura distribuzione](configure-distribution.md)   
 [Configurare la pubblicazione e la distribuzione](configure-publishing-and-distribution.md)  
  
  
