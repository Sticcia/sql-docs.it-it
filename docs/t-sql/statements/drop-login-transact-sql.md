---
title: DROP LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP LOGIN
- DROP_LOGIN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting login accounts
- logins [SQL Server], removing
- DROP LOGIN statement
- removing login accounts
- dropping login accounts
ms.assetid: acb5c3dc-7aa2-49f6-9330-573227ba9b1a
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3eec950bbf9270a9c31dc0d5b23ba3b4a5cd0a3
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361421"
---
# <a name="drop-login-transact-sql"></a>DROP LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP LOGIN login_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *login_name*  
 Specifica il nome dell'account di accesso da eliminare.  
  
## <a name="remarks"></a>Remarks  
 Non è possibile eliminare un account di accesso connesso. Non è possibile eliminare un account di accesso proprietario di un'entità a protezione diretta, un oggetto a livello di server oppure un processo di SQL Server Agent.  
  
 È possibile eliminare un account di accesso a cui viene eseguito il mapping degli utenti del database. In questo caso, tuttavia, verranno creati utenti isolati (orfani). Per altre informazioni, vedere [Risolvere i problemi relativi agli utenti isolati &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md).  
  
 Nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] i dati dell'account di accesso necessari per autenticare una connessione e le regole del firewall a livello di server vengono memorizzati temporaneamente nella cache in ogni database. Questa cache viene aggiornata periodicamente. Per forzare un aggiornamento della cache di autenticazione e assicurarsi che un database abbia la versione più recente della tabella di account di accesso, eseguire [DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY LOGIN nel server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-login"></a>A. Eliminazione di un account di accesso  
 Nell'esempio seguente l'account di accesso `WilliJo` viene eliminato.  
  
```  
DROP LOGIN WilliJo;  
GO 
```  
 
  
## <a name="see-also"></a>Vedere anche  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  

