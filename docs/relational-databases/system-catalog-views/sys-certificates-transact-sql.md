---
title: Sys. Certificates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- certificates
- certificates_TSQL
- sys.certificates_TSQL
- sys.certificates
dev_langs:
- TSQL
helpviewer_keywords:
- sys.certificates catalog view
ms.assetid: e5046102-a65c-401e-b80d-05636884dec9
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 634fbc4ddd96fd407aa124c98ae2b55897edaa71
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391224"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni certificato nel database.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del certificato. Valore univoco all'interno del database.|  
|**certificate_id**|**int**|ID del certificato. Valore univoco all'interno del database.|  
|**principal_id**|**int**|ID dell'entità di database che possiede il certificato.|  
|**pvt_key_encryption_type**|**char(2)**|Tipo di crittografia utilizzata per la chiave.<br /><br /> NA = Nessuna chiave privata per il certificato<br /><br /> MK = La chiave privata è crittografata tramite la chiave master<br /><br /> PW = La chiave privata è crittografata tramite una password definita dall'utente<br /><br /> SK = La chiave privata è crittografata tramite la chiave master del servizio.|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Descrizione della modalità di crittografia utilizzata per la chiave privata.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|Se è 1, questo certificato è utilizzato per avviare i dialoghi dei servizi crittografati.|  
|**issuer_name**|**nvarchar(442)**|Nome dell'autorità emittente del certificato.|  
|**cert_serial_number**|**nvarchar(64)**|Numero di serie del certificato.|  
|**sid**|**varbinary(85)**|SID dell'account di accesso del certificato.|  
|**string_sid**|**nvarchar(128)**|Rappresentazione della stringa del SID dell'account di accesso per il certificato|  
|**subject**|**nvarchar(4000)**|Oggetto del certificato.|  
|**expiry_date**|**datetime**|Data di scadenza del certificato.|  
|**start_date**|**datetime**|Data di inizio di validità del certificato.|  
|**Identificazione personale**|**varbinary(32)**|Hash SHA-1 del certificato. L'hash SHA-1 è univoco globale.|  
|**attested_by**|**nvarchar(260)**|Riservato per l'utilizzo nel sistema.|  
|pvt_key_last_backup_date|**datetime**|Data e ora che ultima esportazione della chiave privata del certificato.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
