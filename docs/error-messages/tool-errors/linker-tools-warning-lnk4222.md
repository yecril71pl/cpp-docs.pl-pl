---
title: Ostrzeżenie LNK4222 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abc4f85fbc361b37d9325f9d395a1c34e1eeed2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106940"
---
# <a name="linker-tools-warning-lnk4222"></a>Ostrzeżenie LNK4222 narzędzi konsolidatora

do wyeksportowanego symbolu "symbol" nie należy przypisywać liczby porządkowej

Według liczby porządkowej, nie powinien można wyeksportować następujących symboli:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Te funkcje zawsze znajdują się przy użyciu nazwy, za pomocą `GetProcAddress`. Konsolidator ostrzega o tym jest rodzaj eksportu, ponieważ może to spowodować większy obraz. Może się to zdarzyć, jeśli zakres Twojej porządkową eksportu jest duży wywozu stosunkowo niewielką liczbą. Na przykład

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

będzie wymagać 100 miejsca w tabeli eksportu adresu z 98 ich po prostu wypełniacza (2-99). Z drugiej strony

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

wymaga dwóch miejsc. (Należy pamiętać, że można również wyeksportować z [/EXPORT](../../build/reference/export-exports-a-function.md) — opcja konsolidatora.)