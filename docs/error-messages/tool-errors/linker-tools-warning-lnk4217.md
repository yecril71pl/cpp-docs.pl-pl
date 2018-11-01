---
title: Ostrzeżenie LNK4217 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 12766241832d39f0b47ed85036c0ebeb0447fc75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448051"
---
# <a name="linker-tools-warning-lnk4217"></a>Ostrzeżenie LNK4217 narzędzi konsolidatora

lokalnie zdefiniowany symbol "symbol" zaimportowany w funkcji "function"

[__declspec(DllImport)](../../cpp/dllexport-dllimport.md) został określony dla symbolu, nawet, jeśli symbol jest zdefiniowane lokalnie. Usuń `__declspec` modyfikator, aby rozwiązać tego ostrzeżenia.

`symbol` to nazwa symbolu, który jest zdefiniowany w obrazie. `function` jest funkcją, która importuje symbolu.

To ostrzeżenie nie będą widoczne, gdy kompilujesz przy użyciu opcji [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

LNK4217 może również wystąpić, Jeśli spróbujesz połączyć dwa moduły ze sobą, jeśli zamiast tego należy skompilować moduł drugi z biblioteką importu modułu pierwszy.

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Następnie wyszukaj maszynę

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Próba połączenia się te dwa moduły spowodować LNK4217, skompilować przykład drugi z biblioteką importu pierwszego przykładu, aby rozwiązać.