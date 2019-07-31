---
title: Częściowe porządkowanie szablonów funkcji (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682425"
---
# <a name="partial-ordering-of-function-templates-c"></a>Częściowe porządkowanie szablonów funkcji (C++)

Dostępnych może być wiele szablonów funkcji, które odpowiadają liście argumentów wywołania funkcji. C++ definiuje częściowe ustalanie kolejności szablonów funkcji w celu określenia, którą funkcję należy wywołać. Ustalanie kolejności jest częściowe, ponieważ może istnieć wiele szablonów, które są uważane za jednakowo specjalistyczne.

Kompilator wybiera najbardziej wyspecjalizowaną funkcję szablonu dostępną z możliwych dopasowań. Na przykład jeśli szablon funkcji przyjmuje typ `T` i jest dostępny inny szablon funkcji, który jest wymagany `T*` , `T*` wersja jest określana jako bardziej wyspecjalizowana. Jest preferowana w porównaniu z `T` wersją ogólną, gdy argument jest typem wskaźnika, mimo że oba byłyby dozwolone.

Użyj następującego procesu w celu określenia, czy jeden z kandydatów szablonów funkcji jest bardziej wyspecjalizowany:

1. Rozważ dwa szablony funkcji T1 i T2.

1. Zastąp parametry w T1 hipotetycznym unikatowym typem X.

1. Mając listę parametrów dla T1, zobacz czy T2 jest prawidłowym szablonem dla tej listy parametrów. Zignoruj wszystkie niejawne konwersje.

1. Powtórz ten sam proces z odwróconymi T1 i T2.

1. Jeśli jeden szablon jest prawidłową listą argumentów szablonu dla innego szablonu, ale nie jest spełniony, ten szablon jest traktowany jako mniej wyspecjalizowany niż inny szablon. Jeśli przy użyciu poprzedniego kroku oba szablony tworzą prawidłowe argumenty dla siebie, są uważane za równie wyspecjalizowane i niejednoznaczne wyniki wywołań podczas próby ich użycia.

1. Przy użyciu tych reguł:

   1. Specjalizacja szablonu dla określonego typu jest bardziej wyspecjalizowana niż ta, która przyjmuje argument typu ogólnego.

   1. Szablon przyjmujący tylko `T*` , że jest bardziej wyspecjalizowany, `T`tylko wtedy, gdy typ `X*` hipotetyczny jest prawidłowym argumentem `T` dla argumentu szablonu, `X` ale nie jest prawidłowym argumentem dla `T*`argument szablonu.

   1. `const T`jest bardziej wyspecjalizowany `T`niż, `const X` ponieważ jest prawidłowym argumentem `T` dla argumentu szablonu, `X` `const T` ale nie jest prawidłowym argumentem argumentu szablonu.

   1. `const T*`jest bardziej wyspecjalizowany `T*`niż, `const X*` ponieważ jest prawidłowym argumentem `T*` dla argumentu szablonu, `X*` `const T*` ale nie jest prawidłowym argumentem argumentu szablonu.

## <a name="example"></a>Przykład

Poniższy przykład działa jak określono w standardzie:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

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
