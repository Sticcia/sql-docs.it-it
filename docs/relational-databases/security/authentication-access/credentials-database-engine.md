---
title: Credenziali (motore di database) | Microsoft Docs
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c1e49cf402cf944e912e4297f6a315a570f27e8
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="credentials-database-engine"></a>Credenziali (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  Una credenziale è un record contenente le informazioni di autenticazione (credenziali) necessarie per connettersi a una risorsa all'esterno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Queste informazioni vengono utilizzate internamente da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La maggior parte delle credenziali contiene un nome utente e una password di Windows.  
  
 Le informazioni archiviate in una credenziale consentono a un utente che ha eseguito la connessione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di accedere a risorse esterne all'istanza del server. Quando la risorsa esterna è Windows, l'utente viene autenticato come l'utente di Windows specificato nella credenziale. È possibile eseguire il mapping di una singola credenziale a più account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , tuttavia, per un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è possibile eseguire il mapping a una sola credenziale.  
  
 Per le credenziali archiviate nel database master che possono essere usate nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md). Per le credenziali usate da un database specifico e trasferibili con il database, vedere [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  
  
 Le credenziali del sistema vengono create automaticamente e associate a endpoint specifici. I nomi delle credenziali di sistema iniziano con due segni di cancelletto (##).  
  
 Per altre informazioni sulle credenziali, vedere le viste del catalogo [sys.credentials](../../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) e [sys.database_scoped_credentials](../../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).  
  
## <a name="related-content"></a>Contenuto correlato  
 [Creare una credenziale](../../../relational-databases/security/authentication-access/create-a-credential.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [CREATE DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
 [Sicurezza di SQL Server](../../../relational-databases/security/securing-sql-server.md)  
  
  
