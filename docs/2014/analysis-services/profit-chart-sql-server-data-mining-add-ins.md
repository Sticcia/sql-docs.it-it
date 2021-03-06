---
title: Grafico (SQL Server Data Mining Add-ins) profitti | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ddeafaafd816e226edff764c8e273cde6df4eaad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748455"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a>Grafico profitti (componenti aggiuntivi Data mining di SQL Server)
  ![Pulsante grafico profitti sulla barra multifunzione Data Mining](media/dmc-profitchart.gif "pulsante grafico profitti sulla barra multifunzione Data Mining")  
  
 Un grafico dei profitti consente di visualizzare l'aumento dei profitti stimato associato all'utilizzo di un modello di data mining al fine di determinare i clienti che devono essere contattati in uno scenario aziendale. L'asse Y del grafico rappresenta i profitti, mentre l'asse X rappresenta la percentuale della popolazione contattata dall'azienda. Un grafico dei profitti tipico mostra un incremento dei profitti fino a un punto specifico, dopo il quale i profitti diminuiscono con l'aumentare della popolazione contattata.  
  
## <a name="configuring-the-profit-chart"></a>Configurazione del grafico dei profitti  
 Mentre il grafico di accuratezza consente solo di valutare la probabilità che le stime siano o meno esatte, il grafico dei profitti incorpora una conoscenza reale delle conseguenze di un'azione intrapresa sulla base di una stima. Questo risultato si ottiene prendendo in considerazione i fattori seguenti, da specificare quando si esegue la procedura guidata:  
  
-   **Popolazione**  
  
     Numero di case nel set di dati utilizzato per la creazione del grafico di accuratezza, ad esempio il numero di potenziali clienti.  
  
-   **Costi fissi**  
  
     Costi fissi associati al problema aziendale. Nel caso di una soluzione per il mailing diretto, i costi non dipendono da variabili quali il numero di chiamate telefoniche effettuate o il numero di mailing promozionali inviati.  
  
-   **Costi singolo contatto**  
  
     Costi extra in aggiunta ai costi fissi che possono essere associati al contatto di ogni cliente, relativi ad esempio a mailing promozionali o a chiamate telefoniche.  
  
-   **Ricavi per singolo contatto**  
  
     Importo dei ricavi associati a ogni vendita effettuata.  
  
## <a name="using-the-profit-chart-wizard"></a>Utilizzo della procedura guidata Grafico profitti  
 Per creare un grafico dei profitti, è necessario fare riferimento a un modello di data mining esistente. È possibile esplorare i modelli per trovare un modello che corrisponda ai propri dati facendo clic **Gestione modelli** oppure **Sfoglia** per visualizzare informazioni dettagliate sull'algoritmo utilizzato e le colonne nel modello di data mining.  
  
 Per altre informazioni, vedere [esplorazione di modelli in Excel &#40;componenti aggiuntivi Data Mining di SQL Server&#41; ](browsing-models-in-excel-sql-server-data-mining-add-ins.md) e [Gestione modelli &#40;componenti aggiuntivi Data Mining di SQL Server&#41;](manage-models-sql-server-data-mining-add-ins.md).  
  
#### <a name="to-create-a-profit-chart"></a>Per creare un grafico dei profitti  
  
1.  Selezionare un modello esistente.  
  
2.  Specificare la colonna di cui si desidera eseguire la stima e un valore di destinazione, se appropriato.  
  
3.  Selezionare i dati di origine, ovvero i dati da passare al modello per creare una stima. Tali dati non devono essere quelli utilizzati per creare il modello.  
  
4.  Eseguire il mapping delle colonne dei nuovi dati di origine alle colonne utilizzate nel modello di data mining. Viene automaticamente eseguito il mapping delle colonne con nomi simili.  
  
5.  Immettere le informazioni sui costi richieste dalla procedura guidata, ovvero i costi fissi, i costi singolo contatto, la popolazione e i ricavi previsti.  
  
6.  Facoltativamente, è possibile immettere una serie progressiva di costi (fare clic su Sfoglia **(...)**  pulsante). Poiché ad esempio un'azione di mailing può diventare meno costosa aumentando il numero di unità inviate, è possibile immettere un costo diverso a seconda del numero di unità e i costi verranno adattati automaticamente per ogni dimensione del campione.  
  
7.  Verrà creato un grafico contenente l'analisi costi-benefici per il modello.  
  
### <a name="requirements"></a>Requisiti  
 Per la stima di un valore numerico discreto, è necessario selezionare il valore di destinazione esatto per cui eseguire la stima.  
  
## <a name="understanding-the-profit-chart"></a>Informazioni sul grafico dei profitti  
 Il grafico dei profitti contiene una linea verticale grigia, che è possibile spostare facendo clic su un punto del grafico. Il **legenda Data Mining** Visualizza un punteggio, la popolazione corretta e la probabilità di stima associati con la posizione della linea grigia nel grafico. Se si seleziona il punto massimo di profitti nel grafico tramite la linea grigia, è possibile utilizzare il valore della probabilità di stima al fine di determinare una soglia di probabilità per contattare un cliente.  
  
 Se ad esempio il picco della curva dei profitti corrisponde al 55% della popolazione e la probabilità di stima associata è pari al 20%, per raggiungere i profitti massimi è consigliabile contattare solo i clienti la cui risposta viene stimata con una probabilità del 20% o superiore.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalida dei modelli e utilizzo dei modelli per la stima &#40;dati di componenti aggiuntivi Data Mining per Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
