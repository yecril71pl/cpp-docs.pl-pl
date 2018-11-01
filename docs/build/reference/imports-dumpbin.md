---
title: /IMPORTS (DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: 9367457a8e7f6be1f372244f8288a994eb777071
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613789"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Ta opcja wyświetla listę bibliotek DLL (obie połączone statycznie i [ładowane z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)), są importowane do pliku wykonywalnego lub biblioteki DLL i wszystkie Importy poszczególnych z każdej z tych bibliotek DLL.

Opcjonalny `file` specyfikacji pozwala określić, że będą wyświetlane Import dla tylko tej biblioteki DLL. Na przykład:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Uwagi

Dane wyjściowe wyświetlane przez tę opcję, jest podobny do [/EKSPORTUJE](../../build/reference/dash-exports.md) danych wyjściowych.

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)