---
title: 'Passaggio 1: Creare un nuovo progetto di Integration Services | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 82420ce073f65483043d44670fc538849a447d90
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723322"
---
# <a name="lesson-1-1-create-a-new-integration-services-project"></a>Lezione 1-1: Creazione di un nuovo progetto di Integration Services

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Il primo passaggio nella creazione di un pacchetto in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste nel creare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Questo progetto di esempio include i modelli per origini dati, viste origini dati e pacchetti che compongono una soluzione di trasformazione dei dati.  
  
I pacchetti creati in questa esercitazione relativa a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] interpretano i valori dei dati dipendenti dalle impostazioni locali. Se il computer non è configurato per l'uso dell'opzione **Inglese (Stati Uniti)** per le impostazioni locali, è necessario impostare proprietà aggiuntive nel pacchetto. 

I pacchetti usati nelle lezioni da 2 a 6 vengono copiati dal pacchetto creato in questa lezione.  
  
> [!NOTE]  
> Se non è ancora stato fatto, vedere [Lezione 1: Prerequisiti](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).

## <a name="create-a-new-integration-services-project"></a>Creazione di un nuovo progetto di Integration Services  
  
1.  Nel menu **Start** di Windows cercare e selezionare **Visual Studio (SSDT)**.  
  
2.  In Visual Studio selezionare **File** > **Nuovo** > **Progetto** per creare un nuovo progetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Business Intelligence** in **Installati** e selezionare **Progetto di Integration Services** nel riquadro **Modelli**.  
  
4.  Nella casella **Nome** impostare il nome predefinito su **SSIS Tutorial**. Per usare una cartella già esistente, deselezionare la casella di controllo **Crea directory per soluzione**.  
  
5.  Accettare il percorso predefinito o selezionare **Sfoglia** per individuare la cartella che si vuole usare. Nella finestra di dialogo **Percorso progetto** selezionare la cartella e quindi **Seleziona cartella**.  
  
6.  Fare clic su **OK**.  
  
    Per impostazione predefinita viene creato e aggiunto al progetto un pacchetto vuoto in **Pacchetti SSIS**, denominato **Package.dtsx**.  
  
7.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Package.dtsx**, scegliere **Rinomina** e rinominare il pacchetto predefinito in **Lesson 1.dtsx**.  
  
## <a name="go-to-next-task"></a>Esecuzione del passaggio successivo
[Passaggio 2: Aggiungere e configurare una gestione connessione file flat](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
