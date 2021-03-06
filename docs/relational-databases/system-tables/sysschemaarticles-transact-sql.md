---
title: sysschemaarticles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysschemaarticles_TSQL
- sysschemaarticles
dev_langs:
- TSQL
helpviewer_keywords:
- sysschemaarticles system table
ms.assetid: 67a1c039-c283-4a9c-bacc-b9b3973590c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 39444e0eaf9a44f48fc86b5d7f4595d63d1e9823
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822705"
---
# <a name="sysschemaarticles-transact-sql"></a>sysschemaarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Tiene traccia degli articoli relativi solo allo schema per pubblicazioni transazionali e snapshot. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|ID dell'articolo.|  
|**creation_script**|**nvarchar(255)**|Percorso e nome di uno script di schema dell'articolo utilizzato per la creazione della tabella di destinazione.|  
|**description**|**nvarchar(255)**|Voce descrittiva per l'articolo.|  
|**dest_object**|**sysname**|Nome dell'oggetto del database di sottoscrizione se l'articolo è relativo solo allo schema, quali articoli di stored procedure, viste e funzioni definite dall'utente.|  
|**name**|**sysname**|Nome dell'articolo relativo solo allo schema in una pubblicazione.|  
|**objid**|**int**|Identificatore dell'oggetto di base dell'articolo. Può corrispondere all'identificatore di oggetto di una procedura, vista, vista indicizzata o funzione definita dall'utente.|  
|**pubid**|**int**|ID della pubblicazione.|  
|**pre_creation_cmd**|**tinyint**|Specifica l'azione eseguita dal sistema se nel Sottoscrittore viene rilevato un oggetto esistente avente lo stesso nome durante l'applicazione dello snapshot per l'articolo:<br /><br /> **0** = nothing.<br /><br /> **1** = eliminazione della tabella di destinazione.<br /><br /> **2** = tabella di destinazione di rilascio.<br /><br /> **3** = tabella di destinazione del troncamento.|  
|**status**|**int**|Mappa di bit utilizzata per indicare lo stato dell'articolo.|  
|**type**|**tinyint**|Tipo di articolo relativo solo allo schema:<br /><br /> **32** = Stored procedure.<br /><br /> **64** = vista o vista indicizzata. <br /><br /> **96** = funzione di aggregazione.<br /><br /> **128** = funzione.|  
|**schema_option**|**binary(8)**|Maschera di bit dell'opzione di creazione dello schema per l'articolo specificato. Imposta la creazione automatica della stored procedure nel database di destinazione per ogni sintassi CALL/MCALL/XCALL e può corrispondere al risultato dell'applicazione dell'operatore OR logico bit per bit a uno dei valori seguenti:<br /><br /> **0x00** = disabilita la creazione di script per l'agente Snapshot e utilizza *creation_script*.<br /><br /> **0x01** = genera la creazione di oggetti (CREATE TABLE, CREATE PROCEDURE e così via). Corrisponde al valore predefinito per gli articoli di stored procedure.<br /><br /> **0x02** = genera stored procedure personalizzate per l'articolo, se definito.<br /><br /> **0x10** = genera un indice cluster corrispondente.<br /><br /> **0x20** = converte i tipi di dati definito dall'utente per i tipi di dati di base.<br /><br /> **0x40**= genera uno o più indici non cluster corrispondenti.<br /><br /> **0x80**= include l'integrità referenziale dichiarata nelle chiavi primarie.<br /><br /> **0x73** = genera l'istruzione CREATE TABLE, crea indici cluster e non cluster, converte i tipi di dati definito dall'utente in tipi di dati di base e genera gli script di stored procedure personalizzata da applicare nel Sottoscrittore. Corrisponde al valore predefinito per tutti gli articoli, tranne gli articoli di stored procedure.<br /><br /> **0x100**= i trigger utente replicati in un articolo di tabella, se definito.<br /><br /> **0x200**= replica i vincoli di chiave esterni. Se la tabella con riferimenti non fa parte di una pubblicazione, i vincoli FOREIGN KEY di una tabella pubblicata non vengono replicati.<br /><br /> **0x400**= replica i vincoli check.<br /><br /> **0x800**= replica le impostazioni predefinite.<br /><br /> **0x1000**= replica le regole di confronto a livello di colonna.<br /><br /> **0x2000**= replica le proprietà estese associate oggetto di origine dell'articolo pubblicato.<br /><br /> **0x4000**= replica le chiavi univoche se definite in un articolo di tabella.<br /><br /> **0x8000**= chiave primaria a replica e le chiavi univoche di un articolo di tabella come vincoli tramite istruzioni ALTER TABLE.|  
|**dest_owner**|**sysname**|Proprietario della tabella nel database di destinazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
