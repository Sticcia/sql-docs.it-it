---
title: REFERENTIAL_CONSTRAINTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- REFERENTIAL_CONSTRAINTS
- REFERENTIAL_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.REFERENTIAL_CONSTRAINTS view
- REFERENTIAL_CONSTRAINTS view
ms.assetid: 5d358f18-0a85-4b55-af4b-98d5f4cd1020
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f0cb0110e6f2cc047ca5db5f2813b250567573fc
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132141"
---
# <a name="referentialconstraints-transact-sql"></a>REFERENTIAL_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni vincolo FOREIGN KEY del database corrente. Questa vista degli schemi delle informazioni restituisce informazioni sugli oggetti per i quali l'utente dispone di autorizzazioni.  
  
 Per recuperare informazioni da queste viste, specificare il nome completo del **INFORMATION_SCHEMA.** _view_name_.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Qualificatore del vincolo.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene il vincolo.<br /><br /> **&#42;&#42;Importante &#42; &#42;**  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**CONSTRAINT_NAME**|**sysname**|Nome del vincolo.|  
|**UNIQUE_CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Qualificatore del vincolo UNIQUE.|  
|**UNIQUE_CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene il vincolo UNIQUE.<br /><br /> **&#42;&#42;Importante &#42; &#42;**  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**UNIQUE_CONSTRAINT_NAME**|**sysname**|Vincolo UNIQUE.|  
|**MATCH_OPTION**|**varchar (** 7 **)**|Condizioni referenziali di corrispondenza con il vincolo. Restituisce sempre SIMPLE, a indicare che non è definita alcuna corrispondenza. La condizione viene considerata una corrispondenza se si verifica una delle situazioni seguenti:<br /><br /> Almeno un valore della colonna chiave esterna è NULL.<br /><br /> Tutti i valori della colonna chiave esterna sono diversi da NULL e una riga della tabella della chiave primaria include la stessa chiave.|  
|**UPDATE_RULE**|**varchar (** 11 **)**|Azione eseguita se un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] viola l'integrità referenziale definita dal vincolo. Restituisce una delle operazioni seguenti: <br />NO ACTION<br />CASCADE<br />SET NULL<br />SET DEFAULT<br /><br /> Se nell'opzione ON UPDATE si specifica NO ACTION per il vincolo, l'aggiornamento della chiave primaria a cui viene fatto riferimento nel vincolo non viene propagato alla chiave esterna. Se l'aggiornamento di una chiave primaria comporta una violazione dell'integrità referenziale perché almeno una chiave esterna contiene lo stesso valore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non modifica le tabelle padre e di riferimento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genererà inoltre un errore.<br /><br /> Se nell'opzione ON UPDATE si specifica CASCADE per il vincolo, tutte le modifiche apportate al valore della chiave primaria vengono propagate automaticamente al valore della chiave esterna.|  
|**DELETE_RULE**|**varchar (** 11 **)**|Azione eseguita se un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] viola l'integrità referenziale definita dal vincolo. Restituisce una delle operazioni seguenti: <br />NO ACTION<br />CASCADE<br />SET NULL<br />SET DEFAULT<br /><br /> Se in ON DELETE si specifica NO ACTION per il vincolo, l'eliminazione nella chiave primaria a cui viene fatto riferimento nel vincolo non viene propagata alla chiave esterna. Se l'eliminazione di una chiave primaria comporta una violazione dell'integrità referenziale perché almeno una chiave esterna contiene lo stesso valore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non modifica le tabelle padre e di riferimento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genererà inoltre un errore.<br /><br /> Se nell'opzione ON DELETE si specifica CASCADE per il vincolo, tutte le modifiche apportate al valore della chiave primaria vengono propagate automaticamente al valore della chiave esterna.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys. Foreign_Keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)  
  
  
