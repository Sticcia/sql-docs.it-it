---
title: Precedenza dei tipi di dati (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e29b874a84001dcd3d25a46bb07f48dd287ab547
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407561"
---
# <a name="data-type-precedence-transact-sql"></a>Precedenza dei tipi di dati (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Quando un operatore combina espressioni di tipi di dati diversi, il tipo di dati con precedenza inferiore viene per prima cosa convertito nel tipo di dati con precedenza superiore. Se la conversione non è una conversione implicita supportata, viene generato un errore. Se le espressioni dell'operando combinate dall'operatore hanno lo stesso tipo di dati, questo sarà il tipo di dati del risultato dell'operazione.
  
Per i tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza l'ordine di precedenza seguente:
  
1.  Tipi di dati definiti dall'utente (superiore)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **data**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (incluso **nvarchar(max)** )  
1. **nchar**  
1. **varchar** (incluso **varchar(max)** )  
1. **char**  
1. **varbinary** (incluso **varbinary(max)** )  
1. **binary** (inferiore)  
  
## <a name="see-also"></a>Vedere anche
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  