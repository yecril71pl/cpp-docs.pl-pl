---
title: Błąd kompilatora C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 7b38755470e3746066711382b2ed471badc8e197
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738443"
---
# <a name="compiler-error-c3487"></a>Błąd kompilatora C3487

"typ zwracany": wszystkie wyrażenia Return muszą być ustalane dla tego samego typu: poprzednio był to "typ zwracany"

Wartość lambda musi określać jej typ zwracany, chyba że zawiera pojedynczą instrukcję return. Jeśli wyrażenie lambda zawiera wiele instrukcji return, muszą one mieć ten sam typ.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Określ końcowy typ zwracany dla wyrażenia lambda. Upewnij się, że wszystkie zwroty z wyrażenia lambda są tego samego typu lub mogą być niejawnie konwertowane na typ zwracany.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3487, ponieważ zwracane typy lambda nie są zgodne:

```cpp
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
