---
title: Błąd kompilatora C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: bdcf97ab6ea877af4e0713fc96ffd38f299e8234
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741452"
---
# <a name="compiler-error-c2057"></a>Błąd kompilatora C2057

oczekiwane wyrażenie stałej

Kontekst wymaga wyrażenia stałego, którego wyrażenie, którego wartość jest znana w czasie kompilacji.

Kompilator musi znać rozmiar typu w czasie kompilacji w celu przydzielenia miejsca na wystąpienie tego typu.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2057 i pokazuje, jak to naprawić:

```cpp
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

Język C ma bardziej restrykcyjne reguły dla wyrażeń stałych.  Poniższy przykład generuje C2057 i pokazuje, jak to naprawić:

```c
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```
