---
title: UPDATE() (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UPDATE()_TSQL
- UPDATE()
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], UPDATE function
- testing column updates
- UPDATE function
- UPDATE() function
- detecting changes
- columns [SQL Server], change detection
- UPDATE statement [SQL Server], UPDATE function
- verifying column updates
- checking column updates
ms.assetid: 8e3be25b-2e3b-4d1f-a610-dcbbd8d72084
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9677ef3717fb83bdaf6ea108279b98a6598adced
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53980347"
---
# <a name="update---trigger-functions-transact-sql"></a>UPDATE - Funzioni di trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un valore booleano che indica se sono stati effettuati tentativi di esecuzione dell'operazione INSERT o UPDATE su una colonna specifica di una tabella o vista. UPDATE() viene utilizzata in qualsiasi punto all'interno del corpo di un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT o UPDATE per controllare se il trigger deve eseguire operazioni specifiche.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>Argomenti  
 *column*  
 Nome della colonna in cui verificare se viene eseguita un'operazione INSERT o UPDATE. Poiché il nome della tabella viene specificato nella clausola ON del trigger, non includere il nome della tabella prima del nome della colonna. Il [tipo di dati](../../t-sql/data-types/data-types-transact-sql.md) della colonna può essere uno dei tipi supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo contesto non è tuttavia possibile utilizzare colonne calcolate.  
  
## <a name="return-types"></a>Tipi restituiti  
 Boolean  
  
## <a name="remarks"></a>Remarks  
 UPDATE() restituisce TRUE indipendentemente dall'esito del tentativo di esecuzione dell'operazione INSERT o UPDATE.  
  
 Per eseguire la verifica di un'azione INSERT o UPDATE in più di una colonna, specificare una clausola UPDATE(*column*) separata a partire dalla prima colonna. In alternativa, è possibile eseguire la stessa verifica utilizzando COLUMNS_UPDATED. In questo caso viene restituito uno schema di bit che indica le colonne inserite o aggiornate.  
  
 In operazioni INSERT l'opzione IF UPDATE restituisce il valore TRUE in quanto nelle colonne vengono inseriti valori espliciti o impliciti (NULL).  
  
> [!NOTE]  
>  La clausola IF UPDATE(*column*) funziona esattamente come una clausola IF, IF...ELSE o WHILE e può usare il blocco BEGIN...END. Per altre informazioni, vedere [Elementi del linguaggio per il controllo di flusso &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md).  
  
 UPDATE(*column*) può essere usata in qualsiasi punto del corpo di un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un trigger che stampa un messaggio nel client in corrispondenza di un tentativo di aggiornamento della la colonna `StateProvinceID` o `PostalCode` della tabella `Address`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
      WHERE name = 'reminder' AND type = 'TR')  
   DROP TRIGGER Person.reminder;  
GO  
CREATE TRIGGER reminder  
ON Person.Address  
AFTER UPDATE   
AS   
IF ( UPDATE (StateProvinceID) OR UPDATE (PostalCode) )  
BEGIN  
RAISERROR (50009, 16, 10)  
END;  
GO  
-- Test the trigger.  
UPDATE Person.Address  
SET PostalCode = 99999  
WHERE PostalCode = '12345';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [COLUMNS_UPDATED &#40;Transact-SQL&#41;](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
