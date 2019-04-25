---
title: 'Operator bezpośredni: *'
ms.date: 11/04/2016
helpviewer_keywords:
- '* operator'
- indirection operator
- operators [C++], indirection
- indirection operator [C++], syntax
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
ms.openlocfilehash: a35d8cb28baaee37ad64a61cbcb9d4c76a5aad06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183586"
---
# <a name="indirection-operator-"></a>Operator bezpośredni: *

## <a name="syntax"></a>Składnia

```
* cast-expression
```

## <a name="remarks"></a>Uwagi

Jednoargumentowy operator pośredni (<strong>\*</strong>) wyłuskania wskaźnika; oznacza to, konwertuje wartość wskaźnika do l wartością. Argument operacji operatora pośredniego musi być wskaźnikiem do typu. Wynik wyrażenia pośredni to typ, z którego jest tworzony na typ wskaźnika. Korzystanie z <strong>\*</strong> operatora w tym kontekście różni się od jego znaczenie jako operator binarny, który jest mnożenia.

Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Jeśli wskazuje on lokalizację magazynu, wynikiem jest l-wartość opisująca lokalizację magazynu.

Operator pośredni mogą łącznie używane w celu wyłuskania wskaźniki do wskaźników. Na przykład:

```cpp
// expre_Indirection_Operator.cpp
// compile with: /EHsc
// Demonstrate indirection operator
#include <iostream>
using namespace std;
int main() {
   int n = 5;
   int *pn = &n;
   int **ppn = &pn;

   cout  << "Value of n:\n"
         << "direct value: " << n << endl
         << "indirect value: " << *pn << endl
         << "doubly indirect value: " << **ppn << endl
         << "address of n: " << pn << endl
         << "address of n via indirection: " << *ppn << endl;
}
```

Jeśli wartość wskaźnika jest nieprawidłowa, wynik jest niezdefiniowany. Następująca lista zawiera niektóre z najbardziej typowych warunków, które unieważniają wartość wskaźnika.

- Wskaźnik jest pustym wskaźnikiem.

- Wskaźnik określa adres lokalnego elementu, który nie jest widoczny w momencie odwołania.

- Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.

- Wskaźnik określa adres nieużywany przez program wykonujący.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operator Address-of: &](../cpp/address-of-operator-amp.md)<br/>
[Operatory pośrednie i „Address-of”](../c-language/indirection-and-address-of-operators.md)