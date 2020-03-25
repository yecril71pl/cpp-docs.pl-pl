---
title: Ostrzeżenie kompilatora (poziom 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 2424d076be0914a68c3227566cb851b7ab64cc0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175041"
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
