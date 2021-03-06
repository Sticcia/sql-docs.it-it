---
title: Creare un Report drill-through (RDLC) con parametri usando ReportViewer (esercitazione su SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79e43f273183d531a8fbc61fd71315a971213773
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265384"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>Creare un report drill-through (RDLC) con parametri utilizzando ReportViewer (esercitazione su SSRS)
  Un report [drill-through](https://technet.microsoft.com/library/ff519554.aspx) è un report aperto da un utente facendo clic su un collegamento in un altro report. Nei report drill-through sono solitamente disponibili dettagli relativi a un elemento contenuto in un report di riepilogo originale. In questa esercitazione verranno illustrati le seguenti lezioni sulla creazione di un report drill-through con parametri e una query, in [report in modalità locale](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).  
  
## <a name="requirements"></a>Requisiti  
 Per utilizzare questa procedura dettagliata, è necessario poter accedere al database di esempio **AdventureWorks2008** . La query utilizzata in questa procedura dettagliata verrà utilizzata anche per il database **AdventureWorks2012** . Per altre informazioni su come ottenere il **AdventureWorks2008** database di esempio, vedere [procedura dettagliata: Installazione del Database AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) per Microsoft Visual Studio 2010.  
  
 Questa procedura dettagliata presuppone che l'utente abbia familiarità con le query Transaction-SQL e gli oggetti [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) e [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) di ADO.NET.  
  
 Utilizzare Visual Studio 2010 o Visual Studio 2012 e il modello di sito Web ASP.NET per creare una pagina Web ASP.NET con un controllo ReportViewer. Il controllo è configurato per visualizzare un report che viene creato. Per questa procedura dettagliata viene creata l'applicazione in Microsoft Visual C#.  
  
## <a name="tasks"></a>Attività  
 [Lezione 1: Creare un nuovo sito Web](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [Lezione 2: Definire una connessione dati e un tabella di dati per il Report padre](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [Lezione 3: Progettare il Report padre tramite la creazione guidata Report](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [Lezione 4: Definire una connessione dati e un tabella di dati per il Report figlio](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [Lezione 5: Progettare il Report figlio tramite la creazione guidata Report](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [Lezione 6: Aggiungere un controllo ReportViewer all'applicazione](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [Lezione 7: Aggiungere l'azione drill-through nel Report padre](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [Lezione 8: Creare un filtro dei dati](../reporting-services/lesson-8-create-a-data-filter.md)   
 [Lezione 9: Compilare ed eseguire l'applicazione](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazioni su Reporting Services &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [Progettare report con Progettazione report &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
