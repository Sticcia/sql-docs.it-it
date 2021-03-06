---
title: I BLOB e gli oggetti OLE | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e459682da63bac8359fa8310233c234e456f4e5b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195222"
---
# <a name="blobs-and-ole-objects"></a>Oggetti BLOB e OLE
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **ISequentialStream** interfaccia per supportare i consumer di accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **testo**, **immagine**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, e i tipi di dati xml come binary large object (BLOB ). Il metodo **Read** in **ISequentialStream** consente al consumer di recuperare una quantità elevata di dati in blocchi gestibili.  
  
 Per un esempio che illustri questa caratteristica, vedere [impostare dati di grandi dimensioni &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client può utilizzare un consumer implementati **IStorage** interfaccia quando il consumer fornisce il puntatore di interfaccia in una funzione di accesso associata per la modifica dei dati.  
  
 Per i tipi di dati di valori di grandi dimensioni, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client controlla presupposti per le dimensioni tipo in **IRowset** e interfacce DDL. Le colonne con **varchar**, **nvarchar**, e **varbinary** tipi di dati con dimensione massima è impostata su un valore illimitato verranno rappresentati come ISLONG mediante le interfacce e i set di righe dello schema restituzione di tipi di dati di colonna.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **varchar (max)**, **varbinary (max)** e **nvarchar (max)** tipi come DBTYPE_STR, DBTYPE_BYTES e DbType WSTR rispettivamente.  
  
 In un'applicazione è possibile utilizzare questi tipi nei modi seguenti:  
  
-   Eseguire l'associazione come tipo (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Se le dimensioni de buffer non sono sufficienti, si verificherà il troncamento, esattamente come accade per questi tipi nelle release precedenti, anche se ora sono disponibili valori più grandi.  
  
-   Eseguire l'associazione come tipo e specificare DBTYPE_BYREF.  
  
-   Eseguire l'associazione come DBTYPE_IUNKNOWN e utilizzare il flusso.  
  
 Se si esegue l'associazione a DBTYPE_IUNKNOWN, viene utilizzata la funzionalità di flusso di ISequentialStream. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta i parametri di output di associazione come DBTYPE_IUNKNOWN per i tipi di dati di valori di grandi dimensioni facilitare scenari in cui una stored procedure restituisce questi dati tipi come valori restituiti che verranno esposti come DBTYPE_IUNKNOWN al client.  
  
## <a name="storage-object-limitations"></a>Limitazioni degli oggetti di archiviazione  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client può supportare solo un oggetto di archiviazione open singolo. I tentativi di aprire più di un oggetto di archiviazione (per ottenere un riferimento su più di un puntatore di interfaccia **ISequentialStream**) restituiscono DBSTATUS_E_CANTCREATE.  
  
-   Nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client, il valore predefinito della proprietà di sola lettura DBPROP_BLOCKINGSTORAGEOBJECTS è VARIANT_TRUE. Tale valore indica che se un oggetto di archiviazione è attivo, alcuni metodi (diversi da quelli degli oggetti di archiviazione) non riusciranno e verrà restituito E_UNEXPECTED.  
  
-   La lunghezza dei dati presentati da un oggetto di archiviazione implementato consumer deve essere resa nota al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client quando viene creata la funzione di accesso di riga che fa riferimento all'oggetto di archiviazione. Il consumer deve associare un indicatore di lunghezza nella struttura DBBINDING utilizzata per la creazione della funzione di accesso.  
  
-   Se una riga contiene più di un valore di dati di grandi dimensioni e DBPROP_ACCESSORDER non è DBPROPVAL_AO_RANDOM, il consumer deve utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client provider supportato dal cursore del set di righe per recuperare i dati di riga o elaborare dati di grandi dimensioni tutti i valori prima di recuperare altri valori di riga. Se DBPROP_ACCESSORDER è DBPROPVAL_AO_RANDOM, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client memorizza nella cache tutti i tipi di dati xml come oggetti binari di grandi dimensioni (BLOB) in modo che sia accessibile in qualsiasi ordine.  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Recupero di dati di grandi dimensioni](getting-large-data.md)  
  
-   [Impostazione di dati di grandi dimensioni](setting-large-data.md)  
  
-   [Supporto del flusso per parametri di output BLOB](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Uso di tipi valore di grandi dimensioni](../native-client/features/using-large-value-types.md)  
  
  
