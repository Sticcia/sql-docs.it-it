---
title: Aggiungere utenti e gruppi, esempio di metodi ChangePassword (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff3e82608c83646198bbf74f537ca76be427d4bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63288192"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Esempio dei metodi Append di Groups e Users e del metodo ChangePassword (VB)
Questo esempio viene illustrato il [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) metodo di [gruppi](../../../ado/reference/adox-api/groups-collection-adox.md), così come il [Append](../../../ado/reference/adox-api/append-method-adox-users.md) metodo [utenti](../../../ado/reference/adox-api/users-collection-adox.md) aggiungendo un nuovo [Gruppo](../../../ado/reference/adox-api/group-object-adox.md) e un nuovo [utente](../../../ado/reference/adox-api/user-object-adox.md) al sistema. Il nuovo **gruppo** viene aggiunto al **gruppi** raccolta del nuovo **utente**. Di conseguenza, il nuovo **utente** viene aggiunto per il **gruppo**. Inoltre, il [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) metodo viene utilizzato per specificare le **utente** password.  
  
> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** oppure **Integrated Security = SSPI** anziché un ID utente e password informazioni nella stringa di connessione.  
  
```  
' BeginGroupVB  
Sub Main()  
    On Error GoTo GroupXError  
  
    Dim cat As ADOX.Catalog  
    Dim usrNew As ADOX.User  
    Dim usrLoop As ADOX.User  
    Dim grpLoop As ADOX.Group  
  
    Set cat = New ADOX.Catalog  
  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';" & _  
        "jet oledb:system database=" & _  
        "'system.mdw'"  
  
    With cat  
        'Create and append new group with a string.  
        .Groups.Append "Accounting"  
  
        ' Create and append new user with an object.  
        Set usrNew = New ADOX.User  
        usrNew.Name = "Pat Smith"  
        usrNew.ChangePassword "", "Password1"  
        .Users.Append usrNew  
  
        ' Make the user Pat Smith a member of the  
        ' Accounting group by creating and adding the  
        ' appropriate Group object to the user's Groups  
        ' collection. The same is accomplished if a User  
        ' object representing Pat Smith is created and  
        ' appended to the Accounting group Users collection  
        usrNew.Groups.Append "Accounting"  
  
        ' Enumerate all User objects in the  
        ' catalog's Users collection.  
        For Each usrLoop In .Users  
            Debug.Print "  " & usrLoop.Name  
            Debug.Print "    Belongs to these groups:"  
            ' Enumerate all Group objects in each User  
            ' object's Groups collection.  
            If usrLoop.Groups.Count <> 0 Then  
                For Each grpLoop In usrLoop.Groups  
                    Debug.Print "    " & grpLoop.Name  
                Next grpLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next usrLoop  
  
        ' Enumerate all Group objects in the default  
        ' workspace's Groups collection.  
        For Each grpLoop In .Groups  
            Debug.Print "  " & grpLoop.Name  
            Debug.Print "    Has as its members:"  
            ' Enumerate all User objects in each Group  
            ' object's Users collection.  
            If grpLoop.Users.Count <> 0 Then  
                For Each usrLoop In grpLoop.Users  
                    Debug.Print "    " & usrLoop.Name  
                Next usrLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next grpLoop  
  
        ' Delete new User and Group objects because this  
        ' is only a demonstration.  
        ' These two line are commented out because the sub "OwnersX" uses  
        ' the group "Accounting".  
'        .Users.Delete "Pat Smith"  
'        .Groups.Delete "Accounting"  
  
    End With  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set usrNew = Nothing  
    Exit Sub  
  
GroupXError:  
  
    Set cat = Nothing  
    Set usrNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndGroupVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Append (metodo) (oggetti Group ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (User ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Oggetto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Metodo ChangePassword (ADOX)](../../../ado/reference/adox-api/changepassword-method-adox.md)   
 [Oggetto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)   
 [Raccolta di gruppi (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)   
 [Raccolta di oggetti User (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
