---
title: Creare sinonimi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e2a45cf4f34b73996b6ecbd4f9cbb5f5a902e760
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854964"
---
# <a name="create-synonyms"></a>Creare sinonimi
  In questo argomento viene descritto come creare un sinonimo in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per creare un sinonimo utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per poter creare un sinonimo in un determinato schema, un utente deve disporre dell'autorizzazione CREATE SYNONYM, oltre a disporre della proprietà dello schema o dell'autorizzazione ALTER SCHEMA. L'autorizzazione CREATE SYNONYM è un'autorizzazione che può essere concessa.  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-synonym"></a>Per creare un sinonimo  
  
1.  In **Esplora oggetti**espandere il database in cui si desidera creare la nuova vista.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Sinonimi**, quindi selezionare **Nuovo sinonimo...**.  
  
3.  Nella finestra di dialogo **Aggiungi sinonimo** immettere le informazioni riportate di seguito.  
  
     **Nome sinonimo**  
     Digitare il nuovo nome che verrà utilizzato per questo oggetto.  
  
     **Schema sinonimo**  
     Digitare lo schema del nuovo nome che verrà utilizzato per questo oggetto.  
  
     **Nome server**  
     Digitare l'istanza del server a cui connettersi.  
  
     **Nome database**  
     Digitare o selezionare il database contenente l'oggetto.  
  
     **Schema**  
     Digitare o selezionare lo schema proprietario dell'oggetto.  
  
     **Tipo oggetto**  
     Selezionare il tipo di oggetto.  
  
     **Nome oggetto**  
     Digitare il nome dell'oggetto al quale fa riferimento il sinonimo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-create-a-synonym"></a>Per creare un sinonimo  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra Query, quindi fare clic su **Esegui**.  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Nell'esempio seguente viene creato un sinonimo per una tabella esistente nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Il sinonimo viene quindi utilizzato negli esempi successivi.  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 Nell'esempio seguente viene inserita una riga nella tabella di base cui fa riferimento il sinonimo `MyAddressType` .  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 Nell'esempio seguente viene illustrato il modo in cui è possibile fare riferimento a un sinonimo in un'istruzione nel linguaggio SQL dinamico.  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
