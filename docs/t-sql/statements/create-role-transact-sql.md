---
title: CREATE ROLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE ROLE
- DATABASE ROLE
- ROLE_TSQL
- DATABASE_ROLE_TSQL
- CREATE_ROLE_TSQL
- CREATE DATABASE ROLE
- ROLE
- CREATE_DATABASE_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], creating
- CREATE DATABASE ROLE statement
- roles [SQL Server], creating
- CREATE ROLE statement
ms.assetid: b0cd54ad-e81d-4d71-acec-8a6d7261ca08
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c1dc06f65e1c724466154197d156517b2c72827f
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54326662"
---
# <a name="create-role-transact-sql"></a>CREATE ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crea un nuovo ruolo di database nel database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE ROLE role_name [ AUTHORIZATION owner_name ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *role_name*  
 Nome del ruolo che si desidera creare.  
  
 AUTHORIZATION *owner_name*  
 Utente o ruolo del database che sarà proprietario del nuovo ruolo. Se non viene specificato alcun utente, il ruolo sarà di proprietà dell'utente che esegue l'istruzione CREATE ROLE.  
  
## <a name="remarks"></a>Remarks  
 I ruoli sono entità a protezione diretta a livello di database. Dopo aver creato un ruolo, configurare le autorizzazioni a livello di database per il ruolo tramite GRANT, DENY e REVOKE. Per aggiungere membri a un ruolo del database, usare [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md). Per altre informazioni, vedere [Ruoli a livello di database](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 I ruoli del database sono visibili nelle viste del catalogo sys.database_role_members e sys.database_principals.  
  
 Per informazioni sulla progettazione di un sistema di autorizzazioni, vedere [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione **CREATE ROLE** per il database o l'appartenenza al ruolo predefinito del database **db_securityadmin**. Se si usa l'opzione **AUTHORIZATION**, sono necessarie anche le autorizzazioni seguenti:  
  
-   Per assegnare la proprietà di un ruolo a un altro utente, è richiesta l'autorizzazione IMPERSONATE per quell'utente.  
  
-   Per assegnare la proprietà di un ruolo a un altro ruolo, è richiesta l'appartenenza al ruolo destinatario oppure l'autorizzazione ALTER per tale ruolo.  
  
-   Per assegnare la proprietà di un ruolo a un ruolo applicazione, è richiesta l'autorizzazione ALTER per il ruolo applicazione.  
  
## <a name="examples"></a>Esempi  
Tutti gli esempi seguenti usano il database AdventureWorks.   

### <a name="a-creating-a-database-role-that-is-owned-by-a-database-user"></a>A. Creazione di un ruolo del database di proprietà di un utente del database  
 Nell'esempio seguente viene creato il ruolo del database `buyers` di proprietà dell'utente `BenMiller`.  
  
```  
CREATE ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-database-role-that-is-owned-by-a-fixed-database-role"></a>b. Creazione di un ruolo del database di proprietà di un ruolo predefinito del database  
 Nell'esempio seguente viene creato il ruolo del database `auditors` di proprietà del ruolo predefinito del database `db_securityadmin`.  
  
```  
CREATE ROLE auditors AUTHORIZATION db_securityadmin;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Introduzione alle autorizzazioni del motore di database](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  


