---
title: Ostrzeżenie kompilatora (poziom 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: a298eb0c55f96289a0043f3a996b09798745c92d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684225"
---
# <a name="compiler-warning-level-1-c4835"></a>Ostrzeżenie kompilatora (poziom 1) C4835

"zmienna": inicjator dla eksportowanych danych nie zostanie uruchomiony, dopóki kod zarządzany nie zostanie uruchomiony po raz pierwszy w zestawie hosta

W przypadku uzyskiwania dostępu do danych między składnikami zarządzanymi zaleca się, aby nie używać natywnych mechanizmów importu i eksportu języka C++. Zamiast tego należy zadeklarować składowe danych w typie zarządzanym i odwołać się do metadanych przy użyciu `#using` klienta. Aby uzyskać więcej informacji, zobacz [#using dyrektywie](../../preprocessor/hash-using-directive-cpp.md).

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C4835.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

Poniższy przykład zużywa składnik skompilowany w poprzednim przykładzie, pokazując, że wartości zmiennych nie są zgodne z oczekiwaniami.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```
