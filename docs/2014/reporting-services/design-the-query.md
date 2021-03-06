---
title: Progettazione Query | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 46e3db8807e8e730ce0476f27d2dad0e3a64eaf4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63165160"
---
# <a name="design-the-query"></a>Progettazione query
  Utilizzare questa pagina della Creazione guidata report per creare una query immettendola manualmente, utilizzando Generatore query per compilare una query in modo interattivo o importando la query da un altro report.  
  
 Il tipo di origine dati selezionato nella pagina Selezione origine dati, una pagina precedente della Creazione guidata report, determina la query che è possibile immettere in questa pagina. Se, ad esempio, il tipo di origine dati è [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], è possibile immettere istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] o nomi di stored procedure. Se il tipo di origine dati è [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], il riquadro Query è disabilitato e non è possibile immettere una query direttamente. È possibile specificare la query utilizzando Generatore di query.  
  
## <a name="options"></a>Opzioni  
 **Stringa di query**  
 Consente di digitare una query che recupera i dati da utilizzare nel report.  
  
 **Generatore di query**  
 Fare clic su **Generatore di query** per aprire una finestra Progettazione query per l'origine dati o importare una query da un altro report.  
  
 Per ulteriori informazioni sugli strumenti di progettazione query, vedere [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).  
  
## <a name="example"></a>Esempio  
 Per il tipo di origine dati **Microsoft SQL Server**, la query seguente recupera un elenco di cognomi dalle [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Person` tabella.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Per il tipo di origine dati **Microsoft SQL Server**, la query seguente esegue il [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure di `uspGetEmployeeManagers` per il dipendente con identificazione numero 1:  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida della creazione guidata report](../../2014/reporting-services/report-wizard-help.md)   
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Aggiungere dati a un Report &#40;Report e SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
