---
title: Mediante i messaggi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e67d8818fb20d339c4166f606d15e0f7dbceced
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63015263"
---
# <a name="using-messages"></a>Utilizzo di messaggi
  In SMO i messaggi di sistema sono rappresentati dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> che appartiene all'oggetto `Server`. Poiché i messaggi di sistema non possono essere modificati, le proprietà dell'oggetto `SystemMessage` sono di sola lettura.  
  
 In SMO i messaggi definiti dall'utente sono rappresentati a livello di codice dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>. È possibile individuare i messaggi definiti dall'utente esistenti scorrendo la raccolta. È possibile creare nuovi messaggi definiti dall'utente creando un'istanza di un nuovo oggetto `UserDefinedMessage` e impostando le proprietà appropriate.  
  
## <a name="examples"></a>Esempi  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual Basic SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) e [creare un Visual C#&#35; progetto SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Individuazione di un messaggio di sistema particolare in Visual Basic  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Individuazione di un messaggio di sistema particolare in Visual C#  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>Individuazione di un messaggio di sistema particolare in PowerShell  
 Nell'esempio di codice viene illustrato come identificare un messaggio di sistema in base al numero ID e come visualizzarlo.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Aggiunta di un nuovo messaggio definito dall'utente in Visual Basic  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```  
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Aggiunta di un nuovo messaggio definito dall'utente in Visual C#  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```  
{  
  
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>Aggiunta di un nuovo messaggio definito dall'utente in PowerShell  
 Nell'esempio di codice viene illustrato come creare un messaggio definito dall'utente con un ID maggiore di 50000.  
  
```  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message  
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
