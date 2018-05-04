---
title: Częściowe porządkowanie szablonów funkcji (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60936a46732e4b2ed827a5efb08740661d9bb0d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="partial-ordering-of-function-templates-c"></a>Częściowe porządkowanie szablonów funkcji (C++)

Dostępnych może być wiele szablonów funkcji, które odpowiadają liście argumentów wywołania funkcji. C++ definiuje częściowe ustalanie kolejności szablonów funkcji w celu określenia, którą funkcję należy wywołać. Ustalanie kolejności jest częściowe, ponieważ może istnieć wiele szablonów, które są uważane za jednakowo specjalistyczne.

Kompilator wybiera najbardziej wyspecjalizowaną funkcję szablonu dostępną z możliwych dopasowań. Na przykład, jeśli typ szablonu funkcji __T__i pobieranie innego szablonu funkcji __T\*__  jest dostępna, __T\*__  , jest określany w wersji więcej specjalizowany i jest preferowane ogólnego __T__ wersji zawsze, gdy argument jest typem wskaźnika, mimo że oba będą dozwolone dopasowań.

Użyj następującego procesu w celu określenia, czy jeden z kandydatów szablonów funkcji jest bardziej wyspecjalizowany:

1. Rozważ dwa szablony funkcji T1 i T2.

2. Zastąp parametry w T1 hipotetycznym unikatowym typem X.

3. Mając listę parametrów dla T1, zobacz czy T2 jest prawidłowym szablonem dla tej listy parametrów. Zignoruj wszystkie niejawne konwersje.

4. Powtórz ten sam proces z odwróconymi T1 i T2.

5. Jeśli jeden szablon jest prawidłową listą argumentów szablonu dla innego szablonu, ale odwrotnie nie jest to prawdą, wówczas szablon jest uważany za mniej wyspecjalizowany od drugiego szablonu. Jeśli oba szablonów przy użyciu poprzedniego kroku formularza poprawne argumenty dla siebie nawzajem, następnie są one uznawane za jednakowo być specjalizowany i powoduje niejednoznaczne wywołanie podczas próby korzystania z nich.

6. Przy użyciu tych reguł:

     1. Specjalizacja szablonu dla określonego typu jest bardziej wyspecjalizowana niż ta, która przyjmuje argument typu ogólnego.

     2. Szablon biorąc tylko __T\*__  jest bardziej skomplikowane niż tylko jeden biorąc __T__, ponieważ typ hipotetyczny __X\*__  jest prawidłowym argumentem dla __T__ argument szablonu, ale __X__ nie jest prawidłowym argumentem dla __T\*__  argument szablonu.

     3. __Const T__ jest bardziej skomplikowane niż __T__, ponieważ __const X__ jest prawidłowym argumentem dla __T__ argument szablonu, ale __X__ jest Nieprawidłowy argument dla __const T__ argument szablonu.

     4. __Const T\*__  jest bardziej skomplikowane niż __T\*__, ponieważ __const X\*__  jest prawidłowym argumentem dla __T\*__  argument szablonu, ale __X\*__  nie jest prawidłowym argumentem dla __const T\*__  argument szablonu.

## <a name="example"></a>Przykład

Poniższy przykład działa jak określono w standardzie:

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
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## <a name="see-also"></a>Zobacz też

[Szablony funkcji](../cpp/function-templates.md)
