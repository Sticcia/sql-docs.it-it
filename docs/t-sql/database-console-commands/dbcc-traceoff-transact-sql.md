---
title: DBCC TRACEOFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRACEOFF_TSQL
- TRACEOFF
- DBCC TRACEOFF
- DBCC_TRACEOFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- trace flags [SQL Server], disabling
- DBCC TRACEOFF statement
- disabling trace flags
ms.assetid: 1379afba-6480-454b-9c65-5e64cb4f3415
author: pmasl
ms.author: umajay
manager: craigg
ms.openlocfilehash: b66d02c4f2b480f4238b87e190d63ee2682e86a7
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685634"
---
# <a name="dbcc-traceoff-transact-sql"></a>DBCC TRACEOFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Disabilita i flag di traccia specificati.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC TRACEOFF ( trace# [ ,...n ] [ , -1 ] ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
*trace#*  
Numero del flag di traccia da disabilitare.  
  
**-1**  
Disabilita globalmente i flag di traccia specificati.  
  
WITH NO_INFOMSGS  
Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="remarks"></a>Remarks  
I flag di traccia consentono di personalizzare alcune caratteristiche controllando il funzionamento dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
## <a name="result-sets"></a>Set di risultati  
DBCC TRACEOFF restituisce:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene disabilitato il flag di traccia `3205`.
  
```sql
DBCC TRACEOFF (3205);   
GO  
```  
  
Nell'esempio seguente viene prima disabilitato il flag di traccia `3205` a livello globale.
  
```sql
DBCC TRACEOFF (3205, -1);   
GO  
```  
  
Nell'esempio seguente vengono disabilitati i flag di traccia `3205` e `260` a livello globale.
  
```sql
DBCC TRACEOFF (3205, 260, -1);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC TRACEON &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)  
[DBCC TRACESTATUS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-tracestatus-transact-sql.md)  
[Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
