---
title: Catalogo di esempio di proprietà ActiveConnection (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveConnection property [ADOX], VC++ example
ms.assetid: 518905a9-6044-4194-af6c-84952d95939d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30f7f4f4165b608070fafa5464e64c9c238651c7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184179"
---
# <a name="catalog-activeconnection-property-example-vc"></a>Esempio della proprietà ActiveConnection di Catalog (VC++)
Impostando il [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) proprietà a una connessione valida, aprire "aperta" nel catalogo. Da un catalogo aperto, è possibile accedere gli oggetti dello schema contenuti all'interno di tale catalogo.  
  
```  
// CatalogActiveConnectionCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void OpenConnectionX();  
void OpenConnectionWithStringX();  
  
int main() {  
   if ( FAILED( ::CoInitialize(NULL) ) )  
      return -1;  
  
   OpenConnectionX();  
   OpenConnectionWithStringX();  
   ::CoUninitialize();  
}  
  
void OpenConnectionX() {  
   HRESULT hr = S_OK;  
  
   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.  
   _CatalogPtr m_pCatalog = NULL;  
  
   // Define ADODB object pointers  
   ADODB::_ConnectionPtr m_pCnn = NULL;  
  
   // Define string variables.  
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");  
  
   try {  
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
      m_pCnn->Open(strcnn, "", "", NULL);  
      m_pCatalog->PutActiveConnection(_variant_t((IDispatch *) m_pCnn));  
      _variant_t vIndex = (short) 0;  
      cout<<m_pCatalog->Tables->GetItem(vIndex)->Type<<endl;  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in OpenConnectionX...." << endl;  
   }  
  
   if (m_pCnn)  
      if (m_pCnn->State == 1)  
         m_pCnn->Close();  
}  
  
void OpenConnectionWithStringX() {  
   HRESULT hr = S_OK;  
  
   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.  
   _CatalogPtr m_pCatalog = NULL;  
  
   // Define string variables.  
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");  
  
   try {  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
      m_pCatalog->PutActiveConnection(strcnn);  
      _variant_t vIndex = (short) 0;  
      cout<<m_pCatalog->Tables->GetItem(vIndex)->Type<<endl;  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in OpenConnectionWithStringX...." << endl;  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
