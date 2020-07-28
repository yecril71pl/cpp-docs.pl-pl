---
title: Ostrzeżenie kompilatora (poziom 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: acc7957493942a9c0e19ce098b74ed0b5d75a12d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214363"
---
# <a name="compiler-warning-level-4-c4463"></a>Ostrzeżenie kompilatora (poziom 4) C4463

> przepływ Przypisywanie *wartości* do pola bitowego, które może zawierać tylko wartości z *low_value* do *high_value*

Przypisana *wartość* znajduje się poza zakresem wartości, które może zawierać pole bitowe. Podpisane typy pól bitowych używają bitu o wysokiej kolejności dla znaku, więc jeśli *n* to rozmiar pola bitowego, zakres podpisanych pól bitowych to-2<sup>n-1</sup> do 2<sup>n-</sup>1-1, podczas gdy pola bitowe bez znaku mają zakres od 0 do 2<sup>n</sup>-1.

## <a name="example"></a>Przykład

Ten przykład generuje C4463, ponieważ próbuje przypisać wartość 3 do pola bitowego typu **`int`** o rozmiarze 2, który ma zakres od-2 do 1.

Aby rozwiązać ten problem, można zmienić przypisaną wartość na coś w dozwolonym zakresie. Jeśli pole bitowe jest przeznaczone do przechowywania wartości bez znaku z zakresu od 0 do 3, można zmienić typ deklaracji na **`unsigned`** . Jeśli pole jest przeznaczone do przechowywania wartości z zakresu od 4 do 3, można zmienić rozmiar pola bitowego na 3.

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
