---
title: Connettersi a Microsoft SQL Server Parallel Data Warehouse (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a9e8dd851604203a9a6c02959c3d11002145f9dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680096"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a>Connettersi a Microsoft SQL Server Parallel Data Warehouse (SSAS)
  Questa pagina dell'**Importazione guidata tabella** consente di specificare le impostazioni per connettersi a Microsoft SQL Server Parallel Data Warehouse (PDW). Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 SQL Server PDW è uno strumento estremamente scalabile che offre prestazioni a basso costo tramite un sistema di elaborazione parallela massiva. Per altre informazioni su SQL Server PDW, vedere il sito Web [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895). È possibile connettersi al data warehouse tramite l'autenticazione SQL Server. Per connettersi a un'origine dati, è necessario che nel computer sia installato il provider appropriato.  
  
> [!NOTE]  
>  Le credenziali dell'utente corrente vengono utilizzate in caso di selezione di un database in questa pagina. Tuttavia, l'importazione non verrà completata se l'utente specificato nella pagina Impostazioni di rappresentazione non dispone di privilegi sufficienti per leggere dal database selezionato.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Nome descrittivo connessione**  
 Digitare un nome univoco per questa connessione all'origine dati. Questo campo è obbligatorio.  
  
 **Nome server**  
 Digitare il nome, o indirizzo IP, del server a cui connettersi.  
  
 **Nome utente**  
 Specificare un nome utente per la connessione al database.  
  
 Questo nome utente viene utilizzato quando si crea la stringa di connessione per l'origine dati. Queste credenziali vengono utilizzate anche in caso di visualizzazione in anteprima e filtro dei dati nella finestra Proprietà tabella e nell'Importazione guidata. Non vengono utilizzate per importare o aggiornare dati; in tal caso vengono infatti utilizzate le credenziali di Windows specificate nella pagina Impostazioni di rappresentazione.  
  
 **Password**  
 Specificare una password per la connessione al database.  
  
 **Salva password**  
 Specificare se la password immessa nella casella **Password** è stata archiviata.  
  
 **Nome database**  
 Selezionare un database dall'elenco di database.  
  
 **Advanced**  
 Impostare ulteriori proprietà relative alla connessione tramite la finestra di dialogo **Impostazione delle proprietà avanzate** . Per altre informazioni, vedere [Impostazione delle proprietà avanzate &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Test connessione**  
 Provare a stabilire una connessione all'origine dati utilizzando le impostazioni correnti. Viene visualizzato un messaggio che indica se la connessione è stata stabilita.  
  
  
