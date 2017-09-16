---
title: Generare feed di dati da un Report (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b49b80de8516e14972b05d7ae91f4f72e765803a
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---

# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Generare i feed di dati da un report (Generatore report e SSRS)

È possibile generare feed di dati conformi ad Atom dai report impaginati e quindi utilizzare i feed di dati nelle applicazioni, ad esempio Power Pivot, o Power BI, che può utilizzare dati feed.  
  
 Tramite l'estensione per il rendering Atom di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene generato un documento di servizio Atom in cui sono elencati i feed di dati disponibili in un report. Nel documento è elencato almeno un feed di dati per ogni area dati nel report. A seconda del tipo di area dati e dei dati in essa visualizzati, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] potrebbe generare più feed di dati da un'area dati.  
  
 Nel documento di servizio Atom è contenuto un identificatore univoco per ogni feed di dati che può essere usato in un URL per visualizzare il contenuto del feed di dati.  
  
 Per altre informazioni, vedere [Generazione di feed di dati dai report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Per generare un documento di servizio Atom  
  
1.  Nel portale Web di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , passare al report per il quale generare feed di dati.  
  
2.  Fare clic sul report.  
  
     Il report verrà eseguito.  
  
3.  Nella barra degli strumenti fare clic sull'icona **Esporta in feed di dati** .  
  
     Verrà visualizzato un messaggio in cui si chiede se si desidera salvare o aprire il documento Atom contenente il feed di dati.  
  
4.  Fare clic su **Salva** per salvare il documento nel file system o su **Apri** per visualizzare il contenuto del documento prima del salvataggio. **Per impostazione predefinita, il documento viene visualizzato in un browser.**  
  
5.  Selezionare il percorso per salvare il documento.  
  
6.  Se lo si desidera, modificare il nome del documento.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, il nome del documento corrisponde a quello del report.  
  
7.  Verificare che il tipo di documento sia **ATOMSVC**, quindi fare clic su **Salva**.  
  
8.  Se lo si desidera, aprire il file con estensione atomsvc in un browser, in un editor di testo o in un editor XML.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Per visualizzare un feed di dati conforme ad Atom  
  
1.  Se il documento di servizio Atom non è già aperto, individuarlo e aprirlo in un browser quale Internet Explorer.  
  
2.  Copiare l'URL del feed dei dati che si desidera visualizzare dal documento di servizio Atom nel browser.  
  
     Il formato dell'URL è il seguente:  
  
     `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
3.  Premere INVIO.  
  
     Verrà visualizzato un messaggio in cui si chiede se si desidera salvare o aprire il documento Atom contenente il feed di dati.  
  
4.  Fare clic su **Salva** per salvare il documento nel file system o su **Apri** per visualizzare il feed di dati prima del salvataggio.  
  
5.  Selezionare il percorso per salvare il documento.  
  
6.  Se lo si desidera, modificare il nome del documento.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, il nome del documento corrisponde a quello del report. Se il documento di servizio Atom dispone di più feed, per impostazione predefinita tutti presentano lo stesso nome ovvero il nome del report. Per differenziarli, rinominarli per usare nomi significativi.  
  
7.  Verificare che il tipo di documento sia **ATOM**, quindi fare clic su **Salva**.  
  
8.  Se lo si desidera, aprire il file con estensione atom in un browser, in un editor di testo o in un editor XML.  

## <a name="next-steps"></a>Passaggi successivi

[Esportare report](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)