---
title: Creare una Query di stima utilizzando Generatore Query di stima | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a112efd8fdfe2b8108d2b6005028f10abf4a706
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740201"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a>Creare una query di stima utilizzando Generatore query di stima
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile creare query di stima mentre si compila una soluzione di data mining in BI Development Studio, o facendo clic con il pulsante destro del mouse su un modello di data mining esistente in SQL Server Management Studio e scegliendo quindi l'opzione **Compila query di stima**.  
  
 Nel **generatore delle query di stima** sono disponibili tre modalità di progettazione che è possibile alternare facendo clic sulle icone nell'angolo in alto a sinistra.  
  
-   **Progetta**  
  
-   **Query**  
  
-   **Result**  
  
 La modalità**Progettazione** consente di compilare una query di stima scegliendo dati di input, eseguendo il mapping dei dati al modello e aggiungendo quindi funzioni di stima in istruzioni compilate tramite la griglia. Nella griglia di progettazione sono presenti questi blocchi predefiniti:  
  
 **Origine**  
 Scegliere l'origine della nuova colonna. È possibile utilizzare le colonne del modello di data mining, le tabelle di input incluse nella vista origine dati, una funzione di stima o un'espressione personalizzata.  
  
 **Campo**  
 Determina la colonna o funzione specifica associata alla selezione nella colonna **Origine** .  
  
 **Alias**  
 Determina il nome della colonna nel set di risultati.  
  
 **Mostra**  
 Determina se la selezione nella colonna **Origine** viene visualizzata o meno nei risultati.  
  
 **Gruppo**  
 Insieme alla colonna **And/Or** consente di raggruppare espressioni racchiudendole tra parentesi. Ad esempio (espr1 Or espr2) And espr3.  
  
 **And/Or**  
 Crea la logica della query. Ad esempio (espr1 Or espr2) And espr3.  
  
 **Criteri/Argomento**  
 Specifica una condizione o espressione dell'utente per la colonna. È possibile trascinare colonne dalle tabelle alla cella.  
  
 La modalità**Query** fornisce un editor di testo che offre accesso diretto al linguaggio DMX (Data Mining Extensions), oltre a una vista dei dati di input e delle colonne del modello. Quando si seleziona la modalità **Query** la griglia utilizzata per definire la query viene sostituita da un editor di testo di base. È possibile utilizzare tale editor per copiare e salvare le query composte o per incollare le query DMX esistenti e presenti negli Appunti ed eseguirle.  
  
 Nella vista**Risultato** viene eseguita la query corrente e vengono visualizzati i risultati in una griglia. Se i dati sottostanti sono stati modificati e si desidera eseguire nuovamente la query, fare clic sul pulsante Esegui sulla barra di stato.  
  
 È possibile progettare una query di data mining utilizzando una combinazione degli strumenti visivi e dell'editor di testo. Se si modifica la query tramite l'editor di testo e si torna quindi alla vista **Progettazione** , le modifiche apportate andranno perse e verrà ripristinata la query originale creata dal generatore di query di stima. In questo argomento viene illustrato l'utilizzo del generatore di query grafico.  
  
### <a name="to-create-a-prediction-query"></a>Per creare una query di stima  
  
1.  Fare clic sulla scheda **Stima modello di data mining** in Progettazione modelli di data mining.  
  
2.  Fare clic su **Seleziona modello** nella tabella **Modello di data mining** .  
  
     Verrà visualizzata la finestra di dialogo **Seleziona modello di data mining** , in cui sono indicate tutte le strutture di data mining presenti nel progetto.  
  
3.  Selezionare il modello in base al quale si desidera creare una stima e quindi fare clic su **OK**.  
  
4.  Nella casella **Seleziona tabelle di input** fare clic su **Seleziona tabella del case**.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona tabella** .  
  
5.  Nell'elenco **Origine dati** selezionare l'origine dei dati contenente i dati su cui si desidera creare una stima.  
  
6.  Nella casella **Nome tabella/vista** selezionare la tabella contenente i dati sui cui si desidera creare una stima e quindi fare clic su **OK**.  
  
     Dopo aver selezionato la tabella di input, il generatore delle query di stima crea un mapping predefinito tra il modello di data mining e la tabella di input in base ai nomi delle colonne. Per eliminare un mapping, fare clic per selezionare la linea che collega la colonna contenuta nella tabella **Modello di data mining** alla colonna contenuta nella tabella **Seleziona tabelle di input** e quindi premere CANC. È inoltre possibile creare mapping manualmente facendo clic su una colonna nella tabella **Seleziona tabelle di input** e trascinandola sulla colonna corrispondente nella tabella **Modello di data mining** .  
  
7.  Aggiungere qualsiasi combinazione dei tre tipi di informazioni seguenti alla griglia del generatore delle query di stima:  
  
    -   Colonne stimabili dalla casella **Modello di data mining** .  
  
    -   Qualsiasi combinazione di colonne di input dalla casella **Seleziona tabelle di input** .  
  
    -   Funzioni di stima  
  
8.  Eseguire la query facendo clic sul primo pulsante della barra degli strumenti della scheda **Stima modello di data mining** e quindi selezionando **Risultato**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una query singleton in Progettazione modelli di data mining](../../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)   
 [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md)  
  
  
