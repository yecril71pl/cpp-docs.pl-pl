---
title: Ostrzeżenie kompilatora (poziom 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 17a33f7c55fa2825eae1c7d8b9d8ab78e4ed5274
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225335"
---
# <a name="compiler-warning-level-1-c4807"></a>Ostrzeżenie kompilatora (poziom 1) C4807

"Operation": niebezpieczne połączenie typu "Type" i podpisane pole bitowe typu "Type"

To ostrzeżenie jest generowane podczas porównywania jednego-bitowego pola bitowego ze znakiem ze **`bool`** zmienną. Ponieważ jedno-bitowe, podpisane pole bitowe może zawierać tylko wartości-1 lub 0, jest niebezpieczne do porównania **`bool`** . Nie są generowane żadne ostrzeżenia o miksowaniu **`bool`** i jednobitowej pola bitów bez znaku, ponieważ są one identyczne z **`bool`** i mogą zawierać tylko 0 lub 1.

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
