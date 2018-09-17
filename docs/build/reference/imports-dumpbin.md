---
title: -IMPORTS (DUMPBIN) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /imports
dev_langs:
- C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5b3b1e3a74fea278bc142d02f793308b6b0e054
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713573"
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