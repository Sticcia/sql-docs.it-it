---
title: 'Procedura: Specificare script pre-distribuzione o post-distribuzione | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f78f517-f13d-4f4b-84b9-e804cb490b2c
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d7b1e6537aa58d06d21eb3df0b4523bfd703252
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087133"
---
# <a name="how-to-specify-predeployment-or-postdeployment-scripts"></a>Procedura: specificare script pre-distribuzione o post-distribuzione
Gli script pre-distribuzione e post-distribuzione consentono di eseguire le istruzioni Transact\-SQL prima e dopo lo script di distribuzione principale generato dal progetto di database. Un progetto può contenere un solo script pre-distribuzione e un solo script post-distribuzione. Tali script possono essere utilizzati per molti scopi. Ad esempio  
  
-   Uno script pre-distribuzione può essere utilizzato per copiare i dati da una tabella da modificare in una tabella temporanea prima di riformattare e applicare i dati nella tabella modificata in uno script post-distribuzione  
  
-   È possibile inserire i dati di riferimento che devono essere presenti in una tabella in uno script post-distribuzione. Prima di inserire dati, è possibile verificare se sono già presenti nella tabella. Se la tabella non è vuota, è necessario cancellare i dati esistenti o specificare che si desidera sempre ricreare il database prima di distribuirlo. È possibile aggiungere un'istruzione come la seguente allo script post-distribuzione:  
  
```  
IF (EXISTS(SELECT * FROM [dbo].[MyReferenceTable]))  
BEGIN  
    DELETE FROM [dbo].[MyReferenceTable]  
END  
```  
  
## <a name="to-add-and-modify-a-pre--or-post-deployment-script"></a>Per aggiungere e modificare uno script pre-distribuzione o post-distribuzione  
  
1.  In **Esplora soluzioni** espandere il progetto di database per visualizzare la cartella Script.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella Script, quindi scegliere Aggiungi.  
  
3.  Selezionare Script dal menu di scelta rapida.  
  
4.  Selezionare Script pre-distribuzione o Script post-distribuzione. Facoltativamente, specificare un nome non predefinito. Fare clic su Aggiungi per completare l'operazione.  
  
5.  Fare doppio clic sul file nella cartella Script.  
  
    Verrà aperto l'Editor Transact\-SQL in cui è visualizzato il contenuto del file.  
  
È possibile utilizzare la sintassi e le variabili SQLCMD negli script e impostare tali valori nelle proprietà del progetto di database. Ad esempio  
  
-   È possibile utilizzare la sintassi SQLCMD per includere il contenuto di un file in uno script pre-distribuzione o post-distribuzione. I file vengono inclusi ed eseguiti nell'ordine in cui vengono definiti: `:r .\myfile.sql`  
  
-   È possibile utilizzare la sintassi SQLCMD per fare riferimento a una variabile nello script post-distribuzione. È possibile impostare la variabile SQLCMD nelle proprietà del progetto o in un profilo di pubblicazione.  
  
    ```  
    :setvar TableName MyTable  
    SELECT * FROM [$(TableName)]  
    ```  
  
Per altre informazioni sull'uso di SQLCMD negli script, vedere [Impostazioni del progetto di database](../ssdt/database-project-settings.md).  
  
## <a name="see-also"></a>Vedere anche  
[Sviluppo di database offline orientato ai progetti](../ssdt/project-oriented-offline-database-development.md)  
  