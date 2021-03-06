---
title: Oggetto SqlXmlCommand (classi gestite SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 736345b7ee5b9c3e40f0ae34fe139cb911cad42f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740514"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a>Oggetto SqlXmlCommand (classi gestite SQLXML)
  Si tratta del costruttore per l'oggetto SqlXmlCommand:  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 In cui `cnString` è la stringa di connessione ADO o OLEDB che identifica il server, database e le informazioni di accesso, ad esempio, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.  
  
 Nella stringa di connessione `Provider` deve essere SQLOLEDB e `Data Provider` non deve essere incluso nella stringa del provider.  
  
 Per un esempio funzionante, vedere [l'esecuzione di query SQL &#40;classi gestite SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
## <a name="methods"></a>Metodi  
 Oggetto TheSqlXmlCommand supporta diversi metodi, inclusi i seguenti metodi per l'esecuzione di un comando:  
  
 void ExecuteNonQuery()  
 Esegue il comando, ma non restituisce alcun valore. Questo metodo è utile se si desidera eseguire un comando senza query, ovvero un comando che non restituisca alcun valore. Un esempio di questo comportamento consiste nell'eseguire un updategram o un Diffgram che aggiorna record ma non restituisce alcun valore.  
  
 Stream ExecuteStream()  
 Restituisce un nuovo oggetto Stream. Questo metodo è utile quando si desidera che i risultati della query vengano restituiti in un nuovo flusso. Per un esempio funzionante, vedere [l'esecuzione di query SQL &#40;classi gestite SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 public void ExecuteToStream (Stream outputStream)  
 Scrive i risultati della query in un flusso esistente. Questo metodo è utile quando si dispone di un flusso a cui è necessario vengano aggiunti (ad esempio, affinché i risultati della query scritte le System.Web.HttpResponse.OutputStream) i risultati. Per un esempio funzionante, vedere [l'esecuzione di query SQL &#40;classi gestite SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 XmlReader ExecuteXmlReader()  
 Restituisce un oggetto XmlReader. È possibile utilizzare questo metodo per modificare direttamente i dati nell'oggetto XmlReader o collegare l'architettura concatenabile di System. Xml. Per ulteriori informazioni, vedere la documentazione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Per un esempio funzionante, vedere [l'esecuzione di query SQL usando il metodo ExecuteXMLReader](executing-sql-queries-by-using-the-executexmlreader-method.md).  
  
 Oggetto TheSqlXmlCommand supporta anche questi altri metodi:  
  
 SqlXmlParameter CreateParameter()  
 Crea un oggetto SqlXmlParameter. È possibile impostare i valori per il *Name* e *valore* i parametri di questo oggetto. Questo metodo è utile se si desidera passare parametri a un comando. Per un esempio funzionante, vedere [l'esecuzione di query SQL &#40;classi gestite SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 void ClearParameters()  
 Cancella i parametri creati per un oggetto comando specifico. Questo metodo è utile se si desidera eseguire più query sullo stesso oggetto comando.  
  
## <a name="properties"></a>Proprietà  
 L'oggetto SqlXmlCommand supporta anche queste proprietà:  
  
 ClientSideXml  
 Se impostata su True, specifica che la conversione del set di righe in XML deve verificarsi nel client anziché nel server. Questa proprietà è utile quando si desidera spostare il carico delle prestazioni nel livello intermedio. La proprietà consente inoltre di eseguire il wrapping delle stored procedure esistenti con FOR XML per ottenere output XML.  
  
 SchemaPath  
 Nome dello schema di mapping insieme al percorso di directory, ad esempio C:\x\y\Schema.xml. Questa proprietà è utile per specificare uno schema di mapping per query XPath. Il percorso specificato può essere assoluto o relativo. Se il percorso è relativo, il percorso di base specificato nel percorso di Base viene usato per risolvere il percorso relativo. Se non è specificato alcun percorso di base, il percorso relativo è tale rispetto alla directory corrente. Per un esempio funzionante, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 XslPath  
 Nome del file XSL insieme al percorso di directory. Il percorso specificato può essere assoluto o relativo. Se il percorso è relativo, il percorso di base specificato nel percorso di Base viene usato per risolvere il percorso relativo. Se non è specificato alcun percorso di base, il percorso relativo è tale rispetto alla directory corrente. Per un esempio funzionante, vedere [applica una trasformazione XSL &#40;classi gestite SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 Percorso di base  
 Percorso di base (un percorso di directory). Questa proprietà è utile per risolvere un percorso relativo specificato per un file XSL (tramite xslpath-proprietà), un file di schema di mapping (utilizzando schemapath-proprietà) o un riferimento allo schema esterno in un modello XML (specificato tramite la `mapping-schema` attributo).  
  
 OutputEncoding  
 Specifica la codifica per il flusso restituito all'esecuzione del comando. Questa proprietà è utile per richiedere una codifica specifica per il flusso restituito. Alcune codifiche di uso comune sono UTF-8, ANSI e Unicode. La codifica predefinita è UTF-8.  
  
 Spazi dei nomi  
 Consente l'esecuzione di query XPath che utilizzano spazi dei nomi. Per altre informazioni sulle query XPath con spazi dei nomi, vedere [l'esecuzione di query XPath con spazi dei nomi &#40;classi gestite SQLXML&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md). Per un esempio funzionante, vedere [l'esecuzione di query XPath &#40;classi gestite SQLXML&#41;](executing-xpath-queries-sqlxml-managed-classes.md).  
  
 RootTag  
 Fornisce il singolo elemento radice per un documento XML generato dall'esecuzione di comandi. Un documento XML valido richiede un singolo tag di livello radice. Se il comando eseguito genera un frammento XML, senza singolo elemento di livello principale, è possibile specificare un elemento radice per il documento XML restituito. Per un esempio funzionante, vedere [applica una trasformazione XSL &#40;classi gestite SQLXML&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).  
  
 CommandText  
 Testo del comando. Questa proprietà viene utilizzata per specificare il testo del comando che si desidera eseguire. Per un esempio funzionante, vedere [l'esecuzione di query SQL &#40;classi gestite SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).  
  
 CommandStream  
 Flusso del comando. Questa proprietà è utile se si desidera eseguire un comando da un file, ad esempio un modello XML. Quando si utilizza CommandStream, solo **"Template"**, **"UpdateGram"** e **"DiffGram" CommandType** sono supportati i valori. Per un esempio funzionante, vedere [l'esecuzione di file di modello tramite la proprietà CommandStream](executing-template-files-by-using-the-commandstream-property.md).  
  
 CommandType  
 Identifica il tipo di comando. Questa proprietà viene utilizzata per specificare il tipo di comando che si desidera eseguire. I valori nella tabella seguente determinano il tipo del comando. Per un esempio funzionante, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SqlXmlCommandType.Sql|Esegue un comando SQL, ad esempio `SELECT * FROM Employees FOR XML AUTO`.|  
|SqlXmlCommandType.XPath|Esegue un comando XPath, ad esempio `Employees[@EmployeeID=1]`.|  
|SqlXmlCommandType.Template|Esegue un modello XML.|  
|SqlXmlCommandType.TemplateFile|Esegue un file di modello nel percorso specificato.|  
|SqlXmlCommandType.UpdateGram|Esegue un updategram.|  
|SqlXmlCommandType.Diffgram|Esegue un Diffgram.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto SqlXmlParameter &#40;classi gestite SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)   
 [Oggetto SqlXmlAdapter &#40;classi gestite SQLXML&#41;](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
