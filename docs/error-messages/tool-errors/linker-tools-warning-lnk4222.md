---
title: Ostrzeżenie LNK4222 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160409"
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