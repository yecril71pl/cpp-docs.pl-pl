---
title: Błąd kompilatora C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 01f8a1bd74ed2b7a3150afae5b46128c6f5b0ca2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381153"
---
# <a name="compiler-error-c3487"></a>Błąd kompilatora C3487

"typ zwracany": wszystkie zwracać wyrażenia muszą być ustalane do tego samego typu: wcześniej było to "typ zwracany"

Wyrażenie lambda, należy określić jego typem zwracanym, chyba że zawiera pojedynczą instrukcję return. Jeśli wyrażenie lambda zawiera wiele instrukcji return, muszą mieć tego samego typu.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Określ końcowym typem zwracanym dla wyrażenia lambda. Sprawdź, czy wszystkie zwraca z wyrażenia lambda są tego samego typu, lub może być niejawnie konwertowane na typ zwracany.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3487, ponieważ typy zwracane, wyrażenia lambda nie są zgodne:

```
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)