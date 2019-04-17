---
title: Ostrzeżenie LNK4217 narzędzi konsolidatora
ms.date: 04/15/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: f1ea3cd0a8770571ae5c55d29a901c134311550f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674243"
---
# <a name="linker-tools-warning-lnk4217"></a>Ostrzeżenie LNK4217 narzędzi konsolidatora

> symbol "*symbol*"zdefiniowane w"*filename_1.obj*"zaimportowanych przez"*filename_2.obj*"w funkcji"*funkcja*"

[__declspec(DllImport)](../../cpp/dllexport-dllimport.md) został określony dla symbolu, nawet jeśli symbol jest zdefiniowana w pliku obiektu tego samego obrazu. Usuń `__declspec(dllimport)` modyfikator, aby rozwiązać tego ostrzeżenia.

## <a name="remarks"></a>Uwagi

*symbol* jest nazwa symbolu, który jest zdefiniowany w obrazie. *Funkcja* jest funkcją, która importuje symbolu.

To ostrzeżenie nie jest wyświetlany podczas kompilowania przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opcji.

LNK4217 może również wystąpić, Jeśli spróbujesz połączyć dwa moduły ze sobą, jeśli zamiast tego należy skompilować moduł drugi z biblioteką importu modułu pierwszy.

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Następnie wyszukaj maszynę

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Próba połączenia się te dwa moduły spowoduje LNK4217. Skompiluj przykład drugi z biblioteką importu pierwszego przykładu, aby rozwiązać.

## <a name="see-also"></a>Zobacz także

[Linker Tools Warning LNK4049](linker-tools-warning-lnk4049.md) \
[Linker Tools Warning LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)