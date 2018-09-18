---
title: Ostrzeżenie (poziom 3) kompilatora C4800 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5a19c27731192a5fe2930aec3e78fb66d790484
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090910"
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