---
title: Informazioni sulle proprietà OLE DB | Documenti di Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e7c010beaf3aefa4f73314d8576a066dca6a167
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62638073"
---
# <a name="about-ole-db-properties"></a>Informazioni sulle proprietà OLE DB
  I consumer impostano i valori delle proprietà per richiedere specifici comportamenti degli oggetti. Utilizzano, ad esempio, proprietà per specificare le interfacce che devono essere esposte da un set di righe. I consumer recuperano i valori delle proprietà per determinare le funzionalità di un oggetto, ad esempio un set di righe, una sessione o un oggetto origine dati.  
  
 Ogni proprietà presenta un valore, un tipo, una descrizione e un attributo di lettura/scrittura e, per le proprietà del set di righe, un indicatore che specifica se la proprietà può essere applicata alle singole colonne.  
  
 Una proprietà viene identificata da un GUID e da un numero intero che rappresenta l'ID della proprietà. Un set di proprietà è un set di tutte le proprietà che condividono lo stesso GUID. Oltre alla proprietà OLE DB predefinita imposta, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client implementa proprietà e set di proprietà specifiche del provider in essi contenuti. Ogni proprietà appartiene a uno o più gruppi di proprietà. Un gruppo di proprietà è il gruppo di tutte le proprietà che si applicano a un particolare oggetto. Alcuni gruppi di proprietà includono i seguenti gruppi di proprietà: di inizializzazione, dell'origine dati, di sessione, del set di righe, di tabella e di colonna. In ognuno di questi gruppi sono presenti proprietà.  
  
 L'impostazione dei valori delle proprietà comporta:  
  
1.  Determinazione delle proprietà per le quali impostare i valori.  
  
2.  Determinazione dei set di proprietà che contengono le proprietà identificate.  
  
3.  Allocazione di una matrice di strutture DBPROPSET, una per ogni set di proprietà identificato.  
  
4.  Allocazione di una matrice di strutture DBPROP, una per ogni set di proprietà. Il numero di elementi di ogni matrice è il numero di proprietà (identificate nel passaggio 1) che appartengono al set di proprietà.  
  
5.  Inserimento di dati nella struttura DBPROP per ogni proprietà.  
  
6.  Inserimento di informazioni (GUID del set di proprietà, conteggio del numero di elementi e un puntatore alla matrice DBPROP corrispondente) nella struttura DBPROPSET per ogni set di proprietà.  
  
7.  Chiamata a un metodo per impostare proprietà e passaggio del conteggio e della matrice delle strutture DBPROPSET.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione del Provider SQL Server Native Client OLE DB](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Proprietà (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
