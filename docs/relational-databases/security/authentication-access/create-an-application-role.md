---
title: Creare un ruolo applicazione | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0778c9ac00e6d9c06161ccc8429e0eb9ae4d846d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-an-application-role"></a>Creazione di un ruolo applicazione
  In questo argomento viene descritto come creare un ruolo applicazione in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. I ruoli applicazione limitano l'accesso dell'utente a un database solo tramite applicazioni specifiche. Poiché i ruoli applicazione non dispongono di utenti, l'elenco **Membri ruolo** non viene visualizzato quando si seleziona **Ruolo applicazione** .  
  
> [!IMPORTANT]  
>  In fase di impostazione delle password per i ruoli applicazione viene eseguito il controllo dei requisiti di complessità delle password. Le applicazioni che richiamano i ruoli applicazione devono archiviare le relative password. Le password dei ruoli applicazione devono essere sempre archiviate in forma crittografata.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per creare un ruolo applicazione utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY APPLICATION ROLE nel database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
##### <a name="to-create-an-application-role"></a>Per creare un ruolo applicazione  
  
1.  In Esplora oggetti espandere il database in cui si desidera creare un ruolo applicazione.  
  
2.  Espandere la cartella **Sicurezza** .  
  
3.  Espandere la cartella **Ruoli** .  
  
4.  Fare clic con il pulsante destro del mouse sulla cartella **Ruoli applicazione** , quindi scegliere **Nuovo ruolo applicazione**.  
  
5.  Nella pagina **Generale** della finestra di dialogo **Ruolo applicazione - Nuovo**immettere il nome del nuovo ruolo applicazione nella casella **Nome ruolo** .  
  
6.  Nella casella **Schema predefinito** specificare lo schema che diventerà proprietario degli oggetti creati da questo ruolo immettendo i nomi degli oggetti. In alternativa, fare clic sui puntini di sospensione **(...)** per aprire la finestra di dialogo **Individua schema** .  
  
7.  Nella casella **Password** , immettere una password per il nuovo ruolo. Immettere nuovamente quella password nella casella **Conferma password** .  
  
8.  In **Schemi di proprietà del ruolo**, selezionare o visualizzare gli schemi che saranno di proprietà di questo ruolo. Uno schema può essere di proprietà di un solo schema o ruolo.  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Opzioni aggiuntive  
 Nella finestra di dialogo **Ruolo applicazione - Nuovo** sono inoltre disponibili opzioni in due pagine aggiuntive, cioè **Entità a protezione diretta** e **Proprietà estese**.  
  
-   Nella pagina **Entità a protezione diretta** sono elencate tutte le possibili entità a protezione diretta e le autorizzazioni su quelle entità a protezione diretta che possono essere concesse all'account di accesso.  
  
-   La pagina **Proprietà estese** consente di aggiungere proprietà personalizzate a utenti di database.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-create-an-application-role"></a>Per creare un ruolo applicazione  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 Per altre informazioni, vedere [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-application-role-transact-sql.md).  
  
  