---
title: Rimuovere i riferimenti a procedure di sistema deprecate archiviato | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5f87cb9160925ccc813ee62737662f85f430f28b
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582864"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a>Rimuovere i riferimenti alle stored procedure di sistema deprecate
  Sono state rilevate istruzioni che fanno riferimento a stored procedure di sistema e stored procedure estese non documentate che non sono più disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le istruzioni che fanno riferimento a tali oggetti non verranno eseguite. Evitare di utilizzare oggetti di sistema o API non documentati, perché la funzionalità potrebbe cambiare oppure potrebbero venire rimossi senza comunicazione in una versione futura.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descrizione  
  
### <a name="documented-system-stored-procedures"></a>Stored procedure di sistema documentate  
 Le seguenti stored procedure di sistema documentate sono state rimosse:  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
### <a name="undocumented-system-stored-procedures"></a>Stored procedure di sistema non documentate  
 Le seguenti stored procedure di sistema e stored procedure estese non documentate sono state rimosse:  
  
-   sp_articlesynctranprocs  
  
-   sp_diskdefault  
  
-   sp_EventLog  
  
-   sp_GetMBCSCharLen  
  
-   sp_helplog  
  
-   sp_helpsql  
  
-   sp_IsMBCSLeadByte  
  
-   sp_lock2  
  
-   sp_MSget_current_activity  
  
-   sp_MSset_current_activity  
  
-   sp_MSobjessearch  
  
-   xp_enum_ActiveScriptEngines  
  
-   xp_eventlog  
  
-   xp_GetAdminGroupName  
  
-   xp_GetFileDetails  
  
-   xp_GetLocalSystemAccountName  
  
-   xp_IsNTAdmin  
  
-   xp_MSLocalSystem  
  
-   xp_MSnt2000  
  
-   xp_MSplatform  
  
-   xp_SetSecurity  
  
-   xp_varbintohexstr  
  
## <a name="corrective-action"></a>Azione correttiva  
  
### <a name="documented-system-stored-procedures"></a>Stored procedure di sistema documentate  
 Modificare le applicazioni in base alla tabella seguente.  
  
|Anziché|Procedere nel modo seguente|  
|----------------|-------------|  
|sp_addalias|Sostituire gli alias con una combinazione di account utente e ruoli del database. Per ulteriori informazioni, vedere gli argomenti "CREATE USER (Transact-SQL)" e "CREATE ROLE (Transact-SQL)" nella documentazione online di SQL Server. Rimuovere gli alias nei database aggiornati utilizzando sp_dropalias.|  
|sp_addgroupsp_changegroup<br /><br /> sp_dropgroup<br /><br /> sp_helpgroup|Utilizzare i ruoli. Per ulteriori informazioni, vedere gli argomenti relativi ai ruoli a livello di server e ai ruoli a livello di database nella documentazione online di SQL Server.|  
  
### <a name="undocmented-system-stored-procedures"></a>Stored procedure di sistema non documentate  
 È possibile creare stored procedure CLR con funzionalità equivalente per sostituire le stored procedure di sistema non documentate. Per ulteriori informazioni, vedere l'argomento "Stored procedure CLR" nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
