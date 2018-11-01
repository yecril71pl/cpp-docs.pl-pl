---
title: Kompilator ostrzeżenie (poziom 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: 0427a97a9e368a19a40a8d1a552f7713e36f831e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516314"
---
# <a name="compiler-warning-level-1-c4835"></a>Kompilator ostrzeżenie (poziom 1) C4835

'Zmienna': Inicjator dla eksportowanych danych nie będzie działać, dopóki kod zarządzany jest wykonywany jako pierwszy w zestawie hosta

Podczas uzyskiwania dostępu do danych między składników zarządzanych, zaleca się nie używać natywnego języka C++ importu i eksportu mechanizmów. Zamiast tego należy zadeklarować członkom danych wewnątrz typu zarządzanego i odwoływać się do metadanych z `#using` w kliencie. Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4835.

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Przykład

Poniższy przykład używa składnika utworzone w poprzednim przykładzie, pokazujący, że wartości zmiennych nie jest zgodne z oczekiwaniami.

```
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