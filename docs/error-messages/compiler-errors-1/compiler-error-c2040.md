---
title: Błąd kompilatora C2040
ms.date: 11/04/2016
f1_keywords:
- C2040
helpviewer_keywords:
- C2040
ms.assetid: 74ca3592-1469-4965-ab34-a4815e2fbefe
ms.openlocfilehash: 8002d7168354b1213d01ca390a03b1baa5e35c88
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740419"
---
# <a name="compiler-error-c2040"></a>Błąd kompilatora C2040

"operator": "Identifier1" różni się w poziomach pośrednich od "identifier2"

Wyrażenie obejmujące określone operandy ma niezgodne typy operandów lub niejawnie przekonwertowane Typy operandów. Jeśli oba operandy są arytmetyczne lub obie są niearytmetyczne (takie jak tablica lub wskaźnik), są używane bez zmian. Jeśli jeden operand jest arytmetyczny, a drugi nie, operand arytmetyczny jest konwertowany na typ operandu niearytmetycznego.

Ten przykład generuje C2040 i pokazuje, jak rozwiązać ten problem.

```cpp
// C2040.cpp
// Compile by using: cl /c /W3 C2040.cpp
bool test() {
   char c = '3';
   return c == "3"; // C2446, C2040
   // return c == '3'; // OK
}
```
