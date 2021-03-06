---
title: Aggiungere nuovi elementi a un progetto | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fcb6d5e1a811f13a346a3daf89de459273cd2140
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105354"
---
# <a name="add-new-items-to-a-project"></a>Aggiunta di nuovi elementi a un progetto
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
È possibile aggiungere nuovi elementi a un progetto per estendere la funzionalità dell'applicazione. Un nuovo elemento può essere una query o una connessione. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] sono disponibili due tipi di progetto: progetto script di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e progetto script di Analysis Services. Gli elementi che è possibile aggiungere varieranno a seconda del tipo di progetto. È possibile aggiungere, ad esempio, una query [!INCLUDE[tsql](../../includes/tsql-md.md)] (un file con estensione sql) a un progetto script di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ma non a un progetto script di Analysis Services.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] non consente di creare cartelle all'interno dei progetti. Per organizzare il lavoro, creare più progetti all'interno della soluzione.  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a>Per aggiungere una nuova query a un progetto esistente  
  
1.  In Esplora soluzioni selezionare un progetto di destinazione.  
  
2.  Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare una categoria nel riquadro sinistro.  
  
4.  Selezionare un modello di query nel riquadro destro e fare clic su **Aggiungi**. La nuova query verrà aggiunta nella cartella **Query** del progetto.  
  
5.  Nella finestra di dialogo **Connetti al Motore di database** specificare una connessione per la nuova query e fare clic su **Connetti**. Se non si vuole associare una connessione alla nuova query, fare clic su **Annulla** nella finestra di dialogo della connessione.  
  
6.  Se lo si desidera, rinominare la query in Esplora soluzioni.  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a>Per aggiungere una nuova connessione a un progetto esistente  
  
1.  In Esplora soluzioni selezionare un progetto di destinazione.  
  
2.  Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Selezionare **Connessione** nel riquadro sinistro.  
  
4.  Selezionare **Nuova connessione** nel riquadro destro e fare clic su **Aggiungi**.  
  
5.  Nella finestra di dialogo **Connetti al Motore di database** specificare una connessione per la nuova query e fare clic su **Connetti**. La nuova connessione verrà aggiunta nella cartella **Connessioni** del progetto.  
  
## <a name="see-also"></a>Vedere anche  
[Esplora soluzioni](../../ssms/solution/solution-explorer.md)  
[Associazione di estensioni di file a un editor di codice](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
[Aggiunta di elementi esistenti a un progetto](../../ssms/solution/add-existing-items-to-a-project.md)  
[Rimozione o eliminazione di un elemento o di un progetto](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
