---
title: Impostazione dei dati delle proprietà dell'origine | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef3719e41680f396c7dcd6bc41d667fe82fe7f6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639019"
---
# <a name="setting-the-data-source-properties"></a>Impostazione delle proprietà delle origini dei dati

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le origini dati sono il meccanismo ideale con cui creare connessioni JDBC in un ambiente Java EE (Java Platform, Enterprise Edition). Le origini dati forniscono connessioni, connessioni in pool e connessioni distribuite senza la necessità di specificare le proprietà di connessione a livello di codice Java. Tutte le origini dati di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] consentono di impostare o ottenere il valore di qualsiasi proprietà usando rispettivamente i metodi setter e getter appropriati.

I prodotti Java EE, quali server applicazioni e motori servlet/JSP, consentono in genere di configurare origini dati per l'accesso ai database. Tutte le proprietà elencate nell'argomento [Impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md) possono essere specificate ovunque la configurazione consenta di immettere una proprietà come coppia proprietà=valore.

Per altre informazioni sulle origini dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Per un esempio di come usare le classi di SQLServerDataSource per stabilire una connessione a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del database, vedere [origine dati di esempio](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a>Vedere anche

[Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
