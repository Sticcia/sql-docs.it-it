---
title: GRANT - autorizzazioni per oggetti di sistema (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], system objects
- system objects [SQL Server]
- GRANT statement, system objects
ms.assetid: 9d4e89f4-478f-419a-8b50-b096771e3880
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8925e71fb7ed3ea6d53f29b438602cae65820fa6
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327612"
---
# <a name="grant-system-object-permissions-transact-sql"></a>GRANT - autorizzazioni per oggetti di sistema (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede le autorizzazioni per oggetti di sistema come stored procedure di sistema, stored procedure estese, funzioni e viste.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GRANT { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>Argomenti  
 [ sys.] .  
 Il qualificatore sys è obbligatorio solo per riferimenti a viste del catalogo e viste a gestione dinamica.  
  
 *system_object*  
 Specifica l'oggetto per cui viene concessa l'autorizzazione.  
  
 *principal*  
 Specifica l'entità a cui viene concessa l'autorizzazione.  
  
## <a name="remarks"></a>Remarks  
 È possibile utilizzare questa istruzione per concedere le autorizzazioni per particolari stored procedure, stored procedure estese, funzioni con valori di tabella, funzioni scalari, viste, viste del catalogo, viste di compatibilità, viste INFORMATION_SCHEMA, viste a gestione dinamica e tabelle di sistema installate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ognuno di questi oggetti di sistema esiste come record univoco nel database delle risorse del server (mssqlsystemresource). Il database delle risorse è di sola lettura. Un collegamento all'oggetto è disponibile in forma di record nello schema sys di tutti i database. È possibile concedere, negare o revocare le autorizzazioni per l'esecuzione o la selezione di un oggetto di sistema.  
  
 La concessione dell'autorizzazione per l'esecuzione o la selezione di un oggetto non include necessariamente tutte le autorizzazioni necessarie per l'utilizzo dell'oggetto. La maggior parte degli oggetti esegue operazioni per cui sono richieste autorizzazioni aggiuntive. Ad esempio, un utente a cui viene concessa l'autorizzazione EXECUTE per sp_addlinkedserver non potrà creare un server collegato a meno che non sia anche membro del ruolo predefinito del server sysadmin.  
  
 I nomi di procedure non qualificati vengono risolti dal processo predefinito di risoluzione dei nomi nel database delle risorse. Il qualificatore sys è pertanto obbligatorio solo quando si specificano viste del catalogo e viste a gestione dinamica.  
  
 Non è supportata la concessione di autorizzazioni per i trigger e le colonne di oggetti di sistema.  
  
 Le autorizzazioni per gli oggetti di sistema vengono mantenute in caso di aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Gli oggetti di sistema sono visibili nella vista del catalogo [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) . Le autorizzazioni per gli oggetti di sistema sono visibili nella vista del catalogo [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) nel database master.  
  
 La query seguente restituisce informazioni sulle autorizzazioni degli oggetti di sistema:  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-granting-select-permission-on-a-view"></a>A. Concessione dell'autorizzazione SELECT per una vista  
 Nell'esempio seguente viene concessa all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `Sylvester1` l'autorizzazione per la selezione di una vista che elenca gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nell'esempio viene poi concessa l'autorizzazione aggiuntiva necessaria per la visualizzazione dei metadati relativi agli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di cui l'utente non è proprietario.  
  
```  
USE AdventureWorks2012;  
GRANT SELECT ON sys.sql_logins TO Sylvester1;  
GRANT VIEW SERVER STATE to Sylvester1;  
GO  
```  
  
### <a name="b-granting-execute-permission-on-an-extended-stored-procedure"></a>b. Concessione dell'autorizzazione EXECUTE per una stored procedure estesa  
 Nell'esempio seguente viene concessa l'autorizzazione `EXECUTE` per `xp_readmail` a `Sylvester1`.  
  
```  
GRANT EXECUTE ON xp_readmail TO Sylvester1;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.system_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [REVOKE - autorizzazioni per oggetti di sistema &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)   
 [DENY - autorizzazioni per oggetti di sistema &#40;Transact-SQL&#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  
