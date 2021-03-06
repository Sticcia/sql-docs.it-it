---
title: 'Passaggio 3: Aggiungere e configurare una gestione connessione OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e55427c2249a93d2a97bbc13b7385dd56fac5d01
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723497"
---
# <a name="lesson-1-3-add-and-configure-an-ole-db-connection-manager"></a>Lezione 1-3: Aggiungere e configurare una gestione connessione OLE DB

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Dopo aver aggiunto una gestione connessione file flat per connettersi all'origine dati, si aggiunge una gestione connessione OLE DB per connettersi alla destinazione dei dati. Una gestione connessione OLE DB abilita un pacchetto all'estrazione di dati o al caricamento di dati in un'origine dati compatibile con OLE DB. Una gestione connessione OLE DB consente di specificare il server, il metodo di autenticazione e il database predefinito per la connessione.  
  
In questa attività verrà creata una gestione connessione OLE DB che usa l'autenticazione di Windows per la connessione all'istanza locale di **AdventureWorksDW2012**. A questa gestione connessione OLE DB faranno riferimento anche altri componenti che verranno creati più avanti in questa esercitazione, come la trasformazione Ricerca e la destinazione OLE DB.  
  
## <a name="add-and-configure-an-ole-db-connection-manager"></a>Aggiungere e configurare una gestione connessione OLE DB

1. Nel riquadro **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Gestioni connessioni** e selezionare **Nuova gestione connessione**.

1. Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **OLEDB** e quindi selezionare **Aggiungi**.
    
2. Nella finestra di dialogo **Configura gestione connessione OLE DB** selezionare **Nuova**.  
  
3. Per **Nome server**, immettere **localhost**.  
  
    Quando si specifica localhost come nome server, la gestione connessione stabilisce una connessione all'istanza predefinita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nel computer locale. Per utilizzare un'istanza remota di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], sostituire localhost con il nome del server a cui si desidera connettersi.  
  
4. Verificare che l'opzione **Usa autenticazione di Windows** sia selezionata nel gruppo **Accesso al server** .  
  
5. Nella casella **Selezionare o immettere un nome di database** del gruppo **Connessione al database** digitare o selezionare **AdventureWorksDW2012**.  
  
6. Selezionare **Test connessione** per verificare che le impostazioni di connessione specificate siano valide.  
  
7. Fare clic su **OK**.  
  
8. Fare clic su **OK**.  
  
9. Nel riquadro **Gestioni connessioni** verificare che sia selezionato **localhost. AdventureWorksDW2012**.  
  

## <a name="go-to-next-task"></a>Esecuzione del passaggio successivo
[Passaggio 4: Aggiungere un'attività Flusso di dati al pacchetto](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>Vedere anche  
[Gestione connessione OLE DB](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
