---
title: Autorizzazioni necessarie della connessione a SQL Server per il servizio CDC | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 406cb1233d871603a38dc2d904d7ecd894b5f0cd
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Autorizzazioni necessarie per la connessione a SQL per il servizio CDC
  Per eseguire le attività, CDC Service Configuration Console richiede informazioni di connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questo argomento vengono illustrate le informazioni che è possibile specificare nella finestra di dialogo Connect to SQL Server per l'impostazione della connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La finestra di dialogo Connect to SQL Server viene visualizzata quando necessario, ad esempio quando le informazioni di connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono disponibili o quando le informazioni sono presenti, ma la connessione non dispone delle autorizzazioni necessarie.  
  
 Nella tabella seguente vengono descritte le diverse attività per le quali è necessario disporre di una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le autorizzazioni necessarie relative all'utente o all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Attività|Autorizzazioni minime|  
|----------|-------------------------|  
|Preparare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`dbcreator` Ruolo predefinito del server|  
|Creare un account di accesso del servizio Oracle CDC-SQL Server che verrà utilizzato dal servizio Oracle CDC.|`public` Ruolo predefinito del server|  
|Creare un account di accesso del servizio Oracle CDC da utilizzare per la registrazione del nuovo servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
|Modificare un account di accesso del servizio Oracle CDC da utilizzare per l'aggiornamento della registrazione del servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
|Eliminare un account di accesso del servizio Oracle CDC da utilizzare per l'aggiornamento della registrazione del servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md)   
 [Connessione a SQL Server per l'eliminazione](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  