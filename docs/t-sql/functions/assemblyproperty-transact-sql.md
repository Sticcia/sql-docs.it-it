---
title: ASSEMBLYPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 468364203d169e6987322edbb99f0b2cea863fec
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696002"
---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Questa funzione restituisce informazioni su una proprietà di un assembly.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>Argomenti  
*assembly_name*  
Nome dell'assembly.
  
*property_name*  
Nome di una proprietà su cui recuperare informazioni. *property_name* può avere uno dei valori seguenti:
  
|valore|Descrizione|  
|---|---|
|**CultureInfo**|Impostazioni locali dell'assembly.|  
|**PublicKey**|Chiave pubblica o token di chiave pubblica dell'assembly.|  
|**MvID**|Numero completo di identificazione della versione dell'assembly generato dal compilatore.|  
|**VersionMajor**|Parte principale (prima parte) del numero di identificazione della versione dell'assembly composto da quattro parti.|  
|**VersionMinor**|Parte secondaria (seconda parte) del numero di identificazione della versione dell'assembly composto da quattro parti.|  
|**VersionBuild**|Parte relativa alla build (terza parte) del numero di identificazione della versione dell'assembly composto da quattro parti.|  
|**VersionRevision**|Parte relativa alla revisione (quarta parte) del numero di identificazione della versione dell'assembly composto da quattro parti.|  
|**SimpleName**|Nome semplice dell'assembly.|  
|**Architettura**|Architettura del processore dell'assembly.|  
|**CLRName**|Stringa canonica che codifica il nome semplice, il numero di versione, le impostazioni internazionali, la chiave pubblica e l'architettura dell'assembly. Questo valore identifica in modo univoco l'assembly sul lato CLR (Common Language Runtime).|  
  
## <a name="return-type"></a>Tipo restituito
**sql_variant**
  
## <a name="examples"></a>Esempi  
Questo esempio presuppone che un assembly `HelloWorld` sia registrato nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Per altre informazioni, vedere [Esempio Hello World](https://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>Vedere anche
[CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
