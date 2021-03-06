---
title: Uso di una stored procedure con parametri di input | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2b85c7ff9943f2c83109b18000adf7c2456b7a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635049"
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Utilizzo di una stored procedure con parametri di input

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Una stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che è possibile chiamare è una procedura contenente uno o più parametri IN, ovvero i parametri utilizzabili per passare i dati alla stored procedure. Tramite [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] viene fornita la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), che è possibile usare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.

Quando si chiama una stored procedure usando il driver JDBC con parametri IN, è necessario usare la sequenza di escape SQL `call` insieme al metodo [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La sintassi della sequenza di escape `call` con parametri IN è la seguente:

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Per altre informazioni sulle sequenze di escape SQL, vedere [usando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Quando si costruisce la sequenza di escape `call`, specificare i parametri IN usando il carattere ? (punto interrogativo), che funge da segnaposto per i valori di parametro che verranno passati alla stored procedure. Per specificare un valore per un parametro, è possibile usare uno dei metodi setter della classe SQLServerPreparedStatement. Il metodo Set che è possibile utilizzare è determinato dal tipo di dati del parametro IN.

Quando si passa un valore al metodo Set, è necessario specificare non solo il valore effettivo da utilizzare nel parametro, ma anche la posizione ordinale del parametro nella stored procedure. Se, ad esempio, la stored procedure contiene un solo parametro IN, il relativo valore ordinale sarà 1. Se la stored procedure contiene due parametri, il primo valore ordinale sarà 1 e il secondo sarà 2.

Per un esempio sulla modalità di chiamata a una stored procedure che contiene un parametro IN, usare la stored procedure uspGetEmployeeManagers nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Questa stored procedure accetta un singolo parametro di input denominato EmployeeID, ovvero un valore integer, e restituisce un elenco ricorsivo di dipendenti e responsabili in base al valore EmployeeID specificato. Il codice Java per la chiamata a questa stored procedure è il seguente:

```java
public static void executeSprocInParams(Connection con) throws SQLException {  
    try(PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}"); ) {  

        pstmt.setInt(1, 50);  
        ResultSet rs = pstmt.executeQuery();  

        while (rs.next()) {  
            System.out.println("EMPLOYEE:");  
            System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER:");  
            System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
        }  
    }
}
```

## <a name="see-also"></a>Vedere anche

[USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)
