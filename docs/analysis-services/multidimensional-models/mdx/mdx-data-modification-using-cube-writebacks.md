---
title: Utilizzo dei writeback dei cubi (MDX) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc950c69a25ff976b8cdf1cd7cb4252c2584e0af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740123"
---
# <a name="mdx-data-modification---using-cube-writebacks"></a>Modifica dei dati MDX - Uso di writeback dei cubi
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  È possibile aggiornare un cubo usando l'istruzione [UPDATE CUBE](../../../mdx/mdx-data-manipulation-update-cube.md) . Tale istruzione consente di aggiornare una tupla con un valore specifico. Per utilizzare in modo efficace l'istruzione UPDATE CUBE per l'aggiornamento di un cubo, è importante conoscere la sintassi dell'istruzione, le condizioni di errore che possono verificarsi e i possibili effetti degli aggiornamenti su un cubo.  
  
## <a name="update-cube-statement-syntax"></a>Sintassi dell'istruzione UPDATE CUBE  
 La sintassi dell'istruzione UPDATE CUBE è la seguente:  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 Se per la tupla non è stato specificato un set completo di coordinate, per le coordinate non specificate verrà utilizzato il membro predefinito della gerarchia. La tupla identificata deve fare riferimento a una cella aggregata tramite la funzione [Sum](../../../mdx/sum-mdx.md) e non deve includere celle con coordinate costituite da membri calcolati.  
  
 È possibile pensare all'istruzione UPDATE CUBE come a una subroutine che genera una serie di operazioni di writeback singole su celle atomiche. Tutte queste operazioni di writeback singole contribuiscono a generare la somma specificata.  
  
> [!NOTE]  
>  Quando le celle aggiornate non si sovrappongono, la proprietà della stringa di connessione **Update Isolation Level** può essere usata per migliorare le prestazioni di UPDATE CUBE. Per altre informazioni, vedere <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.  
  
## <a name="example"></a>Esempio  
 È possibile eseguire il test di UPDATE CUBE con il gruppo di misure relativo agli obiettivi vendita nel cubo Adventure Works. Questo gruppo di misure è costituito da misure aggregate in base a SUM, vale a dire un requisito per UPDATE CUBE.  
  
1.  Abilitare il writeback per il gruppo di misure relativo agli obiettivi vendita nel database Adventure Works. In Management Studio fare clic con il pulsante destro del mouse su un gruppo di misure, scegliere **Opzioni writeback**, quindi **Abilita writeback**.  
  
     Viene visualizzata una nuova tabella writeback nella cartella Writeback. Il nome della tabella è WriteTable_Fact Sales Quota.  
  
2.  Aprire una finestra Query MDX. Eseguire l'istruzione SELECT riportata di seguito per visualizzare il valore originale:  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     Vengono visualizzate le quote vendite di ogni rappresentante.  
  
3.  Eseguire l'istruzione UPDATE CUBE per eseguire il writeback di un nuovo valore. In questo esempio la quota vendite viene impostata su 0. Poiché il nuovo valore è pari a 0, non specificare un metodo di allocazione.  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  Eseguire nuovamente l'istruzione SELECT. A questo punto viene visualizzato zero per le quote.  
  
 Il valore writeback è vincolato alla sessione corrente. Per rendere persistente il valore negli utenti e nelle sessioni, elaborare la tabella writeback. In Management Studio fare clic con il pulsante destro del mouse su WriteTable_Fact Sales Quota e scegliere **Elabora**.  
  
 Per specificare un metodo di allocazione, il nuovo valore deve essere maggiore di zero. In questo esempio il nuovo valore di Sales Amount Quota è pari a due milioni e tramite il metodo di allocazione l'importo viene distribuito a tutti i rappresentanti.  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a>Condizioni di errore  
 Nella tabella seguente vengono descritte le possibili cause di errore dei writeback e le conseguenze di tali errori.  
  
|Condizione di errore|Risultato|  
|---------------------|------------|  
|L'aggiornamento include membri incompatibili della stessa dimensione.|L'aggiornamento non verrà eseguito. lo spazio del cubo non conterrà la cella a cui è stato fatto riferimento.|  
|L'aggiornamento include una misura originata da una misura di un tipo senza segno.|L'aggiornamento non verrà eseguito. Per gli incrementi è necessario che la misura possa contenere un valore negativo.|  
|L'aggiornamento include una misura con un'aggregazione diversa dalla somma.|Verrà generato un errore.|  
|È stato tentato un aggiornamento su un sottocubo.|Verrà generato un errore.|  
  
## <a name="affect-of-cube-changes"></a>Effetti delle modifiche al cubo  
 Le modifiche seguenti non hanno effetto su un writeback:  
  
-   Elaborazione di un cubo, dei gruppi di misure del cubo o delle dimensioni del cubo.  
  
-   Aggiunta di attributi a una dimensione.  
  
-   Aggiunta di una nuova dimensione.  
  
-   Eliminazione di una dimensione che non include il writeback.  
  
-   Aggiunta, modifica o rimozione di una gerarchia.  
  
-   Aggiunta di una nuova misura.  
  
 Le modifiche seguenti non possono essere eseguite senza rimuovere i dati di writeback:  
  
-   Eliminazione di un attributo o della relativa gerarchia, se l'attributo è incluso nel writeback. È inclusa la rimozione esplicita dell'attributo, o della relativa gerarchia, o la rimozione della dimensione padre dell'attributo.  
  
-   Eliminazione di una misura inclusa nel writeback.  
  
-   Aggiunta di un attributo privo del livello **(All)** a una dimensione inclusa nel writeback.  
  
-   Modifica della granularità di una dimensione inclusa nel writeback.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica dei dati &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-data-modification-modifying-data.md)  
  
  
