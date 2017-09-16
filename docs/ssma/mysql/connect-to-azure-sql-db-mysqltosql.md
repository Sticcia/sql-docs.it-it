---
title: Connettersi al database SQL di Azure (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98888517c8f092b5d014be0bf2c0112f1afa1629
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Connettersi al database SQL di Azure (MySQLToSQL)
Utilizzare la connessione per la finestra di dialogo di SQL Azure per la connessione al database di SQL Azure che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti a SQL Azure**. Se in precedenza si è connessi, il comando è **Riconnetti a SQL Azure.**  
  
## <a name="options"></a>Opzioni  
**Nome server**  
  
Selezionare o immettere il nome del Server per la connessione a SQL Azure.  
  
**Database**  
  
Selezionare, inserire o **Sfoglia** il nome del Database.  
  
> [!IMPORTANT]  
> SSMA per MySQL non supporta la connessione al database master in SQL Azure.  
  
**Nome utente**  
  
Immettere il nome utente utilizzato per connettersi al database di SQL Azure SSMA  
  
**Password**  
  
Immettere la password associata al nome utente.  
  
**Crittografare**  
  
SSMA consiglia una connessione crittografata a SQL Azure.  
  
## <a name="create-azure-database"></a>Creare il Database di Azure  
Se non sono disponibili database nell'account di SQL Azure, è possibile creare il primo database.  
  
Per creare un nuovo database per la prima volta, seguire i passaggi seguenti  
  
1.  Fare clic sul pulsante Sfoglia che è presente nella finestra Connetti per la finestra di dialogo di SQL Azure  
  
2.  Se non sono disponibili database, vengono visualizzati i seguenti due voci di menu.  
  
    1.  **(Nessun database trovato)**  che è disabilitato e visualizzato in grigio costantemente  
  
    2.  **Crea nuovo database** cui è abilitata solo se non sono disponibili database nell'account di SQL Azure. Facendo clic su questa voce di menu nella finestra di dialogo Crea Database di Azure è presente con dimensioni e il nome di database.  
  
3.  Al momento della creazione del database, i due parametri seguenti vengono forniti come input:  
  
    1.  **Nome del database:** immettere il nome del Database.  
  
    2.  **Dimensioni del database:** selezionare le dimensioni del Database che si devono creare nell'account di SQL Azure.  
  
