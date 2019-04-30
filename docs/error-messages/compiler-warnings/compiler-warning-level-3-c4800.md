---
title: Ostrzeżenie (poziom 4) kompilatora C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401556"
---
# <a name="compiler-warning-level-4-c4800"></a>Ostrzeżenie (poziom 4) kompilatora C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 lub nowszy:
> Niejawna konwersja z "*typu*" na wartość logiczna. Prawdopodobieństwo utraty informacji możliwych
::: moniker-end

C4800 jest ostrzeżenie poziom 3 w programie Visual Studio 2015 i starszych wersji:
> "*typu*": Wymuszenie wartość logiczna "prawda" lub "fałsz" (ostrzeżenie dotyczące wydajności)

To ostrzeżenie jest generowane, gdy wartość jest niejawnie konwertowany na typ `bool`. Zazwyczaj ten komunikat jest spowodowany przez przypisywanie `int` zmienne `bool` zmienne gdzie `int` zmienna zawiera tylko wartości **true** i **false**i można go ponownie zadeklarowany jako typ `bool`. Jeśli nie Napisz ponownie wyrażenie typu `bool`, następnie można dodać "`!=0`" na wyrażenie, które zapewnia typ wyrażenia `bool`. Rzutowanie wyrażenia na typ `bool` nie Wyłącz ostrzeżenie, co jest zgodne z projektem.

::: moniker range=">= vs-2017"
To ostrzeżenie nie jest emitowane w programie Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
To ostrzeżenie jest wyłączone domyślnie, począwszy od programu Visual Studio 2019 r. Użyj __Wn__*n*__4800__ umożliwiające C4800 jako poziom *n* ostrzeżenie, lub [/Wall](../../build/reference/compiler-option-warning-level.md) włączyć wszystkie ostrzeżenia, są domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Przykład

Poniższy przykład generuje C4800 i pokazuje, jak go naprawić:

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```