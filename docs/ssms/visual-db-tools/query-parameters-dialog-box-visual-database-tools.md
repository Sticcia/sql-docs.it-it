---
title: Finestra di dialogo Parametri query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7b841a4874c8fefa735547cdd42ff0cb704c1ccc
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098232"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Finestra di dialogo Parametri query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Questa finestra di dialogo consente di immettere valori per i parametri definiti nella query. Viene visualizzata quando si esegue una query contenente parametri che richiedono la presenza dell'utente finale in fase di esecuzione.  
  
## <a name="options"></a>Opzioni  
**Nome**  
Elenca i parametri definiti per la query eseguita. Se la query contiene parametri denominati, i nomi vengono visualizzati nell'elenco. Se nella query sono contenuti parametri senza nome, per ogni parametro della query verranno elencati i nomi di parametro definiti dal sistema.  
  
**Value**  
Immettere il valore per ogni parametro elencato in **Nome**. Il valore utilizzato per ultimo viene visualizzato come valore del parametro predefinito.  
  
## <a name="example"></a>Esempio  
La query del riquadro SQL riportata di seguito consente di aprire la finestra di dialogo Parametri query quando viene eseguita nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di query mediante parametri &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
