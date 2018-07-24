---
title: Creare pacchetti in SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 94fddf1871c03bd70f86a61c80a736d2f18a30a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324571"
---
# <a name="create-packages-in-sql-server-data-tools"></a>Creare pacchetti in SQL Server Data Tools
  I pacchetti creati in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] tramite Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] vengono salvati nel file system. Per salvare un pacchetto in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o nell'archivio pacchetti, è necessario salvare una copia del pacchetto. Per altre informazioni, vedere [Salvataggio di una copia di un pacchetto](../../2014/integration-services/save-a-copy-of-a-package.md).  
  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]è possibile creare un nuovo pacchetto con uno dei metodi seguenti:  
  
-   Utilizzare il modello di pacchetto incluso in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
-   Utilizzare un modello personalizzato  
  
     Per utilizzare pacchetti personalizzati come modelli per la creazione di nuovi pacchetti, è sufficiente copiare tali modelli nella cartella DataTransformationItems, che per impostazione predefinita si trova in C:\Programmi\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
-   Copiare un pacchetto esistente.  
  
     Se sono disponibili altri pacchetti che includono funzionalità che si desidera riutilizzare, sarà possibile compilare più rapidamente il flusso di controllo e i flussi di dati nel nuovo pacchetto copiando e incollando gli oggetti necessari da tali pacchetti. Per altre informazioni su come copiare e incollare oggetti nei progetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , vedere [Riutilizzo di oggetti di pacchetto](reuse-of-package-objects.md).  
  
     Se si crea un nuovo pacchetto copiando un pacchetto esistente oppure utilizzando un pacchetto personalizzato come modello, verranno copiati anche il nome e il GUID del pacchetto esistente. Sarà pertanto necessario modificare il nome e il GUID del nuovo pacchetto per distinguerlo da quello da cui è stato copiato. Se ad esempio sono presenti più pacchetti con lo stesso GUID, sarà più difficile stabilire a quale pacchetto appartengono i dati di un log. È possibile rigenerare il GUID nella `ID` proprietà e aggiornare il valore della `Name` usando la finestra proprietà in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Impostazione delle proprietà di un pacchetto](set-package-properties.md) e [Utilità dtutil](dtutil-utility.md).  
  
-   Utilizzare un pacchetto personalizzato designato come modello.  
  
-   Eseguire l’Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
     L'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] crea un pacchetto completo per un'importazione o un'esportazione semplice. Questa procedura guidata consente di configurare le connessioni, l'origine e la destinazione e di aggiungere tutte le trasformazioni dei dati necessarie per eseguire immediatamente l'importazione o l'esportazione. È facoltativamente possibile salvare il pacchetto per eseguirlo nuovamente in un secondo momento o rifinire e migliorare il pacchetto in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Se si salva il pacchetto, tuttavia, è necessario aggiungerlo a un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] esistente prima che sia possibile modificarlo o eseguirlo in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Le procedure seguenti descrivono come creare o eliminare un pacchetto in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Per un video che illustra come creare un pacchetto di base usando il modello di pacchetto predefinito, vedere [Creazione di un pacchetto di base (video su SQL Server)](http://go.microsoft.com/fwlink/?LinkId=131023).  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>Per creare un pacchetto in SQL Server Data Tools utilizzando il Modello del Pacchetto  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in cui si desidera creare un pacchetto.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Pacchetti SSIS** e scegliere **Nuovo pacchetto SSIS**.  
  
3.  Facoltativamente, è possibile aggiungere al pacchetto un flusso di controllo, attività flusso di dati e gestori di eventi. Per altre informazioni, vedere [Flusso di controllo](control-flow/control-flow.md), [Flusso di dati](data-flow/data-flow.md) e [Gestori eventi di Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md).  
  
4.  Scegliere **Salva elementi selezionati** dal menu **File** per salvare il nuovo pacchetto.  
  
    > [!NOTE]  
    >  È possibile salvare un pacchetto vuoto.  
  
  