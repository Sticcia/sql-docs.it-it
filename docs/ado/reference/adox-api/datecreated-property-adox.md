---
title: Proprietà DateCreated (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46c6017f7b0c9bbeeb654c2cf6aa3965aafff8e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281589"
---
# <a name="datecreated-property-adox"></a>Proprietà DateCreated (ADOX)
Indica la data che di creazione dell'oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **Variant** valore che specifica la data di creazione. Il valore è null se **DateCreated** non è supportato dal provider.  
  
## <a name="remarks"></a>Note  
 Il **DateCreated** proprietà è null per gli oggetti appena aggiunti. Dopo aver aggiunto un nuovo [vista](../../../ado/reference/adox-api/view-object-adox.md) o [Procedure](../../../ado/reference/adox-api/procedure-object-adox.md), è necessario chiamare il [Aggiorna](../../../ado/reference/ado-api/refresh-method-ado.md) metodo il [viste](../../../ado/reference/adox-api/views-collection-adox.md) o [procedure ](../../../ado/reference/adox-api/procedures-collection-adox.md) insieme per ottenere valori per il **DateCreated** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Oggetto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà DateCreated e DateModified (esempio di proprietà (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Proprietà DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
