---
title: Tipi di Sottoscrittore | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.subscribertypes.f1
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d417381f2da6229fcb93baad510e57dc7686de78
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135941"
---
# <a name="subscriber-types"></a>Tipi di Sottoscrittore
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La replica di tipo merge consente di specificare i tipi di Sottoscrittore che si richiede vengano supportati da una pubblicazione. La selezione dei tipi di Sottoscrittore causa l'impostazione del *livello di compatibilità della pubblicazione*, che determina le funzionalità utilizzabili da una pubblicazione.  
  
 Dopo aver creato una pubblicazione snapshot, è possibile aumentare il livello di compatibilità della pubblicazione, rendendolo più restrittivo, nella pagina **Generale** della finestra di dialogo **Proprietà pubblicazione** . Non è possibile diminuire il livello di compatibilità.  
  
## <a name="options"></a>Opzioni  
 Consente di selezionare i tipi di Sottoscrittore che devono essere supportati dalla pubblicazione.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 La pubblicazione è in grado di utilizzare tutte le funzionalità.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 La pubblicazione richiede che i file di snapshot siano in formato carattere, gestito automaticamente dall'agente snapshot. [!INCLUDE[ssEW](../../includes/ssew-md.md)] prevede inoltre alcune limitazioni non correlate al livello di compatibilità.  
  
 Se si seleziona questa opzione, l'opzione per la sincronizzazione Web viene abilitata per la pubblicazione. Per ulteriori informazioni sulla sincronizzazione Web, vedere [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
  
  
