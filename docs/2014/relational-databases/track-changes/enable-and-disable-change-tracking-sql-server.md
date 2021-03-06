---
title: Abilitare e disabilitare il rilevamento delle modifiche (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server], disabling
- data changes [SQL Server]
- change tracking [SQL Server], enabling
- tracking data changes [SQL Server]
- change tracking [SQL Server], configuring
- data [SQL Server], changing
ms.assetid: 1c92ec7e-ae53-4498-8bfd-c66a42a24d54
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: db1a34a93c740aac5e24734f0a5f07c2d6719b73
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670600"
---
# <a name="enable-and-disable-change-tracking-sql-server"></a>Abilitare e disabilitare il rilevamento delle modifiche (SQL Server)
  In questo argomento viene descritto come abilitare e disabilitare il rilevamento delle modifiche per un database e una tabella.  
  
## <a name="enable-change-tracking-for-a-database"></a>Abilitazione del rilevamento delle modifiche per un database  
 Prima di utilizzare il rilevamento delle modifiche, è necessario abilitarlo a livello di database. Nell'esempio seguente viene illustrato come abilitare il rilevamento delle modifiche usando [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = ON  
(CHANGE_RETENTION = 2 DAYS, AUTO_CLEANUP = ON)  
```  
  
 È anche possibile abilitare il rilevamento delle modifiche in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tramite la finestra di dialogo [Proprietà database &#40;pagina Rilevamento delle modifiche&#41;](../databases/database-properties-changetracking-page.md) .  
  
 È possibile specificare le opzioni CHANGE_RETENTION e AUTO_CLEANUP quando si abilita il rilevamento delle modifiche ed è possibile modificare i valori in qualsiasi momento dopo l'abilitazione del rilevamento.  
  
 Il valore di memorizzazione della modifica specifica il periodo di tempo durante il quale vengono mantenute le informazioni sul rilevamento delle modifiche. Le informazioni sul rilevamento delle modifiche precedenti a tale periodo di tempo vengono rimosse periodicamente. Durante l'impostazione di questo valore, considerare la frequenza di sincronizzazione delle applicazioni con le tabelle nel database. Il periodo di memorizzazione specificato deve durare almeno quanto il periodo di tempo massimo tra le sincronizzazioni. Se un'applicazione ottiene modifiche a intervalli più lunghi, i risultati restituiti potrebbero non essere corretti, poiché alcune delle informazioni sulle modifiche sono state probabilmente rimosse. Per evitare di ottenere risultati non corretti, un'applicazione può utilizzare la funzione di sistema CHANGE_TRACKING_MIN_VALID_VERSION per determinare se l'intervallo tra sincronizzazioni è stato troppo lungo.  
  
 Per abilitare o disabilitare l'attività di pulizia che rimuove le informazioni obsolete sul rilevamento delle modifiche, è possibile utilizzare l'opzione AUTO_CLEANUP. Questa procedura può risultare utile quando un problema temporaneo impedisce la sincronizzazione delle applicazioni e la procedura di rimozione delle informazioni sul rilevamento delle modifiche precedenti al periodo di memorizzazione deve essere messa in pausa finché il problema non viene risolto.  
  
 Per qualsiasi database che utilizza il rilevamento delle modifiche, tenere presente quanto segue:  
  
-   Per utilizzare il rilevamento delle modifiche, il livello di compatibilità del database deve essere impostato su 90 o su un valore superiore. Se il livello di compatibilità del database è minore di 90, è possibile comunque configurare il rilevamento delle modifiche, ma la funzione CHANGETABLE, utilizzata per ottenere informazioni sul rilevamento delle modifiche, restituirà un errore.  
  
-   L'utilizzo dell'isolamento dello snapshot rappresenta il modo più semplice per garantire che tutte le informazioni sul rilevamento delle modifiche siano coerenti. Per questo motivo, è consigliabile impostare l'isolamento dello snapshot per il database su ON. Per altre informazioni, vedere [Usare il rilevamento delle modifiche &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).  
  
## <a name="enable-change-tracking-for-a-table"></a>Abilitazione del rilevamento delle modifiche per una tabella  
 Il rilevamento delle modifiche deve essere abilitato per ciascuna tabella per cui si desidera eseguirlo. Quando il rilevamento delle modifiche è abilitato, le relative informazioni vengono gestite per tutte le righe della tabella interessate da un'operazione DML.  
  
 Nell'esempio seguente viene illustrato come abilitare il rilevamento delle modifiche per una tabella tramite [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).  
  
```sql  
ALTER TABLE Person.Contact  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
 È anche possibile abilitare il rilevamento delle modifiche per una tabella in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tramite la finestra di dialogo [Proprietà database &#40;pagina Rilevamento delle modifiche&#41;](../databases/database-properties-changetracking-page.md) .  
  
 Quando l'opzione TRACK_COLUMNS_UPDATED è impostata su ON, nel [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] vengono archiviate informazioni aggiuntive sulle colonne aggiornate nella tabella del rilevamento delle modifiche interna. Il rilevamento a livello di colonna consente di sincronizzare solo le colonne aggiornate. Ciò può migliorare efficienza e prestazioni. Tuttavia, poiché la gestione delle informazioni sul rilevamento a livello della colonna aggiunge un ulteriore overhead di archiviazione, per impostazione predefinita questa opzione è impostata su OFF.  
  
## <a name="disable-change-tracking-for-a-database-or-table"></a>Disabilitazione del rilevamento delle modifiche per un database o una tabella  
 Il rilevamento delle modifiche deve essere prima disabilitato per tutte le tabelle di cui sono state rilevate le modifiche prima che il rilevamento possa essere impostato su OFF per il database. Per determinare le tabelle in cui è abilitato il rilevamento delle modifiche per un database, usare la vista del catalogo [sys.change_tracking_tables](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables) .  
  
 Quando non vengono rilevate modifiche in nessuna tabella di un database, è possibile disabilitare il rilevamento delle modifiche per il database. Nell'esempio seguente viene illustrato come disabilitare il rilevamento delle modifiche per un database tramite [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET CHANGE_TRACKING = OFF  
```  
  
 Nell'esempio seguente viene illustrato come disabilitare il rilevamento delle modifiche per una tabella tramite [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).  
  
```sql  
ALTER TABLE Person.Contact  
DISABLE CHANGE_TRACKING;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà database &#40;pagina Rilevamento delle modifiche&#41;](../databases/database-properties-changetracking-page.md)   
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [sys.change_tracking_databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases)   
 [sys.change_tracking_tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/change-tracking-catalog-views-sys-change-tracking-tables)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](track-data-changes-sql-server.md)   
 [Informazioni sul rilevamento delle modifiche &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md)   
 [Usare Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md)   
 [Gestire il rilevamento delle modifiche &#40;SQL Server&#41;](manage-change-tracking-sql-server.md)  
  
  
