---
title: Autorizzazioni certificato GRANT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/12/2017
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
- granting permissions [SQL Server], certificates
- certificates [SQL Server], permissions
- permissions [SQL Server], certificates
- GRANT statement, certificates
ms.assetid: 77270245-a24b-4a20-b481-e6a5ea05b499
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06cd8f6b6b9e6a05326bad54319961a2120b979d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="grant-certificate-permissions-transact-sql"></a>GRANT (autorizzazioni per certificati) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Concede le autorizzazioni per un certificato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```
GRANT permission  [ ,...n ]    
    ON CERTIFICATE :: certificate_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere concessa per un certificato. Vedere l'elenco riportato di seguito.  
  
 CERTIFICATO ON **::***nome_certificato*  
 Specifica il certificato a cui viene concessa l'autorizzazione. Il qualificatore di ambito "::" è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene concessa l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
AS *granting_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di concedere l'autorizzazione. I tipi validi sono:  
  
-   utente del database  
-   ruolo del database  
-   ruolo dell'applicazione  
-   utente del database sul quale viene eseguito il mapping a un account di accesso di Windows  
-   utente del database sul quale viene eseguito il mapping a un gruppo di Windows  
-   utente del database sul quale viene eseguito il mapping a un certificato  
-   utente del database mappato a una chiave asimmetrica  
-   utente del database non mappato ad alcuna entità server.  
  
## <a name="remarks"></a>Osservazioni  
 Un certificato è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Di seguito sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un certificato, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del certificato|Autorizzazione del certificato in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CERTIFICATE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 L'utente che concede le autorizzazioni (o l'entità specificata con l'opzione AS) deve disporre della relativa autorizzazione con GRANT OPTION oppure di un'autorizzazione di livello superiore che include l'autorizzazione che viene concessa.  
  
 Se si usano l'opzione AS, sono previsti questi requisiti aggiuntivi.  
  
|AS *granting_principal*|Autorizzazione aggiuntiva necessaria|  
|------------------------------|------------------------------------|  
|Utente del database|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un gruppo di Windows|L'appartenenza al gruppo di Windows, appartenenza al gruppo il **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a un certificato|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica|L'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza di **db_owner** o l'appartenenza al ruolo il **sysadmin** ruolo predefinito del server.|  
|Utente del database di cui non è stato eseguito il mapping ad alcuna entità server|L'autorizzazione IMPERSONATE per l'utente, l'appartenenza al **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin** ruolo predefinito del server.|  
|Ruolo del database|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
|Ruolo applicazione|L'autorizzazione ALTER per il ruolo, appartenenza al gruppo di **db_securityadmin** ruolo predefinito del database, l'appartenenza al **db_owner** o l'appartenenza al ruolo di **sysadmin**ruolo predefinito del server.|  
  
 I proprietari degli oggetti possono concedere autorizzazioni per gli oggetti di cui sono proprietari. Le entità con l'autorizzazione CONTROL per un'entità a sicurezza diretta possono concedere l'autorizzazione per quella entità.  
  
 Gli utenti che dispongono dell'autorizzazione CONTROL SERVER, ad esempio i membri del **sysadmin** ruolo predefinito del server, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel server. Gli utenti che dispongono dell'autorizzazione CONTROL per un database, ad esempio i membri del **db_owner** ruolo predefinito del database, possono concedere qualsiasi autorizzazione per qualsiasi entità a protezione diretta nel database. Gli utenti che dispongono dell'autorizzazione CONTROL in uno schema, possono concedere qualsiasi autorizzazione per qualsiasi oggetto all'interno dello schema.  
  
## <a name="see-also"></a>Vedere anche  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
