---
title: dbo.sysdac_instances (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysdac_instances_TSQL
- sysdac_instances
- sysdac_instances_TSQL
- dbo.sysdac_instances
dev_langs: TSQL
helpviewer_keywords:
- dbo.sysdac_instances
- sysdac_instances
ms.assetid: 28285f3d-3889-439f-8b24-3bdef08e46b4
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 197eb0d8887f56d77c5851403f2914712a757bbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="data-tier-application-views---dbosysdacinstances"></a>Visualizzazioni di applicazione livello dati - dbo.sysdac_instances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Consente di visualizzare una riga per ogni istanza di applicazione livello dati distribuita in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. sysdac_instances appartiene dello schema dbo nel database msdb. Nella tabella seguente vengono descritte le colonne nella vista sysdac_instances.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|Identificatore dell'istanza di applicazione livello dati.|  
|nome_istanza|**sysname**|Nome dell'istanza di applicazione livello dati specificata alla distribuzione dell'applicazione livello dati.|  
|type_name|**sysname**|Nome dell'applicazione livello dati specificata alla creazione del pacchetto di applicazione livello dati.|  
|type_version|**nvarchar (64)**|Versione dell'applicazione livello dati specificata alla creazione del pacchetto di applicazione livello dati.|  
|description|**nvarchar(4000)**|Descrizione dell'applicazione livello dati scritta alla creazione del pacchetto di applicazione livello dati.|  
|type_stream|**varbinary(max)**|Flusso di bit contenente una rappresentazione codificata degli oggetti logici, quali tabelle e viste, contenuti nell'applicazione livello dati.|  
|date_created|**datetime**|Data e ora di creazione dell'istanza di applicazione livello dati.|  
|created_by|**sysname**|Account di accesso utilizzato per la creazione dell'istanza di applicazione livello dati.|  
|database_name|**sysname**|Nome del database creato per l'istanza di applicazione livello dati.|  
  
## <a name="remarks"></a>Osservazioni  
 Un'applicazione livello dati include un tipo di applicazione livello dati, ovvero una definizione degli oggetti di livello dati logici utilizzati da un'applicazione, quali tabelle e viste. Un pacchetto DAC è un file utilizzato per la distribuzione di DAC. Il pacchetto di applicazione livello dati contiene una rappresentazione di tutti gli oggetti logici contenuti nel tipo di applicazione livello dati. Il pacchetto di applicazione livello dati può essere utilizzato per la distribuzione di una o più copie, o istanze, dell'applicazione livello dati in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Ogni istanza di applicazione livello dati distribuita dallo stesso pacchetto di applicazione livello dati condivide lo stesso tipo, ma è associata a un nome di istanza e a un identificatore univoci.  
  
## <a name="permissions"></a>Permissions  
 Per visualizzare tutte le colonne è necessaria l'appartenenza al ruolo predefinito del server sysadmin. I membri del ruolo public possono visualizzare le colonne instance_name, description e type_version.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Visualizzazioni di applicazione livello dati &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/0de01328-d7a6-4677-b7a0-dcd3098c23d4)  
  
  