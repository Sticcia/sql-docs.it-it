---
title: 'Configurazione TLS 1.2 nel sistema di piattaforma Analitica | Microsoft Docs '
description: Raccomandazione per configurare TLS 1.2 in APS
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6ea2144fe333f87123abdf92e16aa7122e98b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239460"
---
# <a name="configure-tls-12-in-aps"></a>Configurare TLS 1.2 in APS

Per proteggere i punti di accesso per usare solo TLS 1.2, si dovrà disabilitare in modo esplicito altri protocolli su tutti gli host fisici e virtuali. Disabilitare i protocolli richiedono modifiche alle impostazioni del Registro di sistema. Le modifiche del Registro di sistema richiedono un riavvio degli host fisici e virtuali.

> [!WARNING]
> In questa sezione, nei passaggi del metodo o dell'attività viene illustrata la modalità di modifica del Registro di sistema. Tuttavia, può causare gravi problemi se si modifica il Registro di sistema in modo non corretto che può causare la perdita di dati e richiedere la reinstallazione del sistema operativo. È consigliabile eseguire il backup del Registro di sistema prima di modificarlo. Successivamente, sarà possibile ripristinarlo in caso di problemi. Per altre informazioni su come eseguire il backup e ripristino del Registro di sistema, fare clic sul seguente numero di articolo per visualizzare l'articolo della Microsoft Knowledge Base:<br>
[322756](https://support.microsoft.com/help/322756) come eseguire il backup e ripristinare il Registro di sistema in Windows

**Disabilitare:**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Anche impostare le chiavi seguenti nel client computer in cui sono installati gli strumenti, ad esempio SSIS APS gli adattatori di destinazione.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



