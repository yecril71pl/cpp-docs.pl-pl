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
ms.openlocfilehash: 09a509f650dee76ea1cb10fea8e4019f6d7f5e2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428422"
---
# <a name="debug-iterator-support"></a>Obsługa iteratora debugowania

Biblioteka środowiska uruchomieniowego Visual C++ wykrywa użycie iteratora niepoprawne potwierdza i wyświetla okno dialogowe w czasie wykonywania. Aby włączyć Obsługa iteratora debugowania, należy użyć wersje do debugowania biblioteki standardowej języka C++ i biblioteki wykonawczej języka C skompilować program. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md). Aby uzyskać informacje o sposobie używania Iteratory sprawdzane, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

C++ standard w tym artykule opisano sposób elementów członkowskich może spowodować Iteratory do kontenera, które staną się nieprawidłowe. Dwa przykłady to:

- Wymazywanie elementu z kontenera powoduje, że Iteratory do elementu staną się nieprawidłowe.

- Zwiększenie rozmiaru [wektor](../standard-library/vector.md) za pomocą wypychania lub Wstaw iteratorów powoduje, że do `vector` staną się nieprawidłowe.

## <a name="invalid-iterators"></a>Nieprawidłowy Iteratory

W przypadku kompilacji ten przykładowy program w trybie debugowania w czasie wykonywania go potwierdza i kończy się.

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

## <a name="using-iteratordebuglevel"></a>Za pomocą _ITERATOR_DEBUG_LEVEL

Można użyć makra preprocesora [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) wyłączenia debugowania funkcji do kompilacji debugowanej iteratora. Ten program nie, ale nadal wyzwala niezdefiniowane zachowanie.

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

## <a name="unitialized-iterators"></a>Iteratory niezainicjowanej

Asercja również występuje, Jeśli spróbujesz użyć iteratora, zanim zostanie zainicjowany, jak pokazano poniżej:

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

Poniższy przykładowy kod powoduje potwierdzenie, ponieważ dwóch iteratorów [for_each](../standard-library/algorithm-functions.md#for_each) algorytm są niezgodne. Algorytmy Sprawdź, czy Iteratory, które są dostarczane do nich odwoływać się do tego samego kontenera.

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

Zwróć uwagę, że w tym przykładzie użyto wyrażenia lambda `[] (int& elem) { elem *= 2; }` zamiast funktorem. Mimo że ten wybór nie ma wpływu na niepowodzenie asercji — podobne funktor mogłoby spowodować wystąpienie takiego samego błędu — wyrażenia lambda są bardzo przydatne w sposób wykonywania zadań obiektu compact funkcji. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iteratory przerywaj poza zakresem

Debugowania iteratora sprawdza również powodować zmienna iteratora, który jest zadeklarowany w **dla** pętli się poza zakres, kiedy **dla** zakończeniu zakresu pętli.

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

Debugowanie Iteratory mają nietrywialnymi destruktory. Jeśli destruktor nie działa, ale obiektu pamięć jest zwalniana, mogą wystąpić dostępu naruszenia i uszkodzenia danych. Rozważmy następujący przykład:

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
  auto vect = std::vector<int>(10);
  auto sink = new auto(std::begin(vect));
  ::operator delete(sink); // frees the memory without calling ~iterator()
} // access violation
```

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
