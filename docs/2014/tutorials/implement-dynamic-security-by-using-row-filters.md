---
title: Implementare la sicurezza dinamica mediante i filtri di riga | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5a26f9c950dd09b8e47c83089415bd2b3d47458f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740381"
---
# <a name="implement-dynamic-security-by-using-row-filters"></a>Implementare la sicurezza dinamica mediante i filtri di riga
  In questa lezione supplementare verrà creato un ruolo aggiuntivo che implementa la sicurezza dinamica. La sicurezza dinamica offre la sicurezza a livello di riga in base al nome o all'ID di accesso dell'utente attualmente connesso. Per altre informazioni, vedere [Ruoli &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
 Per implementare la sicurezza dinamica, è necessario aggiungere una tabella al modello contenente i nomi degli utenti di Windows che possono creare una connessione al modello come origine dati ed esplorare oggetti modello e dati. Il modello creato in questa esercitazione è nel contesto di Adventure Works Corp. Tuttavia, per completare questa lezione, è necessario aggiungere una tabella contenente gli utenti del proprio dominio. Non saranno necessarie le password dei nomi utente che verranno aggiunti. Per creare una tabella Sicurezza dipendenti con una piccola parte degli utenti del proprio dominio, è possibile utilizzare la funzionalità Incolla per incollare i dati dei dipendenti da un foglio di calcolo di Excel. In uno scenario realistico la tabella che contiene i nomi utente da aggiungere a un modello utilizza in genere una tabella di un database effettivo come origine dati, ad esempio una tabella dimEmployee reale.  
  
 Per implementare la sicurezza dinamica, si useranno due nuove funzioni DAX: [Funzione USERNAME &#40;DAX&#41; ](https://msdn.microsoft.com/library/hh230954.aspx) e [funzione LOOKUPVALUE &#40;DAX&#41;](https://msdn.microsoft.com/library/gg492170.aspx). Queste funzioni applicate in una formula di filtro di riga vengono definite in un nuovo ruolo. Utilizzando la funzione LOOKUPVALUE, la formula specifica un valore della tabella Sicurezza dipendenti, quindi passa il valore alla funzione USERNAME che specifica il nome dell'utente connesso appartenente a questo ruolo. L'utente può quindi esplorare solo i dati specificati dai filtri di riga del ruolo. In questo scenario verrà specificato che i dipendenti addetti alle vendite possono esplorare solo i dati relativi alle vendite Internet per i territori di vendita in cui sono membri.  
  
 Per completare questa lezione supplementare, verrà completata una serie di attività. Le attività che sono specifiche di questo scenario di modello tabulare Adventure Works, ma che potrebbero non applicarsi necessariamente a uno scenario realistico, vengono identificate come tali. Ogni attività include informazioni aggiuntive che descrivono lo scopo dell'attività.  
  
 Tempo stimato per il completamento della lezione: **30 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questo argomento della lezione supplementare fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività di questa lezione supplementare, è necessario avere completato tutte le lezioni precedenti.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Aggiungere la tabella dimSalesTerritory al progetto AW Internet Sales Tabular Model  
 Per implementare la sicurezza dinamica per questo scenario di Adventure Works, è necessario aggiungere due tabelle aggiuntive al modello. La prima tabella da aggiungere è dimSalesTerritory (come Territorio vendita) dallo stesso database AdventureWorksDW. Successivamente verrà applicato un filtro di riga alla tabella Territorio vendita per definire i dati specifici che l'utente connesso può esplorare.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Per aggiungere la tabella dimSalesTerritory  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** , quindi scegliere **Connessioni esistenti**.  
  
2.  Nella finestra di dialogo **Connessioni esistenti** verificare che sia selezionata la connessione origine dati **Adventure Works DB da SQL** , quindi fare clic su **Apri**.  
  
     Se viene visualizzata la finestra di dialogo credenziali di rappresentazione, digitare le credenziali di rappresentazione usate nella lezione 2: Aggiungere i dati.  
  
3.  Nella pagina **Scelta della modalità di importazione dei dati** lasciare selezionata l'opzione **Seleziona da un elenco di tabelle e viste per scegliere i dati da importare** , quindi fare clic su **Avanti**.  
  
4.  Nella pagina **Seleziona tabelle e viste** selezionare la tabella **DimSalesTerritory**.  
  
5.  Nella colonna Nome descrittivo digitare **Territorio vendita**.  
  
6.  Fare clic su **Anteprima e Filtro**.  
  
7.  Deselezionare la colonna **SalesTerritoryAlternateKey** , quindi fare clic su **OK**.  
  
8.  Nella pagina **Seleziona tabelle e viste** fare clic su **Fine**.  
  
     La nuova tabella verrà aggiunta all'area di lavoro del modello. Gli oggetti e i dati della tabella dimSalesTerritory di origine verranno quindi importati nella nuova tabella Territorio vendita in AW Internet Sales Tabular Model.  
  
9. Dopo l'importazione della tabella fare clic su **Chiudi**.  
  
## <a name="give-the-columns-friendly-names"></a>Assegnare nomi descrittivi alle colonne  
 In questa attività verranno assegnati nomi descrittivi alle colonne della tabella Territorio vendita. Non è sempre necessario specificare nomi descrittivi per tabelle e/o colonne; questa attività, tuttavia, semplifica la navigazione del progetto di modello in Progettazione modelli nonché l'esplorazione degli oggetti e dei dati del modello in un elenco di campi di un'applicazione client da parte degli utenti.  
  
#### <a name="to-rename-columns-in-the-sales-territory-table"></a>Per rinominare le colonne nella tabella Territorio vendita  
  
-   In Progettazione modelli rinominare le colonne nella tabella **Territorio vendita** :  
  
     **Territorio vendita**  
  
    |Nome origine|Nome descrittivo|  
    |-----------------|-------------------|  
    |SalesTerritoryKey|ID territorio vendita|  
    |SalesTerritoryRegion|Area territorio vendita|  
    |SalesTerritoryCountry|Paese territorio vendita|  
    |SalesTerritoryGroup|Gruppo territorio vendita|  
  
## <a name="add-a-table-with-user-name-data"></a>Aggiungere una tabella con i dati del nome utente  
 Poiché nella tabella dimEmployee nel database di esempio AdventureWorksDW sono contenuti utenti del dominio AdventureWorks e i nomi di questi utenti non esistono nel proprio ambiente, è necessario creare una tabella nel modello contenente una piccola parte degli utenti effettivi dell'organizzazione, ad esempio tre utenti. Tali utenti verranno quindi aggiunti come membri al nuovo ruolo. Non sono necessarie le password per i nomi utente di esempio, ma saranno necessari nomi utente di Windows effettivi presenti nel proprio dominio.  
  
#### <a name="to-add-an-employee-security-table"></a>Per aggiungere una tabella Sicurezza dipendenti  
  
1.  Aprire Microsoft Excel creando un nuovo foglio di lavoro.  
  
2.  Copiare la tabella seguente, inclusa la riga di intestazione, quindi incollarla nel foglio di lavoro.  
  
    |ID dipendente|ID territorio vendita|Nome|Cognome|ID di accesso|  
    |-----------------|------------------------|----------------|---------------|--------------|  
    |1|2|\<nome utente >|\<cognome dell'utente >|\<dominio\nome utente >|  
    |1|3|\<nome utente >|\<cognome dell'utente >|\<dominio\nome utente >|  
    |2|4|\<nome utente >|\<cognome dell'utente >|\<dominio\nome utente >|  
    |3|5|\<nome utente >|\<cognome dell'utente >|\<dominio\nome utente >|  
  
3.  Nel nuovo foglio di lavoro sostituire il nome, il cognome e il dominio\nomeutente con i nomi e gli ID di accesso dei tre utenti dell'organizzazione. Inserire lo stesso utente nelle prime due righe per ID dipendente 1, a indicare che tale utente appartiene a più territori di vendita. Lasciare i campi ID dipendente e ID territorio vendita così come sono.  
  
4.  Salvare il foglio di lavoro come `Sample Employee`.  
  
5.  Nel foglio di lavoro, selezionare tutte le celle con i dati dei dipendenti, incluse le intestazioni, fare clic con il pulsante destro del mouse sui dati selezionati, quindi scegliere **Copia**.  
  
6.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Incolla** dal menu **Modifica**.  
  
     Se Incolla è disattivato, ovvero visualizzato in grigio, fare clic su una colonna di qualsiasi tabella nella finestra Progettazione modelli, quindi scegliere **Incolla** dal menu **Modifica**.  
  
7.  Nel **anteprima Incolla** nella finestra di dialogo **Table_name**, tipo `Employee Security`.  
  
8.  In **Dati da incollare**verificare che i dati includano tutti i dati dell'utente e le intestazioni del foglio di lavoro Dipendente di esempio.  
  
9. Verificare che l'opzione **Utilizza la prima riga per le intestazioni di colonna** sia selezionata, quindi fare clic su **OK**.  
  
     Verrà creata una nuova tabella denominata Sicurezza dipendenti con i dati dei dipendenti copiati dal foglio di lavoro Dipendente di esempio.  
  
## <a name="create-relationships-between-internet-sales-geography-and-sales-territory-table"></a>Creare relazioni tra le tabelle Vendite Internet, Geografia e Territorio vendita  
 Le tabelle Vendite Internet, Geografia e Territorio vendita contengono tutte una colonna comune, ID territorio vendita. Nella colonna ID territorio vendita nella tabella Territorio vendita sono contenuti valori con un ID diverso per ogni territorio di vendita.  
  
#### <a name="to-create-relationships-between-the-internet-sales-geography-and-the-sales-territory-table"></a>Per creare relazioni tra le tabelle Vendite Internet, Geografia e Territorio vendita  
  
1.  Nella tabella **Geografia** in Vista diagramma di Progettazione modelli fare clic e tenere premuto il pulsante del mouse sulla colonna **ID territorio vendita** , quindi trascinare il cursore nella colonna **ID territorio vendita** della tabella **Territorio vendita** e infine rilasciare il pulsante del mouse.  
  
2.  Nella tabella **Vendite Internet** fare clic e tenere premuto il pulsante del mouse sulla colonna **ID territorio vendita** , quindi trascinare il cursore nella colonna **ID territorio vendita** della tabella **Territorio vendita** e infine rilasciare il pulsante del mouse.  
  
     Si noti che la proprietà Active di questa relazione è False, a indicare che non è attiva, poiché la tabella Vendite Internet già contiene un'altra relazione attiva utilizzata nelle misure.  
  
## <a name="hide-the-employee-security-table-from-client-applications"></a>Nascondere la tabella Sicurezza dipendenti alle applicazioni client  
 In questa attività si nasconderà la tabella sicurezza dipendenti, impedendone la visualizzazione nell'elenco di campi di un'applicazione client. Tenere presente che nascondere una tabella non significa proteggerla. Gli utenti possono ancora eseguire una query sui dati della tabella Sicurezza dipendenti se sanno come fare. Per proteggere i dati della tabella Sicurezza dipendenti, impedendo agli utenti di potervi eseguire una query, verrà applicato un filtro in un'attività successiva.  
  
#### <a name="to-hide-the-employee-table-from-client-applications"></a>Per nascondere la tabella Dipendente alle applicazioni client  
  
-   In Vista diagramma di Progettazione modelli, fare clic con il pulsante destro del mouse sull'intestazione della tabella **Dipendente** , quindi scegliere **Nascondi a strumenti client**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Creare un ruolo utente Addetti alle vendite per territorio  
 In questa attività verrà creato un nuovo ruolo utente. Questo ruolo includerà un filtro di riga che definisce le righe della tabella Territorio vendita visibili agli utenti. Il filtro viene quindi applicato nella direzione della relazione uno-a-molti a tutte le altre tabelle correlate alla tabella Territorio vendita. Verrà inoltre applicato un semplice filtro per proteggere l'intera tabella Sicurezza dipendenti impedendone l'esecuzione di query da parte di tutti gli utenti membri del ruolo.  
  
> [!NOTE]  
>  Il ruolo Addetti alle vendite per territorio creato in questa lezione consente ai membri di esplorare o eseguire query solo sui dati di vendita relativi al territorio di vendita a cui appartengono. Se si aggiunge un utente come membro a addetti alle vendite dal ruolo territorio presente anche come un membro in un ruolo creato nella [lezione 12: Creare ruoli](../analysis-services/lesson-11-create-roles.md), si otterrà una combinazione di autorizzazioni. Se un utente è membro di più ruoli, le autorizzazioni e i filtri di riga definiti per ogni ruolo sono cumulativi, ovvero l'utente disporrà di maggiori autorizzazioni determinate dalla combinazione dei ruoli.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Per creare un ruolo utente Addetti alle vendite per territorio  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] fare clic sul menu **Modello** e quindi su **Ruoli**.  
  
2.  Nella finestra di dialogo **Gestione ruoli** fare clic su **Nuovo**.  
  
     All'elenco verrà aggiunto un nuovo ruolo con l'autorizzazione Nessuno.  
  
3.  Fare clic sul nuovo ruolo, quindi nella **Name** colonna, rinominare il ruolo in `Sales Employees by Territory`.  
  
4.  Nella colonna **Autorizzazioni** fare clic nell'elenco a discesa, quindi selezionare l'autorizzazione **Lettura** .  
  
5.  Fare clic sulla scheda **Membri**, quindi su **Aggiungi**.  
  
6.  Nella finestra di dialogo **Seleziona utente o gruppo** in **Immettere i nomi degli oggetti da selezionare**digitare il primo nome utente di esempio usato per la creazione della tabella Sicurezza dipendenti. Fare clic su **Controlla nomi** per verificare che il nome utente sia valido, quindi fare clic su **OK**.  
  
     Ripetere questo passaggio aggiungendo gli altri nomi utente di esempio utilizzati per la creazione della tabella Sicurezza dipendenti.  
  
7.  Fare clic sulla scheda **Filtri di riga** .  
  
8.  Per il `Employee Security` tabella di **filtro DAX** colonna, digitare la formula seguente.  
  
     `=FALSE()`  
  
     Dopo avere completato la compilazione della formula, premere INVIO.  
  
     Questa formula specifica che tutte le colonne vengono risolte nella condizione booleana false. Pertanto, non sarà possibile eseguire query in alcuna colonna della tabella Sicurezza dipendenti da parte dei membri del ruolo utente Addetti alle vendite per territorio.  
  
9. Per la tabella **Territorio vendita** digitare la formula seguente.  
  
     `='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])`  
  
     Dopo avere completato la compilazione della formula, premere INVIO.  
  
     In questa formula la funzione LOOKUPVALUE restituisce tutti i valori per la colonna Sicurezza dipendenti[ID territorio vendita], dove Sicurezza dipendenti[ID di accesso] corrisponde al nome utente di Windows attualmente connesso e Sicurezza dipendenti[ID territorio vendita] corrisponde a Territorio vendita[ID territorio vendita].  
  
     Il set di ID territorio vendita restituito da LOOKUPVALUE viene quindi utilizzato per limitare le righe visualizzate nella tabella Territorio vendita. Verranno visualizzate solo le righe il cui ID territorio vendita è presente nel set di ID restituito dalla funzione LOOKUPVALUE.  
  
10. Nella finestra di dialogo Gestione ruoli fare clic su **OK**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Testare il ruolo utente Addetti alle vendite per territorio  
 In questa attività verrà utilizzata la funzionalità Analizza in Excel di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per testare l'efficacia del ruolo utente Addetti alle vendite per territorio. Specificare uno dei nomi utente aggiunti nella tabella Sicurezza dipendenti come membro del ruolo. Questo nome utente verrà quindi utilizzato come nome utente effettivo nella connessione creata tra Excel e il modello.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Per testare il ruolo utente Addetti alle vendite per territorio  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] fare clic sul menu **Modello** e quindi scegliere **Analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** in **Specificare il nome utente o il ruolo da usare per la connessione al modello**selezionare **Altro utente di Windows**, quindi fare clic su **Sfoglia**.  
  
3.  Nella finestra di dialogo **Seleziona utente o gruppo** in **Immettere i nomi degli oggetti da selezionare**digitare uno dei nomi utente inclusi nella tabella Dipendente, quindi fare clic su **Controlla nomi**.  
  
4.  Fare clic su **OK** per chiudere la finestra di dialogo **Seleziona utente o gruppo**, quindi fare clic su **OK** per chiudere la finestra di dialogo **Analizza in Excel**.  
  
     Verrà aperto Excel con una nuova cartella di lavoro. Verrà creata automaticamente una tabella pivot. L'elenco di campi tabella pivot include la maggior parte dei campi dati disponibili nel nuovo modello.  
  
     Si noti che la tabella Sicurezza dipendenti non è visibile nell'elenco di campi tabella pivot in quanto in un'attività precedente si è scelto di nascondere questa tabella agli strumenti client.  
  
5.  Nell'elenco **Campo tabella pivot** in **∑ Internet Sales** (misure) selezionare la misura **Internet Total Sales** . La misura verrà immessa nei campi **Valori**.  
  
6.  Nell'elenco **Campo tabella pivot** selezionare la colonna **ID territorio vendita** della tabella **Territorio vendita** . La colonna verrà immessa nei campi **Etichette di riga**.  
  
     Si noti che le cifre delle vendite Internet vengono visualizzate solo per l'area a cui appartiene il nome utente effettivo utilizzato. Se si seleziona un'altra colonna, ad esempio Città della tabella Geografia, come campo Etichette di riga, verranno visualizzate solo le città del territorio di vendita a cui appartiene l'utente effettivo.  
  
     Questo utente non può esplorare né eseguire una query sui dati delle vendite Internet per territori diversi da quello a cui appartiene poiché il filtro di riga definito per la tabella Territorio vendita nel ruolo utente Addetti alle vendite per territorio protegge in effetti tutti i dati correlati agli altri territori di vendita.  
  
## <a name="see-also"></a>Vedere anche  
 [USERNAME Function &#40;DAX&#41;](https://msdn.microsoft.com/library/hh230954.aspx)   
 [Funzione LOOKUPVALUE &#40;DAX&#41;](https://msdn.microsoft.com/library/gg492170.aspx)   
 [Funzione CUSTOMDATA &#40;DAX&#41;](https://msdn.microsoft.com/library/hh213140.aspx)  
  
  
