---
title: Ostrzeżenie kompilatora (poziom 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: c18dbac0681067d9bc52455dfdbe44a24c786ee7
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051540"
---
# <a name="compiler-warning-level-1-c4807"></a>Ostrzeżenie kompilatora (poziom 1) C4807

"Operation": niebezpieczne połączenie typu "Type" i podpisane pole bitowe typu "Type"

To ostrzeżenie jest generowane podczas porównywania jednego bitowego pola bitowego ze znakiem do zmiennej `bool`. Ze względu na to, że jedno-bitowe, podpisane pole bitowe może zawierać tylko wartości-1 lub 0, jest to nieszkodliwe do porównania z `bool`. Nie są generowane żadne ostrzeżenia dotyczące mieszania `bool` i jeden-bitowego pola bitów bez znaku, ponieważ są one identyczne z `bool` i mogą zawierać tylko 0 lub 1.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4807:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```