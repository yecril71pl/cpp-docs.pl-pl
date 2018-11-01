---
title: Błąd kompilatora C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585370"
---
# <a name="compiler-error-c2732"></a>Błąd kompilatora C2732

Specyfikacja powiązania jest sprzeczna wcześniejszą specyfikacją dla "function"

Funkcja jest już zadeklarowana ze specyfikatorem różne powiązania.

Ten błąd może być spowodowany przez obejmują plików przy użyciu specyfikatorów różne powiązania.

Aby naprawić ten błąd, zmień `extern` instrukcji, aby zaakceptować powiązań. W szczególności, nie jest zawijany `#include` dyrektywy w `extern "C"` bloków.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2732:

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```