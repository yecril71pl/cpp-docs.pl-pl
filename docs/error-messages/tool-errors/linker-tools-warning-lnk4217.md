---
title: Ostrzeżenie LNK4217 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4217
dev_langs:
- C++
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c650eddd8078419f63df48cc91705d2e86eb5c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067985"
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