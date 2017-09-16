---
title: Esempio di metodo OpenSchema (VB) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- OpenSchema method [ADO], Visual Basic example
ms.assetid: 455a02f0-8143-4562-8648-8fb45ffd334c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75e6a7d65eca38c217b6868dc3fc2a08c4f0eb54
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="openschema-method-example-vb"></a>Esempio di metodo OpenSchema (VB)
Questo esempio viene utilizzato il [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) metodo per visualizzare il nome e il tipo di ogni tabella di ***Pubs*** database.  
  
```  
'BeginOpenSchemaVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim rstSchema As ADODB.Recordset  
    Dim strCnxn As String  
  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstSchema = Cnxn.OpenSchema(adSchemaTables)  
  
    Do Until rstSchema.EOF  
        Debug.Print "Table name: " & _  
            rstSchema!TABLE_NAME & vbCr & _  
            "Table type: " & rstSchema!TABLE_TYPE & vbCr  
        rstSchema.MoveNext  
    Loop  
  
    ' clean up  
    rstSchema.Close  
    Cnxn.Close  
    Set rstSchema = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstSchema Is Nothing Then  
        If rstSchema.State = adStateOpen Then rstSchema.Close  
    End If  
    Set rstSchema = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndOpenSchemaVB  
```  
  
 Questo esempio viene specificato un vincolo di query TABLE_TYPE nel **OpenSchema** metodo ***criteri*** argomento. Di conseguenza, solo le informazioni sullo schema per le viste specificate nel ***Pubs*** database vengono restituiti. Nell'esempio viene quindi visualizzato il nome e i tipi di ogni tabella.  
  
```  
Attribute VB_Name = "OpenSchema"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo OpenSchema](../../../ado/reference/ado-api/openschema-method.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)