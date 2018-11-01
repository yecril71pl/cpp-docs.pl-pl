---
title: Ostrzeżenie (poziom 3) kompilatora C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636140"
---
# <a name="compiler-warning-level-3-c4800"></a>Ostrzeżenie (poziom 3) kompilatora C4800

> "*typu*": Wymuszenie wartość logiczna "prawda" lub "fałsz" (ostrzeżenie dotyczące wydajności)

To ostrzeżenie jest generowane, gdy wartość to nie `bool` jest przypisany lub przekształcić na typ `bool`. Zazwyczaj ten komunikat jest spowodowany przez przypisywanie `int` zmienne `bool` zmienne gdzie `int` zmienna zawiera tylko wartości **true** i **false**i można go ponownie zadeklarowany jako typ `bool`. Jeśli nie Napisz ponownie wyrażenie typu `bool`, następnie można dodać "`!=0`" na wyrażenie, które zapewnia typ wyrażenia `bool`. Rzutowanie wyrażenia na typ `bool` nie wyłącza ostrzeżenie, co jest zgodne z projektem.

To ostrzeżenie nie jest generowany w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4800 i pokazuje, jak go naprawić:

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```