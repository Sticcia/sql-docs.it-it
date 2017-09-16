---
title: Strumenti degli eventi estesi | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], using
- extended events [SQL Server], options for using
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 923b012345d18abb393479744a65b4572cb20a08
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="extended-events-tools"></a>Strumenti degli eventi estesi
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  È possibile utilizzare gli strumenti seguenti per creare e gestire sessioni Eventi estesi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Istruzioni DDL (Data Definition Language). Queste istruzioni consentono di creare e modificare una sessione Eventi estesi.  
  
-   DMV, viste del catalogo e tabelle di sistema. Questi strumenti consentono di ottenere dati e metadati della sessione tramite istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] . Le tabelle di sistema consentono di determinare gli equivalenti degli eventi estesi esistenti per colonne e classi di eventi di Traccia SQL.  
  
-   Nodo **Eventi estesi** di Esplora oggetti. Questo nodo consente di avviare, arrestare o eliminare una sessione oppure di importare ed esportare modelli della sessione.  
  
-   Provider PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Questo potente strumento consente di creare, modificare e gestire sessioni Eventi estesi. Per altre informazioni, vedere [Utilizzare il provider PowerShell per eventi estesi](../../relational-databases/extended-events/use-the-powershell-provider-for-extended-events.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Questo strumento consente di creare ed eseguire gli esempi di codice forniti negli argomenti relativi agli eventi estesi. Per altre informazioni, vedere [Esplora oggetti](http://msdn.microsoft.com/library/469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2).  
  
 Oltre alle sessioni create, nel server è presente una sessione di integrità di sistema predefinita. Tale sessione consente di raccogliere dati di sistema che è possibile utilizzare per risolvere i problemi relativi alle prestazioni. Per altre informazioni, vedere [Utilizzare la sessione system_health](../../relational-databases/extended-events/use-the-system-health-session.md).  
  
## <a name="ddl-statements"></a>Istruzioni DDL  
 Le istruzioni DDL seguenti consentono di creare, modificare ed eliminare una sessione Eventi estesi.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)|Consente di creare un oggetto sessione Eventi estesi che identifica l'origine degli eventi, nonché le destinazioni e i parametri delle sessioni eventi.|  
|[ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)|Consente di avviare o arrestare una sessione eventi oppure di modificare la configurazione di una sessione eventi.|  
|[DROP EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-event-session-transact-sql.md)|Consente di eliminare una sessione eventi.|  
  
## <a name="catalog-views"></a>Viste del catalogo  
 Le viste del catalogo seguenti consentono di ottenere i metadati creati al momento della creazione della sessione eventi.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)|Elenca tutte le definizioni di sessione di evento.|  
|[sys.server_event_session_actions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql.md)|Restituisce una riga per ogni azione su ogni evento di una sessione dell'evento.|  
|[sys.server_event_session_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql.md)|Restituisce una riga per ogni evento in una sessione dell'evento.|  
|[sys.server_event_session_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql.md)|Restituisce una riga per ogni colonna personalizzabile che è impostata in modo esplicito su eventi e destinazioni.|  
|[sys.server_event_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql.md)|Restituisce una riga per ogni destinazione di evento per una sessione eventi.|  
  
## <a name="dynamic-management-views"></a>DMV  
 Le DMV seguenti consentono di ottenere metadati e dati delle sessioni. I metadati vengono ottenuti dalle viste del catalogo e i dati della sessione vengono creati quando si avvia e si esegue una sessione eventi.  
  
> [!NOTE]  
>  Queste viste non contengono dati della sessione fino a che non viene avviata una sessione.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql.md)|Restituisce le informazioni sui pool di dispatcher di sessione.|  
|[sys.dm_xe_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)|Restituisce una riga per ogni oggetto esposto da un pacchetto dell'evento.|  
|[sys.dm_xe_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)|Restituisce le informazioni sullo schema per tutti gli oggetti.|  
|[sys.dm_xe_packages &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql.md)|Restituisce un elenco di tutti i pacchetti registrati con il motore degli eventi estesi.|  
|[sys.dm_xe_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql.md)|Restituisce informazioni su una sessione Eventi estesi attiva.|  
|[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql.md)|Restituisce informazioni sulle destinazioni della sessione.|  
|[sys.dm_xe_session_events &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql.md)|Restituisce informazioni sugli eventi di sessione.|  
|[sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql.md)|Restituisce informazioni sulle azioni di sessione di evento.|  
|[sys.dm_xe_map_values &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql.md)|Fornisce un mapping di chiavi numeriche interne in un testo leggibile.|  
|[sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql.md)|Mostra i valori di configurazione per gli oggetti associati a una sessione.|  
  
## <a name="system-tables"></a>Tabelle di sistema  
 Le tabelle di sistema seguenti consentono di ottenere informazioni sugli equivalenti degli eventi estesi per colonne e classi di eventi di Traccia SQL.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[trace_xe_event_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-event-map.md)|Contiene una riga per ogni evento degli eventi estesi di cui è stato eseguito il mapping a una classe di evento di Traccia SQL.|  
|[trace_xe_action_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)|Contiene una riga per ogni azione degli eventi estesi di cui è stato eseguito il mapping a un ID della colonna di Traccia SQL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Tabelle degli eventi estesi di SQL Server &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)   
 [Utilizzare la sessione system_health](../../relational-databases/extended-events/use-the-system-health-session.md)   
 [Utilizzare il provider PowerShell per eventi estesi](../../relational-databases/extended-events/use-the-powershell-provider-for-extended-events.md)  
  
  
