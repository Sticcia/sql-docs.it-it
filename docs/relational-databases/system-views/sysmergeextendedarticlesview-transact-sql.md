---
title: sysmergeextendedarticlesview (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergeextendedarticlesview
- sysmergeextendedarticlesview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeextendedarticlesview view
ms.assetid: bd5c8414-5292-41fd-80aa-b55a50ced7e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f91537880615fd7075db67ff8d89835944d1a79
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125881"
---
# <a name="sysmergeextendedarticlesview-transact-sql"></a>sysmergeextendedarticlesview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysmergeextendedarticlesview** espone articolo informazioni di visualizzazione. Questa vista è archiviata nel database di pubblicazione del server di pubblicazione e nel database di sottoscrizione del Sottoscrittore.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome dell'articolo.|  
|**type**|**tinyint**|Specifica il tipo di articolo. I possibili valori sono i seguenti:<br /><br /> **10** = tabella.<br /><br /> **32** = solo schema Proc.<br /><br /> **64** = solo schema della vista o solo schema della vista indicizzata.<br /><br /> **128** = solo schema funzione.<br /><br /> **160** = solo schema sinonimo.|  
|**objid**|**int**|Identificatore dell'oggetto del server di pubblicazione.|  
|**sync_objid**|**int**|Identificatore della vista che rappresenta il set di dati sincronizzato.|  
|**view_type**|**tinyint**|Tipo di vista:<br /><br /> **0** = non una vista, utilizzare tutti gli dell'oggetto di base.<br /><br /> **1** = vista permanente.<br /><br /> **2** = vista temporanea.|  
|**artid**|**uniqueidentifier**|Identificatore univoco per l'articolo specificato.|  
|**description**|**nvarchar(255)**|Breve descrizione dell'articolo.|  
|**pre_creation_command**|**tinyint**|Azione predefinita da eseguire quando viene creato l'articolo nel database di sottoscrizione:<br /><br /> **0** = Nessuna: se la tabella esiste già nel Sottoscrittore, viene eseguita alcuna azione.<br /><br /> **1** = rimozione: Elimina la tabella prima di crearne uno nuovo.<br /><br /> **2** = eliminazione specifica: esegue un'operazione di eliminazione in base alla clausola WHERE nel filtro di subset.<br /><br /> **3** = troncamento: equivale 2, ma Elimina pagine anziché righe. La clausola WHERE in questo caso non viene utilizzata.|  
|**pubid**|**uniqueidentifier**|ID della pubblicazione a cui appartiene l'articolo corrente.|  
|**nome alternativo**|**int**|Mapping di un nome alternativo per l'identificazione dell'articolo.|  
|**column_tracking**|**int**|Specifica se viene implementato il rilevamento a livello di colonna per l'articolo.|  
|**status**|**tinyint**|Specifica lo stato dell'articolo. I possibili valori sono i seguenti:<br /><br /> **1** = non sincronizzato: lo script di elaborazione iniziale per pubblicare la tabella verrà eseguito alla successiva esecuzione dell'agente Snapshot.<br /><br /> **2** = attivo: lo script di elaborazione iniziale per pubblicare la tabella è stato eseguito.<br /><br /> **5** = New_inactive: da aggiungere.<br /><br /> **6** = New_active: da aggiungere.|  
|**conflict_table**|**sysname**|Nome della tabella locale che include i record in conflitto per l'articolo corrente. Lo scopo di questa tabella è esclusivamente informativo. Il contenuto può essere modificato o eliminato da routine di risoluzione dei conflitti personalizzate oppure direttamente dall'amministratore.|  
|**creation_script**|**nvarchar(255)**|Script per la creazione dell'articolo.|  
|**conflict_script**|**nvarchar(255)**|Script dei conflitti dell'articolo.|  
|**article_resolver**|**nvarchar(255)**|Sistema di risoluzione dei conflitti a livello di riga personalizzato per l'articolo.|  
|**ins_conflict_proc**|**sysname**|Procedura utilizzata per la scrittura di conflitti in **conflict_table**.|  
|**insert_proc**|**sysname**|Procedura utilizzata dal sistema di risoluzione dei conflitti predefinito per l'inserimento di righe durante la sincronizzazione.|  
|**update_proc**|**sysname**|Procedura utilizzata dal sistema di risoluzione dei conflitti predefinito per l'aggiornamento di righe durante la sincronizzazione.|  
|**select_proc**|**sysname**|Nome di una stored procedure generata automaticamente utilizzata dall'agente di merge per l'implementazione di blocchi e l'individuazione di righe e colonne per un articolo.|  
|**schema_option**|**binary(8)**|Per i valori supportati *schema_option*, vedere [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Nome della tabella creata nel Sottoscrittore.|  
|**resolver_clsid**|**nvarchar(50)**|ID del sistema di risoluzione dei conflitti personalizzato.|  
|**subset_filterclause**|**nvarchar(1000)**|Clausola di filtro per l'articolo.|  
|**missing_col_count**|**int**|Numero di colonne mancanti.|  
|**missing_cols**|**varbinary(128)**|Mappa di bit delle colonne mancanti.|  
|**columns**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resolver_info**|**nvarchar(255)**|Archivio per informazioni aggiuntive necessarie ai sistemi di risoluzione dei conflitti personalizzati.|  
|**view_sel_proc**|**nvarchar(290)**|Nome di una stored procedure utilizzata dall'agente di merge per il popolamento iniziale di un articolo in una pubblicazione filtrata in modo dinamico e per l'enumerazione delle righe modificate in qualsiasi pubblicazione filtrata.|  
|**gen_cur**|**int**|Numero di generazione per modifiche locali della tabella di base di un articolo.|  
|**excluded_cols**|**varbinary(128)**|Mappa di bit delle colonne escluse dall'articolo quando viene inviato al Sottoscrittore.|  
|**excluded_col_count**|**int**|Numero di colonne escluse.|  
|**vertical_partition**|**int**|Specifica se in un articolo di tabella il filtraggio delle colonne è abilitato. **0** indica non è applicato alcun filtro verticale e pertanto pubblicate tutte le colonne.|  
|**identity_support**|**int**|Specifica se è abilitata la gestione automatica degli intervalli di valori Identity. **1** significa che degli intervalli di valori identity sono abilitato, e **0** significa che non vi sia alcuna identità di intervalli di valori supportati.|  
|**destination_owner**|**sysname**|Nome del proprietario dell'oggetto di destinazione.|  
|**before_image_objid**|**int**|ID dell'oggetto tabella di rilevamento. La tabella di rilevamento include valori di colonna chiave specifici se una pubblicazione è configurata in modo da abilitare le ottimizzazioni delle modifiche delle partizioni.|  
|**before_view_objid**|**int**|ID di oggetto di una tabella di vista. La vista è relativa a una tabella in cui viene tenuto traccia se una riga appartiene a un Sottoscrittore specifico prima di essere eliminata o aggiornata. Si applica solo quando una pubblicazione viene creata con *@keep_partition_changes*  =  **true**.|  
|**verify_resolver_signature**|**int**|Specifica se una firma digitale viene verificata o meno prima dell'utilizzo di un sistema di risoluzione dei conflitti in una replica di tipo merge:<br /><br /> **0** = firma non viene verificata.<br /><br /> **1** = firma viene verificata per stabilire se deriva da una fonte attendibile.|  
|**allow_interactive_resolver**|**bit**|Specifica se per un articolo l'utilizzo del sistema di risoluzione dei conflitti interattivo è attivato. **1** specifica che il sistema di risoluzione interattivo viene utilizzato per l'articolo.|  
|**fast_multicol_updateproc**|**bit**|Specifica se l'agente di merge è stato attivato per l'applicazione di modifiche a più colonne della stessa riga tramite una sola istruzione UPDATE:<br /><br /> **0** = esegue un'istruzione UPDATE distinta per ogni colonna modificata.<br /><br /> **1** = rilasciato nell'istruzione UPDATE che fa in modo che gli aggiornamenti a più colonne in un'unica istruzione.|  
|**check_permissions**|**int**|Mappa di bit delle autorizzazioni a livello di tabella che verranno verificate quando l'agente di merge applicherà le modifiche nel server di pubblicazione. *check_permissions* può avere uno dei valori seguenti:<br /><br /> **0x00** = le autorizzazioni non vengono controllate.<br /><br /> **0x10** = le autorizzazioni vengono verificate nel server di pubblicazione prima del caricamento gli inserimenti eseguiti in un sottoscrittore.<br /><br /> **0x20** = le autorizzazioni vengono verificate nel server di pubblicazione prima gli aggiornamenti apportati nel Sottoscrittore possono essere caricati.<br /><br /> **0x40** = le autorizzazioni vengono verificate nel server di pubblicazione prima del caricamento DELETE eseguite in un sottoscrittore.|  
|**maxversion_at_cleanup**|**int**|La generazione con il valore più alto per cui i metadati vengono rimossi.|  
|**processing_order**|**int**|Indica l'ordine di elaborazione degli articoli in una pubblicazione di tipo merge. dove il valore **0** indicava che l'articolo non è ordinato e gli articoli vengono elaborati in ordine dal valore più basso al più alto. Se due articoli hanno lo stesso valore, essi vengono elaborati simultaneamente. Per altre informazioni, vedere [delle proprietà di replica di tipo Merge specificare](../../relational-databases/replication/merge/specify-merge-replication-properties.md).|  
|**published_in_tran_pub**|**bit**|Indica che un articolo in una pubblicazione di tipo merge viene pubblicato anche in una pubblicazione transazionale.<br /><br /> **0** = articolo non viene pubblicato in un articolo transazionale.<br /><br /> **1** = articolo è pubblicato anche in un articolo transazionale.|  
|**upload_options**|**tinyiny**|Specifica se è possibile apportare modifiche nel Sottoscrittore o caricare modifiche dal Sottoscrittore. I possibili valori sono i seguenti.<br /><br /> **0** = non esistono restrizioni per gli aggiornamenti eseguiti nel Sottoscrittore; tutte le modifiche vengono caricate nel server di pubblicazione.<br /><br /> **1** = sono consentite modifiche nel Sottoscrittore, ma non vengono caricate nel server di pubblicazione.<br /><br /> **2** = non sono consentite modifiche nel Sottoscrittore.|  
|**lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**delete_proc**|**sysname**|Procedura utilizzata dal sistema di risoluzione dei conflitti predefinito per l'eliminazione di righe durante la sincronizzazione.|  
|**before_upd_view_objid**|**int**|ID della vista di una tabella prima degli aggiornamenti.|  
|**delete_tracking**|**bit**|Specifica se le eliminazioni vengono replicate.<br /><br /> **0** = le eliminazioni non vengono replicate.<br /><br /> **1** = le eliminazioni vengono replicate, ovvero il comportamento predefinito per la replica di tipo merge.<br /><br /> Quando il valore di *delete_tracking* viene **0**, le righe eliminate nel Sottoscrittore devono essere rimosse manualmente nel server di pubblicazione e le righe eliminate nel server di pubblicazione devono essere rimosse manualmente nel Sottoscrittore.<br /><br /> Nota: Un valore pari **0** comporta non convergenza.|  
|**compensate_for_errors**|**bit**|Specifica se devono essere eseguite azioni di compensazione quando vengono rilevati errori durante la sincronizzazione.<br /><br /> **0** = Compensating le azioni vengono disabilitate.<br /><br /> **1** = le modifiche che non possono essere applicate in un sottoscrittore o un server di pubblicazione generano sempre azioni di compensazione per annullare queste modifiche, ovvero il comportamento predefinito per la replica di tipo merge.<br /><br /> Nota: Un valore pari **0** comporta non convergenza.|  
|**pub_range**|**bigint**|Dimensioni dell'intervallo di valori Identity del server di pubblicazione.|  
|**Intervallo**|**bigint**|Dimensioni dei valori Identity consecutivi che verrebbero assegnati nei Sottoscrittori durante un intervento di regolazione.|  
|**soglia**|**int**|Percentuale di soglia dell'intervallo di valori Identity.|  
|**metadata_select_proc**|**sysname**|Nome della stored procedure generata automaticamente utilizzata per accedere a metadati nelle tabelle del sistema di replica di tipo merge.|  
|**stream_blob_columns**|**bit**|Specifica se viene utilizzata l'ottimizzazione del flusso di dati per la replica di colonne BLOB (Binary Large Object). **1** significa che l'ottimizzazione verrà tentata.|  
|**preserve_rowguidcol**|**bit**|Specifica se per la replica viene utilizzata una colonna rowguid esistente. Un valore pari **1** indica che viene utilizzata una colonna ROWGUIDCOL esistente. **0** significa che la replica aggiunto la colonna ROWGUIDCOL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica di &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [sysmergearticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md)  
  
  
