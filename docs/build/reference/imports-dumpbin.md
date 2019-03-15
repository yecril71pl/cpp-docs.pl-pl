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
ms.openlocfilehash: c8b0f88b38eb657fe4d3916ef0df13972e985cbe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810344"
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)

```
/IMPORTS[:file]
```

Ta opcja wyświetla listę bibliotek DLL (obie połączone statycznie i [ładowane z opóźnieniem](linker-support-for-delay-loaded-dlls.md)), są importowane do pliku wykonywalnego lub biblioteki DLL i wszystkie Importy poszczególnych z każdej z tych bibliotek DLL.

Opcjonalny `file` specyfikacji pozwala określić, że będą wyświetlane Import dla tylko tej biblioteki DLL. Na przykład:

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>Uwagi

Dane wyjściowe wyświetlane przez tę opcję, jest podobny do [/EKSPORTUJE](dash-exports.md) danych wyjściowych.

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
