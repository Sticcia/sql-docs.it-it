---
title: Aggiungere tabelle a diagrammi (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 601f077b8ebeb5971526c6f9f25978e09078fb83
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099466"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a>Aggiunta di tabelle a diagrammi (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
È possibile aggiungere una tabella al diagramma di database per modificarne la struttura o per correlarla ad altre tabelle nel diagramma, aggiungendo una tabella di database esistente o inserendone una nuova non ancora definita nel database.  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a>Per inserire una nuova tabella nel diagramma  
  
1.  Assicurarsi di essere connessi al database nel quale si desidera creare la tabella.  
  
    Per creare una tabella nel diagramma corrente, fare clic sul pulsante **Nuova tabella** sulla barra degli strumenti.  
  
    oppure  
  
    Fare clic con il pulsante destro del mouse nel diagramma e scegliere **Nuova tabella**.  
  
2.  Nella finestra di dialogo **Scegli nome** modificare o accettare il nome di tabella assegnato dal sistema e scegliere **OK**.  
  
    Verrà visualizzata una nuova tabella nella vista Standard.  
  
3.  Digitare un nome di colonna nella prima cella della nuova tabella. Premere quindi il tasto TAB per passare alla cella successiva.  
  
4.  In **Tipo di dati**selezionare un tipo di dati per la colonna. A ciascuna colonna deve corrispondere un nome e un tipo di dati.  
  
    Le altre proprietà della colonna possono essere impostate in Progettazione tabelle.  
  
5.  Ripetere i passaggi 3 e 4 per ogni colonna da aggiungere alla tabella.  
  
> [!NOTE]  
> Una volta salvato il diagramma di database, la nuova tabella verrà aggiunta al database.  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a>Per aggiungere una tabella esistente a un diagramma  
  
1.  Assicurarsi di essere connessi al database di cui si desidera modificare le tabelle.  
  
2.  Selezionare una tabella nella cartella **Tabelle** .  
  
3.  Trascinare la tabella nel diagramma di database.  
  
4.  Rilasciare il pulsante del mouse.  
  
> [!NOTE]  
> Se esistono delle relazioni tra la tabella selezionata e altre tabelle nel diagramma, verranno tracciate automaticamente le linee delle relazioni.  
  
### <a name="to-add-related-tables-to-a-diagram"></a>Per aggiungere tabelle correlate a un diagramma  
  
1.  Selezionare una o più tabelle con vincoli di chiave esterna nel diagramma di database.  
  
2.  Fare clic con il pulsante destro del mouse su una delle tabelle selezionate e scegliere **Aggiungi tabelle correlate**.  
  
> [!NOTE]  
> Verranno aggiunte al diagramma sia le tabelle a cui fa riferimento un vincolo di chiave esterna dalle tabelle selezionate, sia quelle che fanno riferimento alle tabelle selezionate con un vincolo di chiave esterna.  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzare diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Utilizzo di tabelle in diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/work-with-tables-in-database-diagram-visual-database-tools.md)  
  
