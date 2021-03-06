---
title: Rendering dei dati (Generatore report e SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a458fdf9-fb2a-4fee-9fbd-b38f36e91753
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 31eee586a5e825f3c2252e6e790d27263f04304d
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65576423"
---
# <a name="rendering-data-report-builder-and-ssrs"></a>Rendering dei dati (Generatore report e SSRS)
  Quando si utilizzano i renderer del layout, ad esempio HTML, MHTML, Word, Excel, PDF o Immagine, i dati e la relativa organizzazione rimangono invariati. Quando si esegue l'esportazione utilizzando un formato di renderer di dati, ad esempio CSV (Comma-Separated Value) o XML, non viene eseguito il rendering di alcun elemento del layout visivo. Durante il rendering del report, CSV e XML applicano al corpo del report e al relativo contenuto apposite regole che determinano la modalità di rendering dei dati in tali formati.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 È possibile utilizzare i renderer di dati per:  
  
-   Eseguire l'importazione in un database. CSV è un formato comune facilmente importabile in numerose applicazioni di database, tra cui SQL Server e Microsoft Access.  
  
-   Eseguire l'esportazione in Excel. Utilizzare il renderer CSV per esportare i dati in Excel senza il layout visivo. Dopo aver esportato i dati in Excel, è possibile sfruttare gli strumenti standard di Excel, ad esempio grafici, formule e tabelle pivot.  
  
-   Trasformazioni XSLT. È possibile applicare XSLT all'output del renderer XML. Questa trasformazione lato server rappresenta una tecnica potente per trasformare i dati in qualsiasi formato.  
  
-   Scambio di dati/EDI Un processo esterno può richiedere un rendering in formato CSV o XML di un report e utilizzare tali dati.  
  
 I formati dei renderer di dati sono controllati da un set di proprietà diverso rispetto a quello dei renderer di layout. Di seguito è riportato un elenco delle proprietà impostate nel riquadro **Proprietà** che si applicano solo ai renderer di dati:  
  
-   La proprietà DataElementOutput controlla se un elemento specifico è o meno presente nei dati al momento dell'esportazione.  
  
-   La proprietà DataElementName controlla il nome dell'elemento dati. Nel formato CSV controlla il nome dell'intestazione di colonna CSV, mentre nel formato XML diventa il nome dell'elemento o dell'attributo XML per l'elemento.  
  
-   La proprietà DataElementStyle controlla se nel formato XML il rendering dell'elemento del report viene eseguito come elemento o come attributo.  
  
 L'opzione di esportazione CSV consente di eseguire il salvataggio dei dati del report in file di testo normale delimitati da virgola, senza alcuna formattazione. Per impostazione predefinita, il file utilizza una virgola (,) per delimitare campi e righe, tuttavia questa impostazione è configurabile nelle impostazioni relative alle informazioni sul dispositivo. Il file risultante può essere aperto in un foglio di calcolo, come Office SharePoint Server, o utilizzato come formato di importazione per altri programmi. Il file con estensione csv può essere aperto in un editor di testo, ad esempio Blocco note. Se viene aperto come un URL, il file csv restituisce il tipo MIME **text/csv**. I file sono in formato MIME versione 1.0. Per altre informazioni sul rendering del report nel tipo di file CSV, vedere [Esportazione in un file CSV &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/exporting-to-a-csv-file-report-builder-and-ssrs.md).  
  
 L'opzione di esportazione File XML con dati del report consente di salvare un report come file XML. L'elemento XML Schema per il report è specifico del report. Le informazioni sul layout del report non vengono salvate dall'opzione di esportazione XML. Il codice XML generato da questa opzione può essere importato in un database, utilizzato come messaggio di dati XML o inviato a un'applicazione personalizzata. Per altre informazioni sul rendering del report nel tipo di file XML, vedere [Esportazione in XML &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/exporting-to-xml-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Paginazione in Reporting Services &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Tipi di rendering &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Funzionalità interattiva per estensioni per il rendering di report differenti &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendering degli elementi del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Reporting Services Device Information Settings](https://go.microsoft.com/fwlink/?LinkId=102515)  
  
  
