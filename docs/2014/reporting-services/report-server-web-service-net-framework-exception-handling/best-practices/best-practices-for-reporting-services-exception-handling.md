---
title: Procedure consigliate per la gestione delle eccezioni in Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd38e382cc0b34de0498dd5ed9ce0237a5a1e07f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046133"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Procedure consigliate per la gestione delle eccezioni di Reporting Services
  Quando si sviluppano applicazioni [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è possibile ricorrere a diversi metodi per eliminare o ridurre le eccezioni. Quando si verificano le eccezioni, fornire messaggi di errore chiari e concisi all'utente e aggiungere funzionalità adeguate di gestione delle eccezioni per impedire che le applicazioni vengano chiuse in modo imprevisto.  
  
 Un'applicazione che invia richieste al servizio Web ReportServer deve essere in grado di effettuare le operazioni seguenti:  
  
-   Evitare che vengano generate eccezioni impedendo il maggior numero possibile di richieste non valide.  
  
-   Rilevare le eccezioni e fornire codice specifico di gestione degli errori quando possibile.  
  
-   Gestire i casi di errore che non generano eccezioni.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Metodi per evitare le richieste non valide](preventing-invalid-requests.md)|Vengono descritte le tecniche per impedire l'invio delle richieste non valide al server di report.|  
|[Uso di blocchi try/catch](using-try-and-catch-blocks.md)|Viene descritto come migliorare l'affidabilità dell'applicazione con i blocchi try/catch.|  
|[Gestione di avvisi e casi che non causano eccezioni](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Viene illustrato come gestire gli errori che non comportano la generazione di un'eccezione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Uso della proprietà Detail per la gestione di errori specifici](using-the-detail-property-to-handle-specific-errors.md)|Spiega come gestire errori specifici a livello di codice tramite la proprietà **Detail** dell'oggetto **SoapException**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Detail](../soapexception-class/detail-property.md)   
 [Introduzione alla gestione delle eccezioni in Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
