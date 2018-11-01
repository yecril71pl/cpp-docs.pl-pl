---
title: Częściowe porządkowanie szablonów funkcji (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 10b920e4d5f999c3a2c9649ceabb0369813cc401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438860"
---
# <a name="partial-ordering-of-function-templates-c"></a>Częściowe porządkowanie szablonów funkcji (C++)

Dostępnych może być wiele szablonów funkcji, które odpowiadają liście argumentów wywołania funkcji. C++ definiuje częściowe ustalanie kolejności szablonów funkcji w celu określenia, którą funkcję należy wywołać. Ustalanie kolejności jest częściowe, ponieważ może istnieć wiele szablonów, które są uważane za jednakowo specjalistyczne.

Kompilator wybiera najbardziej wyspecjalizowaną funkcję szablonu dostępną z możliwych dopasowań. Na przykład, jeśli szablon funkcji przyjmuje typ __T__, a inny szablon funkcji __T\*__  jest dostępny, __T\*__  wersji jest nazywany więcej wyspecjalizowane i jest preferowany w porównaniu do ogólnego __T__ zawsze wtedy, gdy argument jest typem wskaźnika, nawet jeśli oba są dopuszczalnymi dopasowaniami.

Użyj następującego procesu w celu określenia, czy jeden z kandydatów szablonów funkcji jest bardziej wyspecjalizowany:

1. Rozważ dwa szablony funkcji T1 i T2.

1. Zastąp parametry w T1 hipotetycznym unikatowym typem X.

1. Mając listę parametrów dla T1, zobacz czy T2 jest prawidłowym szablonem dla tej listy parametrów. Zignoruj wszystkie niejawne konwersje.

1. Powtórz ten sam proces z odwróconymi T1 i T2.

1. Jeśli jeden szablon jest prawidłową listą argumentów szablonu dla innego szablonu, ale odwrotnie nie jest to prawdą, wówczas szablon jest uważany za mniej wyspecjalizowany od drugiego szablonu. Jeśli oba szablony używając poprzedniego kroku formularza prawidłowe argumenty dla siebie nawzajem, następnie są wówczas uważane za jednakowo można wyspecjalizować, a wyniki się niejednoznacznego wywołania podczas próby ich używać.

1. Przy użyciu tych reguł:

   1. Specjalizacja szablonu dla określonego typu jest bardziej wyspecjalizowana niż ta, która przyjmuje argument typu ogólnego.

   1. Szablon tylko __T\*__  jest bardziej wyspecjalizowana niż tylko jeden biorąc __T__, ponieważ możesz wpisać __X\*__  jest prawidłowym argumentem dla __T__ argument szablonu, ale __X__ nie jest prawidłowym argumentem dla __T\*__  argument szablonu.

   1. __Const T__ jest bardziej wyspecjalizowana niż __T__, ponieważ __const X__ jest prawidłowym argumentem dla __T__ argument szablonu, ale __X__ jest Nieprawidłowy argument dla __const T__ argument szablonu.

   1. __Const T\*__  jest bardziej wyspecjalizowana niż __T\*__, ponieważ __const X\*__  jest prawidłowym argumentem dla __T\*__  argument szablonu, ale __X\*__  nie jest prawidłowym argumentem dla __const T\*__  argument szablonu.

## <a name="example"></a>Przykład

Poniższy przykład działa jak określono w normie:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

extern "C" int printf(const char*,...);
template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>Zobacz także

[Szablony funkcji](../cpp/function-templates.md)
