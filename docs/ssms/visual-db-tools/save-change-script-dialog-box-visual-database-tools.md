---
title: Finestra di dialogo Salva script modifiche (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b15796ca6dc6b9faf1b2601b1727e5b693e2bc63
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099242"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Finestra di dialogo Salva script modifiche (Visual Database Tools)
  In questa finestra di dialogo viene visualizzato lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] relativo alle modifiche apportate a partire dall'ultimo salvataggio della tabella. Questa finestra consente inoltre di salvare lo script in un file di testo nel percorso desiderato.  
  
 È possibile accedere a questa finestra di dialogo dopo avere apportato modifiche non salvate a una tabella in Progettazione tabelle. Scegliere **Genera script delle modifiche** dal menu **Progettazione tabelle**.  
  
> [!NOTE]  
>  Gli script delle modifiche disponibili in Visual Database Tools non includono la gestione degli errori. Si suppone che gli oggetti di database non abbiano subito modifiche dopo l'apertura dello strumento e che quindi non si verificherà alcun problema relativo a modifiche. Prima di eseguire uno script delle modifiche è consigliabile includere le istruzioni di gestione degli errori appropriate.  
  
## <a name="options"></a>Opzioni  
 **Genera automaticamente script delle modifiche a ogni salvataggio**  
 Se si seleziona questa opzione, la finestra di dialogo **Salva script modifiche** verrà visualizzata ogni volta che si salvano le modifiche apportate a una tabella.  
  
 **Sì**  
 Visualizza la finestra di dialogo **Salva** , in cui è possibile selezionare il percorso per il file di testo.  
  
 **No**  
 Annulla la creazione dello script delle modifiche.  
  
  
