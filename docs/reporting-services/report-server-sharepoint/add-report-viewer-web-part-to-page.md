---
title: Aggiungere la web part Visualizzatore di report di SQL Server Reporting Services in una pagina di SharePoint | Microsoft Docs
ms.date: 11/26/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51f45290847444a1400f1d708755c6737a3b3f84
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65574783"
---
# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>Aggiungere la web part Visualizzatore di report di SQL Server Reporting Services in una pagina di SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2016-2019](../../includes/ssrs-appliesto-sharepoint-2016-2019.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

Visualizzare un report, da SQL Server Reporting Services o dal server di report di Power BI aggiungendo una web part Visualizzatore di report a una pagina di SharePoint.

![Web part Visualizzatore di report in una pagina di SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Prerequisites

* Per caricare correttamente i report, è necessario configurare Attestazioni per il servizio token Windows (C2WTS) per la delega vincolata Kerberos. Per altre informazioni su come configurare C2WTS, vedere [Attestazioni per il servizio token Windows (C2WTS) e Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md).

* La web part Visualizzatore di report deve essere distribuita alla farm di SharePoint. Per informazioni su come distribuire il progetto della soluzione web part Visualizzatore di report, vedere [Distribuire la web part Visualizzatore di report in un sito di SharePoint](deploy-report-viewer-web-part.md).

* Per aggiungere una web part a una pagina Web, è necessario avere l'autorizzazione Aggiunta e personalizzazione pagine a livello di sito. Se si usano impostazioni di sicurezza predefinite, questa autorizzazione è concessa ai membri del gruppo **Proprietari** che hanno il livello di autorizzazione Controllo completo.

## <a name="add-web-part"></a>Aggiungere una web part

1. Nel sito di SharePoint selezionare l'icona dell'**ingranaggio** in alto a sinistra e selezionare **Aggiungi una pagina**.

    ![Aggiungere una pagina a un sito di SharePoint dall'icona dell'ingranaggio.](media/sharepoint-add-a-page.png)

2. Assegnare alla pagina un nome e selezionare **Crea**.

3. Nella finestra di progettazione della pagina selezionare la scheda **Inserisci** della barra multifunzione. Selezionare quindi **web part** all'interno della sezione **Parti**.

    ![Inserire una web part dalla barra multifunzione di Office.](media/sharepoint-insert-web-part.png)

4. In **Categorie** selezionare **SQL Server Reporting Services (modalità nativa). In **Parts** selezionare **Visualizzatore report**. Selezionare quindi **Aggiungi**.

    ![Aggiungere la web part Visualizzatore di report.](media/sharepoint-report-viewer-web-part.png)

    È possibile che inizialmente venga visualizzato un errore. L'errore è dovuto al fatto che l'URL del server di report predefinito è impostato su *https://localhost* e non è disponibile nel percorso.

## <a name="configure-the-report-viewer-web-part"></a>Configurare la web part Visualizzatore di report

Per configurare la web part in modo da puntare al report specifico, eseguire le operazioni seguenti.

1. Quando si modifica la pagina di SharePoint, selezionare la freccia GIÙ in alto a destra della web part e selezionare **Modifica web part**.

    ![Modificare la pagina Web dal menu a discesa della web part.](media/sharepoint-edit-web-part.png)

2. Immettere l'**URL server di report** per il server di report che ospita il report. L'URL dovrebbe essere simile a *https://myrsserver/reportserver*.

3. Immettere il percorso e il nome del report che si vuole visualizzare nella web part. Il percorso e il nome dovranno essere simili a */AdventureWorks Sample Reports/Company Sales*. In questo esempio, il report *Company Sales* si trova in una cartella denominata *AdventureWorks Sample Reports*.

4. Se il report richiede parametri, dopo aver specificato l'URL del server di report e il nome del report, selezionare **Carica parametri** nella sezione **Parametri**.

5. Selezionare **Ok** per salvare le modifiche alla configurazione della web part.

6. Selezionare **Salva** nella barra multifunzione di Office per salvare le modifiche alla pagina di SharePoint.

![Web part Visualizzatore di report in una pagina di SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* La web part Visualizzatore di report non può essere usata nelle pagine moderne all'interno di SharePoint.
* I report di Power BI non possono essere usati con la web part Visualizzatore di report.
* Se non viene visualizzata la web part Visualizzatore di report da aggiungere alla pagina, accertarsi di aver [distribuito la web part Visualizzatore di report](deploy-report-viewer-web-part.md).

Altre domande? [Visitare il forum su Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
