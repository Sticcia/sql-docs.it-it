---
title: Modificare una stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7cbc7981817a6c62db378976fe36a4dc753c6b9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63015882"
---
# <a name="modify-a-stored-procedure"></a>Modificare una stored procedure
    
##  <a name="Top"></a> In questo argomento viene descritto come modificare una stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#Restrictions), [Sicurezza](#Security)  
  
-   **Per modificare una stored procedure usando:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] in stored procedure CLR e viceversa.  
  
 Se la definizione di stored procedure precedente è stata creata tramite l'opzione WITH ENCRYPTION o WITH RECOMPILE, tali opzioni sono abilitate solo se incluse nell'istruzione ALTER PROCEDURE.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER PROCEDURE per la stored procedure.  
  
##  <a name="Procedures"></a> Modalità di modifica di una stored procedure  
 È possibile usare uno dei seguenti elementi:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per modificare una stored procedure in Management Studio**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**, espandere il database a cui appartiene la stored procedure, quindi espandere **Programmabilità**.  
  
3.  Espandere **Stored procedure**, fare clic con il pulsante destro del mouse sulla stored procedure da modificare, quindi scegliere **Modifica**.  
  
4.  Modificare il testo della stored procedure.  
  
5.  Per controllare la sintassi, scegliere **Analizza** dal menu **Query**.  
  
6.  Per salvare le modifiche alla definizione della stored procedure, scegliere **Esegui** dal menu **Query**.  
  
7.  Per salvare la definizione della stored procedure aggiornata come script [!INCLUDE[tsql](../../includes/tsql-md.md)] , scegliere **Salva con nome** dal menu **File**. Accettare il nome del file o sostituirlo con uno nuovo, quindi fare clic su **Salva**.  
  
> [!IMPORTANT]  
>  Convalidare sempre input di tutti gli utenti. Non concatenare l'input dell'utente prima di averlo convalidato. Non eseguire mai un comando creato dall'input dell'utente non convalidato.  
  
###  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per modificare una stored procedure nell'editor di query**  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**ed espandere il database a cui appartiene la stored procedure. In alternativa, selezionare il database nell'elenco dei database disponibili sulla barra degli strumenti. Per questo esempio, selezionare il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  Scegliere **Nuova query** dal menu **File**.  
  
4.  Copiare e incollare l'esempio seguente nell'editor di query. Nell'esempio viene creata la stored procedure `uspVendorAllInfo` mediante la quale vengono restituiti i nomi di tutti i fornitori nel database [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , i prodotti da essi forniti, nonché le informazioni relative alla posizione creditizia e alla disponibilità.  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  Scegliere **Nuova query** dal menu **File**.  
  
6.  Copiare e incollare l'esempio seguente nell'editor di query. Nell'esempio viene modificata la stored procedure `uspVendorAllInfo` . La clausola EXECUTE AS CALLER viene rimossa e il corpo della stored procedure viene modificato in modo da restituire solo i fornitori del prodotto specificato. Le funzioni `LEFT` e `CASE` personalizzano l'aspetto del set di risultati.  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  Per salvare le modifiche alla definizione della stored procedure, scegliere **Esegui** dal menu **Query**.  
  
8.  Per salvare la definizione della stored procedure aggiornata come script [!INCLUDE[tsql](../../includes/tsql-md.md)] , scegliere **Salva con nome** dal menu **File**. Accettare il nome del file o sostituirlo con uno nuovo, quindi fare clic su **Salva**.  
  
9. Per eseguire la stored procedure modificata, eseguire l'esempio riportato di seguito.  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
