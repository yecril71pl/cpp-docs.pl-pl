---
title: Obsługa iteratora debugowania
ms.date: 09/13/2018
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
ms.openlocfilehash: 3ccb618c9a3c6b21d6ffe3fbbce7b6c1140e0564
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450589"
---
# <a name="debug-iterator-support"></a>Obsługa iteratora debugowania

Biblioteka wykonawcza wizualizacji C++ wykrywa nieprawidłowe użycie iteratora i potwierdza i wyświetla okno dialogowe w czasie wykonywania. Aby włączyć obsługę iteratora debugowania, należy użyć wersji debugowania biblioteki C++ standardowej i biblioteki środowiska uruchomieniowego języka C do kompilowania programu. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md). Aby uzyskać informacje o sposobach używania sprawdzonych iteratorów, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

Standard C++ opisuje sposób, w jaki funkcje elementów członkowskich mogą powodować, że Iteratory do kontenera stają się nieprawidłowe. Dwa przykłady:

- Wymazanie elementu z kontenera powoduje, że Iteratory elementu stają się nieprawidłowe.

- Zwiększenie rozmiaru wektora przy [](../standard-library/vector.md) użyciu instrukcji push lub INSERT powoduje, że `vector` Iteratory do stają się nieprawidłowe.

## <a name="invalid-iterators"></a>Nieprawidłowe Iteratory

W przypadku skompilowania tego przykładowego programu w trybie debugowania w czasie wykonywania zostanie potwierdzone i przerwane.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-iteratordebuglevel"></a>Korzystanie z _ITERATOR_DEBUG_LEVEL

Aby wyłączyć funkcję debugowania iteratora w kompilacji debugowania, można użyć [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) makro preprocesora. Ten program nie potwierdza, ale nadal wyzwala niezdefiniowane zachowanie.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

```Output
20
-572662307
```

## <a name="unitialized-iterators"></a>Iteratory Unitialized

Potwierdzenie występuje również wtedy, gdy spróbujesz użyć iteratora przed zainicjowaniem, jak pokazano poniżej:

```cpp
// iterator_debugging_2.cpp
// compile by using: /EHsc /MDd
#include <string>
using namespace std;

int main() {
   string::iterator i1, i2;
   if (i1 == i2)
      ;
}
```

## <a name="incompatible-iterators"></a>Niezgodne Iteratory

Poniższy przykład kodu powoduje potwierdzenie, ponieważ dwa Iteratory algorytmu [for_each](../standard-library/algorithm-functions.md#for_each) są niezgodne. Algorytmy sprawdzają, czy Iteratory, które są dostarczane do nich odwołują się do tego samego kontenera.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

Zwróć uwagę, że w tym przykładzie używane `[] (int& elem) { elem *= 2; }` jest wyrażenie lambda zamiast Funktor. Mimo że wybór ten nie ma wpływu na błąd potwierdzenia — podobny Funktor może spowodować wystąpienie tego samego błędu — wyrażenia lambda są bardzo przydatne w przypadku wykonywania zadań obiektów funkcji Compact. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iteratory wykraczające poza zakres

Testy iteratora debugowania również powodują, że zmienna iteratora zadeklarowana w pętli **for** jest poza zakresem, gdy zostanie zakończony zakres pętli **for** .

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>Destruktory dla iteratorów debugowania

Iteratory debugowania mają nieproste destruktory. Jeśli destruktor nie zostanie uruchomiony, ale pamięć obiektu jest zwolniona, mogą wystąpić naruszenia zasad dostępu i uszkodzenia danych. Rozważmy następujący przykład:

```cpp
// iterator_debugging_5.cpp
// compile by using: /EHsc /MDd
#include <vector>
struct base {
   // TO FIX: uncomment the next line
   // virtual ~base() {}
};

struct derived : base {
   std::vector<int>::iterator m_iter;
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}
   ~derived() {}
};

 int main() {
   std::vector<int> vect( 10 );
   base * pb = new derived( vect.begin() );
   delete pb;  // doesn't call ~derived()
   // access violation
}
```

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)
