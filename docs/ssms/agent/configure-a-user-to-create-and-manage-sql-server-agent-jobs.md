---
title: Configurare un utente per la creazione e la gestione di processi di SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2c0a85b70906a7784093ba1fb6905c27278176fa
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a>Configurare un utente per la creazione e la gestione di processi di SQL Server Agent
In questo argomento viene illustrato come configurare un utente per la creazione o l'esecuzione di processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   **Prima di iniziare:**  [Sicurezza](#Security)  
  
-   **Per configurare un utente per la creazione e la gestione di processi di SQL Server Agent tramite**  [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Sicurezza  
Per configurare un utente per la creazione o l'esecuzione di processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, è anzitutto necessario aggiungere un account di accesso esistente di SQL Server o un ruolo msdb a uno dei ruoli predefiniti del database seguenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent nel database msdb: SQLAgentUserRole, SQLAgentReaderRole o SQLAgentOperatorRole.  
  
Per impostazione predefinita, i membri di questi ruoli del database possono creare passaggi di processo personalizzati ed eseguirli con il proprio account. Per eseguire processi che includono altri tipi di passaggi, ad esempio pacchetti [!INCLUDE[ssIS](../../includes/ssis_md.md)] , questi utenti non amministrativi dovranno avere accesso a un account proxy. Tutti i membri del ruolo predefinito del server sysadmin dispongono dell'autorizzazione per la creazione, la modifica e l'eliminazione degli account proxy. Per altre informazioni sulle autorizzazioni associate con questi ruoli di database predefiniti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Ruoli di database predefiniti di SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
#### <a name="Permissions"></a>Permissions  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
**Per aggiungere un account di accesso SQL o un ruolo msdb a un ruolo predefinito del database di SQL Server Agent**  
  
1.  Espandere un server in **Esplora oggetti**.  
  
2.  Espandere **Sicurezza**e quindi **Account di accesso**.  
  
3.  Fare clic con il pulsante destro del mouse sull'account di accesso che si vuole aggiungere al ruolo predefinito del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e scegliere **Proprietà**.  
  
4.  Nella pagina **Mapping utenti** della finestra di dialogo **Proprietà account di accesso** selezionare la riga contenente **msdb**.  
  
5.  Nell'area **Appartenenza a ruoli del database per: msdb**selezionare il ruolo predefinito del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Per configurare un account proxy per la creazione e la gestione dei passaggi di processo di SQL Server Agent**  
  
1.  Espandere un server in **Esplora oggetti**.  
  
2.  Espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse su **Proxy** e scegliere **Nuovo proxy**.  
  
4.  Nella pagina **Generale** della finestra **Nuovo account proxy** specificare il nome del proxy, il nome delle credenziali e la descrizione per il nuovo proxy. Si noti che prima di creare un proxy di SQL Server Agent, è necessario innanzitutto creare le credenziali. Per altre informazioni sulla creazione di una credenziale, vedere [Procedura: Creazione di credenziali (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/c1e77e91-2a69-40d9-b8b3-97cffc710586) e [CREATE CREDENTIAL (Transact-SQL)](http://msdn.microsoft.com/en-us/d5e9ae69-41d9-4e46-b13d-404b88a32d9d).  
  
5.  Selezionare i sottosistemi appropriati per il proxy.  
  
6.  Nella pagina **Entità** aggiungere o rimuovere account di accesso oppure ruoli per concedere o negare l'accesso all'account proxy.  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione della sicurezza di SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)  
  
