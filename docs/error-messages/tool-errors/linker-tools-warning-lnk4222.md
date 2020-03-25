---
title: Ostrzeżenie LNK4222 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183036"
---
# <a name="linker-tools-warning-lnk4222"></a>Ostrzeżenie LNK4222 narzędzi konsolidatora

do wyeksportowanego symbolu "symbol" nie należy przypisywać liczby porządkowej

Następujące symbole nie powinny być eksportowane według numeru porządkowego:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Te funkcje są zawsze zlokalizowane według nazwy, przy użyciu `GetProcAddress`. Konsolidator ostrzega o tym rodzaju eksportu, ponieważ może to skutkować większym obrazem. Taka sytuacja może wystąpić, jeśli zakres eksportów porządkowych jest duży z stosunkowo niewielkim eksportem. Na przykład:

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

Program będzie wymagał 100 gniazd w tabeli adresów eksportu z 98 z nich (2-99). Z drugiej strony

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

wymagane są dwa gniazda. Należy pamiętać, że można również wyeksportować z opcją [/Export](../../build/reference/export-exports-a-function.md) konsolidatora.
