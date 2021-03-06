---
title: Scelta dei dati per il Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content type [data mining]
- nested tables
- key [data mining]
- continuous values
- key sequence [data mining]
- table data type
- key time [data mining]
- discrete values
- discretized
ms.assetid: 7c72d80e-913c-4bbe-b258-444294a78838
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4a9c7a8152896aa3bd9f75cf483aaf29429a5638
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62681188"
---
# <a name="choosing-data-for-data-mining"></a>Scelta di dati per il data mining
  Quando si inizia il data mining, si potrebbe chiedere "quanti dati è necessario?" o "Sono previsti requisiti speciali che è necessario conoscere durante la pulizia o formattazione dei dati?"  
  
 In particolare, i meno esperti nel data mining si imbattono spesso in problemi relativi ai dati di Excel, ad esempio la necessità di formattare i dati in modo coerente nelle colonne, la pulizia dei valori mancanti o la creazione di contenitori per i numeri. In questa sezione sono inoltre elencati i requisiti di dati per tipi di modelli specifici.  
  
 [Scelta dei dati](#bkmk_ChoosingData)  
  
 [Problemi di dati comuni](#bkmk_CommonDataProblems)  
  
 [Altri requisiti di dati](#bkmk_OtherRequirements)  
  
##  <a name="bkmk_ChoosingData"></a> Scelta dei dati  
 La selezione dei dati utilizzati per l'analisi è forse la parte più importante del processo di data mining, ancora più importante della scelta di un algoritmo. Ciò è dovuto al fatto che il data mining non è in genere basato su ipotesi, ma sui dati. Anziché selezionare e verificare le variabili preventivamente, come si farebbe con un modello statistico tradizionale, il data mining può accettare dati e individuare nuove correlazioni o non riuscire a individuare alcun modello. La qualità e la quantità dei dati possono avere un effetto significativo sui risultati.  
  
 Attenersi, in linea generale, alle regole seguenti:  
  
-   Ottenere la quantità di dati puliti più ampia possibile.  
  
-   Eseguire il profiling dei dati prima di provare qualsiasi modelle. È necessario comprendere i dati prima di poter ottenere un significato dagli stessi. Come minimo:  
  
    1.  Utilizzare gli strumenti disponibili nei componenti aggiuntivi per trovare i valori massimo e minimo, i valori più comuni e i valori medi.  
  
    2.  Inserire i valori mancanti. I componenti aggiuntivi, nonché alcuni algoritmi, forniscono strumenti per l'immissione dei valori mancanti.  
  
    3.  Correggere i dati errati se possibile. I progetti di data mining sono spesso alla base di nuove iniziative per la qualità dei dati.  
  
-   Provare a compilare un modello di prova e individuare in tal modo i problemi relativi ai dati. Osservando i risultati, è possibile rilevare, ad esempio, che le proiezioni di vendita sono basate su dati anomali a causa di un errore di conversione della valuta.  
  
-   Provare a eseguire il cast dei dati in formati diversi oppure creare bucket per i numeri. I modelli emergono spesso quando si trasformano i dati.  
  
     Ad esempio, il livello di servizio del call center può variare in base al giorno della settimana e ciò non si noterebbe se si utilizzassero solo i valori datetime. È possibile migliorare le previsioni generandole su cicli di dieci giorni, anziché su unità giornaliere o settimanali.  
  
-   Inserire i numeri in contenitori appropriati per ridurre il numero di possibili valori per l'analisi.  
  
-   Creare più versioni dei dati e compilare più modelli.  
  
 Per altri suggerimenti su come selezionare, modificare ed esaminare i dati, vedere [elenco di controllo di preparazione per il Data Mining](checklist-of-preparation-for-data-mining.md).  
  
### <a name="how-much-data-do-i-need"></a>Quanti dati sono necessari  
 Come regola pratica, non prendere mai in considerazione meno di 50-100 righe di dati per i tipi di modelli e gli scenari più semplici. Ad esempio, per la previsione di un solo attributo tramite un modello Naïve Bayes e con un set di dati ben formato, si potrebbero generare stime abbastanza accurate utilizzando 50-100 righe di dati.  
  
 Per i modelli di associazione in genere necessari molti più dati: un migliaio di righe potrebbe non essere sufficiente se si analizzano molti attributi, ad esempio le associazioni tra prodotti. Se il set di dati è troppo grande o troppo piccolo, si possono talvolta ottenere risultati migliori comprimendo le righe in categorie. Ad esempio, anziché analizzare associazioni tra i singoli prodotti, è possibile suddividere i prodotti in categorie.  
  
 Se si dispone di un set di dati di dimensioni adeguate, incentrare l'analisi sulla qualità dei dati invece di aggiungere più dati. A un certo punto, tutti i modelli statisticamente validi saranno stati trovati e aggiungere più dati non ne migliora la validità. Viceversa, l'aggiunta di altri dati può talvolta introdurre correlazioni accidentali.  
  
### <a name="discrete-vs-continuous-numbers"></a>Numeri discreti e Numeri continui  
 Oggetto *discreti* colonna contiene un numero finito di valori. I caratteri di testo ad esempio vengono sempre trattati come valori discreti.  
  
 I valori discreti hanno alcuni attributi importanti. Ad esempio, se si considerano i numeri come discreti, non vi è un ordine implicito tra loro e non è possibile calcolare la media o la somma dei numeri. Gli indicativi di località telefonici sono un valido esempio di dati numerici discreti che non si utilizzerebbero mai per eseguire operazioni matematiche.  
  
 I valori discreti vengono talvolta denominati valori di categoria, in quanto, al contrario di numeri disposti in una serie infinita, essi possono essere utilizzati per raggruppare un set di dati.  
  
 Si potrebbe anche decidere di trattare i numeri come discreti quando i valori sono chiaramente separati e non è possibile utilizzare valori frazionari oppure tali valori non sono utili.  
  
 *Continua* dati numerici possono contenere un numero infinito di valori frazionari. Una colonna relativa al reddito è un esempio di colonna attributo continua. Se si specifica che una colonna è numerica, ogni valore in tale colonna deve essere un numero, ad eccezione dei valori Null. Si noti che in Excel possono essere considerati i timestamp e qualsiasi altra rappresentazione di data e ora che può essere convertita in un tipo di dati di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **Conversione di numeri in variabili categoriche**  
  
 Non necessariamente i numeri contenuti in una colonna devono essere considerati numeri continui. *Discretizzazione* offre molti vantaggi per l'analisi. uno dei quali è rappresentato dal fatto che si riduce lo spazio dei problemi. Un altro vantaggio è legato al fatto che talvolta i numeri non sono il modo migliore per esprimere un risultato.  
  
 Il numero di figli per nucleo familiare ad esempio può essere considerato sia come valore continuo che come valore discreto. Poiché una famiglia non può avere 2,5 figli e i nuclei familiari con 3 o più figli possono adottare comportamenti molto diversi rispetto a quelli con 2 figli, è possibile ottenere risultati migliori considerando questo numero come una categoria. Se, tuttavia, si compila un modello di regressione o è necessario trovare una media (ad esempio 1,357 figlio per nucleo familiare), è preferibile utilizzare un tipo di dati di numeri continui.  
  
 Non è possibile creare un modello di data mining con dati continui e quindi considerare in un secondo momento la colonna come colonna discreta. È necessario elaborare i due set di dati in modo diverso e gestirli nel back-end come strutture di data mining separate. Se si hanno dubbi sulla modalità ottimale di gestire i dati, è necessario creare modelli separati che gestiscono i dati in modo diverso. in ogni caso, ciò costituisce un ottimo modo per ottenere una prospettiva diversa sui dati e, forse, risultati differenti.  
  
 **Conversione di numeri in testo**  
  
 Molto spesso valori che devono essere discreti come Maschio e Femmina sono rappresentati come dati numerici, utilizzando le etichette 1 e 2. In genere, questa codifica viene effettuata per semplificare l'immissione dei dati o per risparmiare spazio di archiviazione in un database, ma può comportare problemi di ambiguità riguardo alla natura o al significato dei valori. Poiché inoltre i valori discreti vengono archiviati come numeri, quando si spostano i dati tra le applicazioni si potrebbero verificare errori di conversione del tipo di dati e i valori potrebbero venire calcolati o trattati in altro modo come valori continui. Per evitare che si verifichino problemi di questo tipo, prima di iniziare le procedure di data mining è consigliabile convertire di nuovo le etichette numeriche in etichette di testo discrete.  
  
 **Il binning dei numeri**  
  
 Anche se tutti i numeri in linea di principio sono infiniti e quindi continui, quando si modellano le informazioni può risultare più efficace *discretizzare* oppure *bin* i valori disponibili.  
  
 È possibile suddividere i dati in molti modi:  
  
-   Specificare un numero finito di bucket e fare in modo che l'algoritmo ordini i valori in bucket.  
  
-   Pre-raggruppare i dati manualmente, creando alcuni set di raggruppamenti che abbiano significato a livello aziendale o più facili da utilizzare. In questo modo, spesso si perde la vera distribuzione dei valori, ma gli intervalli possono essere letti più facilmente dagli utenti.  
  
-   Consentire all'algoritmo di determinare il numero ottimale di bucket e la distribuzione di valori. Questo è l'impostazione predefinita nella maggior parte degli strumenti, ma è possibile eseguire l'override di questi valori predefiniti in di **Data Mining** procedure guidate sulla barra degli strumenti.  
  
-   Approssimare i valori a una media centrale o a un valore rappresentativo.  
  
##  <a name="bkmk_CommonDataProblems"></a> Problemi di dati comuni  
  
### <a name="excel-number-formats"></a>Formati numerici di Excel  
 Excel è uno strumento facile da utilizzare, in quanto si tratta di crea dei problemi: è possibile inserire qualsiasi tipo di dati in qualsiasi punto. Tuttavia, prima di iniziare a cercare modelli e ad analizzare le correlazioni, è necessario imporre ai dati una struttura o alcuni vincoli.  
  
 Per impostazione predefinita, quando si importano dati numerici in [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel, i numeri vengono archiviati in formato decimale con due cifre decimali. Se tale formato numerico non è appropriato, cambiare formato o cambiare il numero di cifre decimali.  
  
 Una possibilità consiste nell'usare la [Rietichettare](relabel-sql-server-data-mining-add-ins.md) dello strumento per modificare il modo che i numeri sono visualizzati o raggruppati.  
  
 Tuttavia, se i dati sono troppo complessi per l'elaborazione con la **Rietichettare** strumento, è possibile usare le funzioni numeriche di Excel per convertire i dati in intervalli discreti, salvare il risultato in una colonna separata e quindi usare la colonna discretizzata per classificazione invece.  
  
 Se ad esempio si desidera analizzare i risultati di una corsa e si desidera raggruppare i partecipanti in base ai tempi di arrivo espressi in minuti, è possibile eseguire un arrotondamento per eccesso al minuto più prossimo e salvare il valore arrotondato in una nuova colonna. È inoltre possibile estrarre solo il valore relativo al minuto utilizzando la funzione `MINUTE` e quindi salvare tale valore in una nuova colonna utilizzabile per l'analisi.  
  
### <a name="discretizing-numbers-and-dates-in-excel"></a>Discretizzazione di numeri e date in Excel  
 Per impostazione predefinita, i dati numerici in Excel vengono archiviati come `Double`. Anche i valori di data e ora vengono archiviati in un formato numerico. Se è necessario discretizzare numeri o date per il data mining, è innanzitutto consigliabile aggiungere nuove colonne prima di compilare il modello di data mining oppure convertire le date e i numeri in un altro formato.  
  
### <a name="scientific-number-formats"></a>Formati numerici scientifici  
 Spesso nell'output degli strumenti di data mining le probabilità vengono indicate utilizzando la notazione scientifica, per rappresentare numeri molto grandi o molto piccoli. Se non si ha familiarità con la notazione scientifica, è possibile visualizzare questi numeri in un altro formato modificando semplicemente la formattazione della cella.  
  
##### <a name="to-change-scientific-notation-to-a-decimal-numeric-format"></a>Per modificare la notazione scientifica in un formato numerico decimale  
  
1.  Nella tabella dati di Excel evidenziare la colonna o la cella contenente il numero in notazione scientifica.  
  
2.  Fare doppio clic e selezionare **formattare le celle** dal menu di scelta rapida.  
  
3.  Nel **categoria** elenco, selezionare **numero**.  
  
4.  Aumentare il numero di cifre decimali. Una probabilità rappresentata in notazione scientifica è generalmente molto piccola.  
  
     Verrà modificata solo la visualizzazione del numero, mentre il valore sottostante resterà invariato.  
  
### <a name="working-with-dates-and-times"></a>Utilizzo di date e ore  
 Quando in una tabella di Excel sono contenute date e si utilizza la colonna come input o per la stima, i risultati ottenuti potrebbero non essere quelli previsti, a seconda della formattazione delle informazioni relative a data o ora. Ad esempio, quando si usa **rileva categorie** oppure **classifica** e includere una colonna che contiene date, le date sono suddivisi in categorie come numeri con molte cifre decimali. Non si tratta di un errore, bensì di una rappresentazione accurata dei dati sottostanti. L'algoritmo di data mining utilizza il formato di archiviazione sottostante, non il formato di visualizzazione.  
  
 Se si incontrano difficoltà con le date e si desidera analizzarle utilizzando raggruppamenti basati sulla logica comune come mese o giorno, è possibile utilizzare le funzioni DATA in Excel per estrarre l'anno, il mese o il giorno in una colonna separata e utilizzare quindi la colonna per la classificazione.  
  
##  <a name="bkmk_OtherRequirements"></a> Altri requisiti di dati  
  
### <a name="requirements-by-algorithm-type"></a>Requisiti per tipo di algoritmo  
 Per creare un modello, alcuni algoritmi utilizzati nei componenti aggiuntivi richiedono tipi di dati o di contenuti specifici.  
  
 **Modelli Naïve Bayes**  
  
-   L'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes, ad esempio, non può utilizzare colonne continue come input. È pertanto necessario suddividere i numeri oppure, se il numero di valori è sufficiente, gestirli come valori discreti.  
  
-   Non è inoltre possibile stimare valori continui con questo tipo di modello. Se si desidera stimare un numero continuo, ad esempio i redditi, è pertanto necessario suddividere prima i valori in intervalli significativi. Se si hanno dubbi sugli intervalli appropriati, è possibile utilizzare l'algoritmo di clustering per individuare gruppi di numeri nei dati.  
  
-   Quando si usa una procedura guidata basata su questo algoritmo (ad esempio [analizza fattori di influenza chiave &#40;strumenti di analisi tabelle per Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)), le colonne continue verranno categorizzate dalla procedura guidata è.  
  
-   Se si compila un modello Naive Bayes utilizzando il [modellazione avanzata &#40;aggiuntivi di Data Mining per Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) opzione, le colonne di numeri verranno rimosse dal modello. Se si vuole evitare questo problema, usare il [modificare le etichette &#40;componenti aggiuntivi Data Mining di SQL Server&#41; ](relabel-sql-server-data-mining-add-ins.md) dello strumento per creare una nuova colonna con valori suddivisi.  
  
 **I modelli di clustering**  
  
-   Gli strumenti di clustering ([Creazione guidata Cluster &#40;aggiuntivi di Data Mining per Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) e [rileva categorie &#40;strumenti di analisi tabelle per Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)) che non è possibile anche usare continua numeri, ma entrambi gli strumenti suddividono automaticamente le colonne di numeri per l'utente.  
  
-   Entrambi gli strumenti offrono la possibilità di scegliere il numero di categorie di output nei risultati, ma se si desidera controllare il modo in cui vengono raggruppati i valori in singole colonne, è necessario creare una nuova colonna con il raggruppamento desiderato.  
  
 **I modelli di previsione**  
  
-   Tutti gli strumenti di previsione richiedono la stima di un numero continuo. Non è possibile prevedere un numero salvato come testo.  
  
-   Se i dati contengono colonne di numeri con il tipo di dati errato, è possibile utilizzare le funzioni di Excel o PowerPivot per creare una copia della colonna con il tipo di dati numerico corretto. In tal caso, assicurarsi di rimuovere la copia della colonna contenente numeri salvati come testo, in modo che i valori non siano duplicati.  
  
-   Se si desidera creare un grafico a dispersione di un modello di regressione, le variabili di input devono essere numeri continui, espressi come tipo di dati appropriato.  
  
### <a name="using-content-types-to-make-better-models"></a>Utilizzo di tipi di contenuto per ottimizzare i modelli  
 Oggetto *tipo di contenuto* è una proprietà si applica a una colonna per specificare come i dati della colonna devono essere utilizzati dal modello. L'algoritmo può utilizzare il tipo di contenuto come istruzione o hint durante l'analisi.  
  
 Se, ad esempio, una colonna contiene numeri che si ripetono in un intervallo specifico per indicare i giorni della settimana, è possibile contrassegnare il tipo di contenuto di tale colonna come `Cyclical`.  
  
 Non è necessario preoccuparsi di tipi di contenuto se si usa le procedure guidate e gli strumenti forniti in questo componente aggiuntivo. Tuttavia, se si usa la [aggiunta modello a struttura &#40;aggiuntivi di Data Mining per Excel&#41; ](add-model-to-structure-data-mining-add-ins-for-excel.md) modellazione opzione per aggiungere un nuovo modello ai dati esistenti, si verifichi un errore relativo ai tipi di contenuto.  
  
 Il motivo è che alcuni tipi di modello richiedono un determinato tipo di dati, ad esempio timestamp. Gli strumenti elaborano queste colonne in base ai requisiti specifici e aggiungono inoltre una proprietà del tipo di contenuto. Pertanto, se si riutilizzano i dati con un algoritmo completamente diverso, potrebbe essere necessario modificare il tipo di dati o il tipo di contenuto.  
  
 Nell'elenco seguente vengono descritti i tipi di contenuto utilizzati nel data mining e vengono identificati i tipi di dati che supportano ogni tipo di contenuto.  
  
 `Discrete`  
 La colonna contiene un numero finito di valori senza continuità. Ad esempio, una colonna relativa al sesso è una tipica colonna attributo discreta, in quanto i dati rappresentano un numero specifico di categorie.  
  
 Il tipo di contenuto `Discrete` può essere utilizzato con tutti i tipi di dati.  
  
 `Continuous`  
 La colonna contiene valori che rappresentano dati numerici su una scala che consente valori provvisori. Una colonna continua rappresenta misure scalabili e i dati possono contenere un numero infinito di valori frazionari. Una colonna di temperature è un esempio di colonna attributo continua.  
  
 Il tipo di contenuto `Continuous` può essere utilizzato con i tipi di dati seguenti: `Date`, `Double` e `Long`.  
  
 `Discretized`  
 La colonna contiene valori che rappresentano gruppi di valori derivati da una colonna continua. I bucket vengono considerati **ordinati** e valori discreti.  
  
 Il tipo di contenuto `Discretized` può essere utilizzato con i tipi di dati seguenti: `Date`, `Double` e `Long`.  
  
 **Key**  
 La colonna identifica in modo univoco una riga.  
  
 In genere la colonna chiave è un identificatore numerico o di testo che non deve essere utilizzato per l'analisi, ma solo per la registrazione di record. Le eccezioni sono chiavi della serie temporale e chiavi della sequenza.  
  
 **Chiavi delle tabelle annidate** vengono utilizzati solo quando si ottengono dati da un'origine dati esterna definita come un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vista origine dati. Per altre informazioni sulle tabelle annidate, vedere [ https://msdn.microsoft.com/library/ms175659.aspx ](https://msdn.microsoft.com/library/ms175659.aspx):  
  
 Questo tipo di contenuto può essere utilizzato con i tipi di dati seguenti: `Date`, `Double`, `Long` e `Text`.  
  
 **Sequenza di tasti**  
 La colonna contiene valori che rappresentano una sequenza di eventi. I valori sono ordinati, ma non è necessario che siano equidistanti.  
  
 Questo tipo di contenuto è supportato dai tipi di dati `Double`, `Long`, `Text` e `Date`.  
  
 **Chiave temporale**  
 La colonna contiene valori ordinati che rappresentano una scala cronologica. È possibile utilizzare il tipo di contenuto chiave temporale solo se il modello è un modello Time Series o un modello Sequence Clustering.  
  
 Questo tipo di contenuto è supportato dai tipi di dati `Double`, `Long` e `Date`.  
  
 **Tabella**  
 Anche questo tipo di contenuto viene utilizzato solo quando si ottengono dati da un'origine dati esterna definita come vista origine dati di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Ciò in pratica significa che ogni riga di dati contiene effettivamente una tabella dati annidata, con una o più colonne e una o più righe.  
  
 Le tabelle nidificate sono molto utili, ma è possibile usarli solo con il [modellazione avanzata &#40;aggiuntivi di Data Mining per Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) opzioni di modellazione. Ad esempio, i dati di esempio per la [associare guidata &#40;Client di Data Mining per Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) guidata e [market Basket Analysis &#40;strumenti di analisi tabelle per Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) strumento contiene dati che sono stati resi bidimensionali da una tabella nidificata.  

  
  
