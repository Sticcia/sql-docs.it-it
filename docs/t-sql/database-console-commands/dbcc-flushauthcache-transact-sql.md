---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 16267d2af81e3338bb04f5f548e2f9d14d1d4186
ms.sourcegitcommit: 009bee6f66142c48477849ee03d5177bcc3b6380
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56231008"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Svuota la cache di autenticazione del database che contiene le informazioni su account di accesso e regole del firewall per il database utente corrente nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Questa istruzione non si applica al database master logico perché il database master contiene lo spazio fisico di archiviazione per le informazioni su account di accesso e regole del firewall. L'utente che esegue l'istruzione e gli altri utenti attualmente connessi mantengono la connessione. DBCC FLUSHAUTHCACHE non è attualmente supportato per [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].
 
![Icona di collegamento a un articolo](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un articolo")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
Nessuna.
  
## <a name="remarks"></a>Remarks  
La cache di autenticazione crea una copia degli account di accesso e delle regole firewall del server archiviati nel database master e li inserisce in memoria nel database utente.  Poiché le informazioni relative agli utenti di database indipendente sono già archiviate nel database utente, gli utenti di database indipendente non fanno parte della cache di autenticazione.
Le connessioni continuamente attive al [!INCLUDE[ssSDS](../../includes/sssds-md.md)] richiedono la riautorizzazione (eseguita dal [!INCLUDE[ssDE](../../includes/ssde-md.md)]) almeno ogni 10 ore. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta la riautorizzazione usando la password inviata originariamente e non richiede alcun input da parte dell'utente. Per motivi di prestazioni, quando si reimposta una password nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)], la connessione non verrà nuovamente autenticata, anche se la connessione viene reimpostata a causa del pool di connessioni. Questo comportamento è diverso da quello dell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se la password è stata cambiata dopo l'autorizzazione iniziale della connessione, è necessario terminare la connessione e stabilirne una nuova usando la nuova password. Un utente con l'autorizzazione KILL DATABASE CONNECTION può terminare in modo esplicito una connessione al [!INCLUDE[ssSDS](../../includes/sssds-md.md)] usando il comando [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md).
  
## <a name="permissions"></a>Permissions  
Richiede l'account amministratore del [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
## <a name="example"></a>Esempio  
L'istruzione seguente consente di cancellare la cache di autenticazione per il database corrente.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
