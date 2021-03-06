---
title: Creare, eliminare o modificare un'origine dati condivisa (gestione Report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8f1eaa33c0a113f540a841ca2cfcfadd71ed0c74
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265904"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a>Creare, eliminare o modificare un'origine dei dati condivisa (Gestione report)
  Un'origine dati condivisa consente di specificare le proprietà di connessione per un'origine dati. Se si dispone di un'origine dati utilizzata da un numero elevato di report, modelli o sottoscrizioni guidate dai dati, creare un'origine dati condivisa per eliminare l'overhead provocato dalla necessità di gestire le stesse informazioni sulla connessione in più posizioni.  
  
 L'icona seguente indica un'origine dei dati condivisa nella gerarchia di cartelle di Gestione report:  
  
 ![Icona di origine dati condivisa](media/hlp-16datasource.png "Icona di origine dati condivisa")  
Icona dell'origine dati condivisa  
  
### <a name="to-create-a-shared-data-source"></a>Per creare un'origine dati condivisa  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).  
  
2.  In Gestione report passare alla pagina **Contenuto** .  
  
3.  Fare clic su **Nuova origine dati**. Verrà visualizzata la pagina **Nuova origine dati** .  
  
4.  Digitare un nome per l'elemento. Un nome deve includere almeno un carattere e deve iniziare con una lettera. È inoltre possibile utilizzare alcuni simboli, con l'esclusione degli spazi e dei caratteri ; ? : \@ & = + , $ / * \< > | " /.  
  
5.  È possibile digitare facoltativamente una descrizione per fornire agli utenti informazioni sulla connessione. La descrizione verrà visualizzata nella pagina **Contenuto** in Gestione report.  
  
6.  Nell'elenco **Tipo di origine dati** specificare l'estensione per l'elaborazione dati usata per elaborare i dati dell'origine dati.  
  
7.  Per **Stringa di connessione**specificare la stringa usata dal server di report per la connessione all'origine dati. È consigliabile evitare di specificare credenziali nella stringa di connessione.  
  
     L'esempio seguente illustra una stringa di connessione usata per connettersi al database [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Per **Connetti tramite**specificare come verranno ottenute le credenziali quando il report è in esecuzione:  
  
    -   Se si vuole richiedere all'utente un nome di accesso e una password, fare clic su **Credenziali fornite dall'utente che esegue il report**. Per usare le credenziali immesse dall'utente come credenziali di Windows, fare clic su **Usa come credenziali di Windows per la connessione all'origine dei dati**. Se il nome utente e la password sono credenziali del database, non selezionare questa opzione.  
  
    -   Se si prevede di usare l'origine dati come origine dati condivisa con credenziali salvate gestite dal proprietario dell'origine dati o per i report che supportano le sottoscrizioni o altre operazioni pianificate, ad esempio la generazione della cronologia del report automatica, fare clic su **Credenziali archiviate in modo protetto nel server di report**. Se il server di database supporta la rappresentazione o la delega, selezionare **Rappresenta l'utente autenticato dopo che è stata stabilita una connessione all'origine dei dati**.  
  
    -   Se si vuole che le credenziali dell'utente che accede al report vengano passate dal server di report al server che ospita l'origine dati esterna, fare clic su **Sicurezza integrata di Windows**. In questo caso, all'utente non viene richiesto di digitare un nome utente o una password.  
  
    -   Se l'origine dati non usa credenziali (ad esempio, se l'origine dati è un file XML a cui si accede dal file system), fare clic su **Credenziali non necessarie**. È necessario specificare questo tipo di credenziali solo se l'operazione risulta valida per l'origine dati specifica. Se si seleziona questa opzione per un'origine dati che richiede l'autenticazione, la connessione non verrà stabilita. Se si seleziona questa opzione, assicurarsi inoltre di configurare l'account di esecuzione automatica che consente al server di report di connettersi agli altri computer per recuperare dati o file quando le credenziali utente non sono disponibili.  
  
     Per altre informazioni sulla configurazione delle credenziali, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](report-data/specify-credential-and-connection-information-for-report-data-sources.md). Per altre informazioni sull'account di esecuzione automatica, vedere [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
9. Fare clic sul pulsante **Test connessione** per convalidare la configurazione dell'origine dati.  
  
    > [!NOTE]  
    >  Il pulsante Test connessione non è supportato per il tipo di origine dati XML.  
  
10. Fare clic su **OK**.  
  
### <a name="to-modify-a-shared-data-source"></a>Per modificare un'origine dati condivisa  
  
1.  In Gestione report passare alla pagina Contenuto.  
  
2.  Passare alla voce origine dati condivisa, posizionare il puntatore del mouse sulla voce, fare clic sull'elenco a discesa e scegliere **Gestisci**dal menu di scelta rapida. Verrà visualizzata la pagina **Proprietà** .  
  
3.  Modificare l'origine dati e fare clic su **Applica**.  
  
### <a name="to-delete-a-shared-data-source"></a>Per eliminare un'origine dei dati condivisa  
  
-   In Gestione report passare alla pagina **Contenuto** e quindi eseguire una di queste operazioni:  
  
    -   Passare all'origine dei dati condivisa.  
  
         Fare clic sull'elemento per aprirlo. Verrà visualizzata la pagina Proprietà generali.  
  
         Fare clic su **Elimina**e quindi su **OK**.  
  
    -   Nella pagina **Contenuto** passare alla cartella contenente l'origine dati che si vuole eliminare.  
  
         Posizionare il puntatore del mouse sull'elemento, fare clic sull'elenco a discesa e scegliere **Elimina** dal menu di scelta rapida.  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni dati, origini dati e stringhe di connessione in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Pagina Contenuto &#40;Gestione report&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Gestire origini dati dei report](report-data/manage-report-data-sources.md)   
 [Configurare le proprietà delle origini dati per un report &#40;Gestione report&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
