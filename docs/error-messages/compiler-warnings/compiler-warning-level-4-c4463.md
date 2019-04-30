---
title: Kompilator ostrzeżenie (poziom 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400802"
---
# <a name="compiler-warning-level-4-c4463"></a>Kompilator ostrzeżenie (poziom 4) C4463

> przepełnienie; Przypisywanie *wartość* do pola bitowego, która może zawierać wartości z *low_value* do *high_value*

Przypisane *wartość* znajduje się poza zakresem wartości, które mogą zawierać pola bitowego. Typy ze znakiem pola bitowego Użyj znaczących bitów podczas logowania, więc jeśli *n* jest rozmiar pola bitowego, zakres, dla podpisanych pól bitowych to -2<sup>n-1</sup> 2<sup>n-1</sup>-1, podczas gdy bez znaku pola bitowe ma zakres od 0 do 2<sup>n</sup>-1.

## <a name="example"></a>Przykład

Ten przykład generuje C4463, ponieważ próbuje przypisać wartość 3 do pola bitowego typu `int` o rozmiarze 2, która ma zakres od -2 do 1.

Aby rozwiązać ten problem, można zmienić przypisaną wartością coś o nim w dozwolonym zakresem. Jeśli pole bitowe jest przeznaczony do przechowywania wartości bez znaku z zakresu od 0 do 3, można zmienić typu zgłoszenia do `unsigned`. Jeśli pole jest przeznaczony do przechowywania wartości w zakresie -4-3, można zmienić rozmiar pola bitowego do 3.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
