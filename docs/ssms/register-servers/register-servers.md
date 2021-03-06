---
title: Registrazione di server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 880692611ff827b77ec5f24565f7ce3626df17a5
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65104266"
---
# <a name="register-servers"></a>Registrazione di server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La registrazione di un server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente di archiviare le informazioni sulla connessione al server per uso futuro. È possibile registrare un server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]in tre modi.  
  
1.  Le istanze locali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono registrate automaticamente durante il primo avvio di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] dopo l'installazione.  
  
2.  È inoltre possibile iniziare la procedura di registrazione automatica in qualsiasi momento, per ripristinare la registrazione delle istanze locali del server.  
  
3.  Infine, è possibile registrare un server utilizzando lo strumento Server registrati di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="benefits-of-registered-servers"></a>Vantaggi di Server registrati  
 Server registrati consente di:  
  
-   Registrare i server per mantenere le informazioni di connessione.  
  
-   Stabilire se un server registrato è in esecuzione.  
  
-   Collegare facilmente Esplora oggetti e l'editor di query a un server registrato.  
  
-   Modificare o eliminare le informazioni di registrazione per un server registrato.  
  
-   Creare gruppi di server.  
  
-   Specificare nomi semplici da usare per i server registrati immettendo nella casella **Nome server registrato** un valore diverso da quello presente nell'elenco **Nome server** .  
  
-   Specificare descrizioni dettagliate per i server registrati.  
  
-   Specificare descrizioni dettagliate dei gruppi di server registrati.  
  
-   Esportare gruppi di server registrati.  
  
-   Importare gruppi di server registrati.  
  
-   Visualizzare i file di log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le istanze online o offline di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Attività correlate  
 Utilizzare gli argomenti seguenti per iniziare a utilizzare i server registrati:  
  
|**Descrizione**|**Argomento**|  
|---------------------|---------------|  
|Registrare istanze locali del server|[Registrare un server connesso &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/register-a-connected-server-sql-server-management-studio.md)|  
|Registrare un server|[Creare un nuovo server registrato &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/create-a-new-registered-server-sql-server-management-studio.md)|  
|Visualizzare i server registrati|[Visualizzazione della finestra Server registrati in SQL Server Management Studio](../../tools/sql-server-management-studio/view-registered-servers-in-sql-server-management-studio.md)|  
|Rimuovere un server registrato|[Rimuovere un server registrato &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/remove-a-registered-server-sql-server-management-studio.md)|  
|Modificare la registrazione di un server|[Modificare la registrazione di un server &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)|  
|Connettersi a un server registrato|[Connettersi a un server registrato &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)|  
|Disconnettersi da un server registrato|[Disconnettersi da un server registrato &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|Spostare un server registrato o un gruppo di server|[Spostare un server registrato o un gruppo di server registrati &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/move-a-registered-server-or-registered-server-group.md)|  
|Modificare il nome di un server registrato o di un gruppo di server|[Modificare il nome di un server registrato o di un gruppo di server registrati &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-the-name-of-registered-server-or-registered-server-group.md)|  
|Creare o modificare un gruppo di server|[Creare o modificare un gruppo di server &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/create-or-edit-a-server-group-sql-server-management-studio.md)|  
|Rimuovere un gruppo di server|[Rimuovere un gruppo di server &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/remove-a-server-group-sql-server-management-studio.md)|  
|Esportare informazioni relative a server registrati|[Esportare informazioni relative a server registrati &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/export-registered-server-information-sql-server-management-studio.md)|  
|Importare informazioni relative ai server registrati|[Importare informazioni relative a server registrati &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/import-registered-server-information-sql-server-management-studio.md)|  
|Creare un server di gestione centrale e un gruppo di server|[Creare un server di gestione centrale e un gruppo di server &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md)|  
|Eseguire istruzioni su più server contemporaneamente|[Eseguire istruzioni su più server contemporaneamente &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Server remoti](../../database-engine/configure-windows/remote-servers.md)  
  
  
