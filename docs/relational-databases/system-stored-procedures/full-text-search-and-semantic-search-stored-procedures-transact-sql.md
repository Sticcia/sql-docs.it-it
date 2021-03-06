---
title: Ricerca full-Text e semantica Stored procedure (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], stored procedures
- full-text search [SQL Server], stored procedures
- full-text catalogs [SQL Server], stored procedures
- system stored procedures [SQL Server], full-text search
ms.assetid: 0d185a16-2b16-4958-884f-efe675e2e551
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c3757941531eba0238df03c72b5653147496443b
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983239"
---
# <a name="full-text-search-and-semantic-search-stored-procedures-transact-sql"></a>Stored procedure per ricerca full-text e ricerca semantica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta le seguenti stored procedure di sistema che consentono di implementare ed eseguire query su indici full-text e semantici.  
  
## <a name="full-text-search-stored-procedures"></a>Stored procedure per ricerche full-text  
 [sp_fulltext_catalog](../../relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql.md)  
 Consente di creare ed eliminare un catalogo full-text e di avviare e arrestare l'azione di indicizzazione per un catalogo. È possibile creare più cataloghi full-text per ogni database.  
  
 [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Uso [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md), [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md), e [DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) invece.  
  
 [sp_fulltext_column](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)  
 Specifica se una determinata colonna di una tabella viene inclusa o meno nell'indicizzazione full-text.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Uso [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) invece.  
  
 [sp_fulltext_database](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)  
 Non ha alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive ed è supportata solo per la compatibilità con le versioni precedenti.  
  
 [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 [sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)  
 Restituisce i mapping tra gli identificatori del documento (**DocId**s) e valori chiave full-text.  
  
 [sp_fulltext_load_thesaurus_file](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)  
 Analizza e carica i dati da un file del thesaurus aggiornato che corrisponde a un LCID e comporta la ricompilazione di query full-text che utilizzano il thesaurus.  
  
 [sp_fulltext_pendingchanges](../../relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql.md)  
 Restituisce modifiche non ancora elaborate, ad esempio inserimenti, aggiornamenti ed eliminazioni in sospeso, per una tabella specificata che utilizza il rilevamento delle modifiche.  
  
 [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
 Modifica le proprietà di ricerca full-text del server per SQL Server.  
  
 [sp_fulltext_table](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)  
 Contrassegna una tabella per l'indicizzazione full-text oppure elimina tale contrassegno.  
  
 [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare in alternativa [CREATE FULLTEXT INDEX](../../t-sql/statements/create-fulltext-index-transact-sql.md), [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)e [DROP FULLTEXT INDEX](../../t-sql/statements/drop-fulltext-index-transact-sql.md) .  
  
 [sp_help_fulltext_catalog_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql.md)  
 Viene restituito un elenco di tutti i componenti (filtri, word breaker e gestori di protocollo) utilizzati per tutti i cataloghi full-text nel database corrente.  
  
 [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 [sp_help_fulltext_catalogs](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)  
 Restituisce l'ID, il nome, la directory radice, lo stato e il numero di tabelle indicizzate full-text per il catalogo full-text specificato.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare la [Sys. fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md) invece la vista del catalogo.  
  
 [sp_help_fulltext_catalogs_cursor](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)  
 Utilizza un cursore per restituire l'ID, il nome, la directory radice, lo stato e il numero di tabelle indicizzate full-text per il catalogo full-text specificato.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare la [Sys. fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md) invece la vista del catalogo.  
  
 [sp_help_fulltext_columns](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)  
 Restituisce le colonne impostate per l'indicizzazione full-text.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare la [Sys. fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) invece la vista del catalogo.  
  
 [sp_help_fulltext_columns_cursor](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)  
 Utilizza un cursore per restituire le colonne impostate per l'indicizzazione full-text.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare la [Sys. fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) invece la vista del catalogo.  
  
 [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
 Restituisce informazioni per i word breaker, il filtro e i gestori di protocollo registrati, nonché l'elenco degli identificatori dei database e dei cataloghi full-text che hanno utilizzato un componente specificato.  
  
 [sp_help_fulltext_tables](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)  
 Restituisce un elenco delle tabelle registrate per l'indicizzazione full-text.  
  
 [sp_help_fulltext_tables_cursor](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)  
 Restituisce un elenco delle tabelle registrate per l'indicizzazione full-text.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare la [Sys. fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) invece la vista del catalogo.  
  
## <a name="semantic-search-stored-procedures"></a>Stored procedure per la ricerca semantica  
 [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md)  
 Consente di registrare un database di statistiche lingua semantica prepopolato nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md)  
 Consente di annullare la registrazione di un database di statistiche lingua semantica esistente dall'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e di eliminare tutti i metadati associati.  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca full-Text e semantica viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)   
 [Funzioni e viste a gestione dinamica la ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)  
  
  
