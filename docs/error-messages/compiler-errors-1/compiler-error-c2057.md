---
title: Błąd kompilatora C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: 6c8b171a878a8f370a024fa7374be6925695bd4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548710"
---
# <a name="compiler-error-c2057"></a>Błąd kompilatora C2057

Oczekiwano stałego wyrażenia

Kontekst wymaga wyrażeniem stałym wyrażeniem, którego wartość jest znany w czasie kompilacji.

Kompilator musi znać rozmiar typu w czasie kompilacji, aby można było przydzielić miejsca w przypadku wystąpienia tego typu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2057 i pokazuje, jak go naprawić:

```
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

## <a name="example"></a>Przykład

C ma bardziej restrykcyjne zasady wyrażeń stałych.  Poniższy przykład generuje C2057 i pokazuje, jak go naprawić:

```
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```