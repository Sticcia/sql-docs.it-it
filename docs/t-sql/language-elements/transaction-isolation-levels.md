---
title: Livelli di isolamento delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0acd70fad20d0ad1c2727f93da52b2e938ee21fd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="transaction-isolation-levels"></a>Livelli di isolamento delle transazioni
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non garantisce che gli hint di blocco verranno rispettati nelle query che accedono ai metadati tramite viste del catalogo, viste di compatibilità, viste degli schemi delle informazioni e funzioni predefinite di creazione di metadati.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] rispetta internamente solo il livello di isolamento READ COMMITTED per l'accesso ai metadati. Se una transazione utilizza, ad esempio, un livello di isolamento SERIALIZABLE e nella transazione viene eseguito un tentativo di accedere ai metadati utilizzando le viste del catalogo o le funzioni predefinite di creazione di metadati, le query verranno eseguite fino a quando non vengono completate come READ COMMITTED. Nel livello di isolamento dello snapshot, tuttavia, l'accesso ai metadati potrebbe non riuscire a causa di operazioni DDL simultanee. Questo comportamento si verifica perché ai metadati non viene applicato il controllo delle versioni. Per questo motivo, l'accesso agli elementi indicati di seguito nel livello di isolamento dello snapshot potrebbe non riuscire:  
  
-   Viste del catalogo  
  
-   Viste di compatibilità  
  
-   Viste degli schemi delle informazioni  
  
-   Funzioni predefinite di creazione dei metadati  
  
-   **sp_help** gruppo di stored procedure  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Procedure di catalogo di Native Client  
  
-   Viste e funzioni a gestione dinamica  
  
 Per ulteriori informazioni sui livelli di isolamento, vedere [SET TRANSACTION ISOLATION LEVEL &#40; Transact-SQL &#41; ](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 Nella tabella seguente è incluso un riepilogo sull'accesso ai metadati in livelli di isolamento diversi.  
  
|Livello di isolamento|Supportato|Rispettato|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|No|Rispetto non garantito|  
|READ COMMITTED|Sì|Sì|  
|REPEATABLE READ|No|No|  
|SNAPSHOT ISOLATION|No|No|  
|SERIALIZABLE|No|No|  
  
  