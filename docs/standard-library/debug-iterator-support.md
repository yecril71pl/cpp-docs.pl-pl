---
title: Obsługa iteratora debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 237ce1e956cd05f21a34d0b2b159ba104167ca37
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959595"
---
# <a name="debug-iterator-support"></a>Obsługa iteratora debugowania

Biblioteka środowiska uruchomieniowego Visual C++ wykrywa użycie iteratora niepoprawne potwierdza i wyświetla okno dialogowe w czasie wykonywania. Aby włączyć Obsługa iteratora debugowania, należy użyć wersje do debugowania biblioteki standardowej języka C++ i biblioteki wykonawczej języka C skompilować program. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md). Aby uzyskać informacje o sposobie używania Iteratory sprawdzane, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

C++ standard w tym artykule opisano sposób elementów członkowskich może spowodować Iteratory do kontenera, które staną się nieprawidłowe. Dwa przykłady to:

- Wymazywanie elementu z kontenera powoduje, że Iteratory do elementu staną się nieprawidłowe.

- Zwiększenie rozmiaru [wektor](../standard-library/vector.md) za pomocą wypychania lub Wstaw iteratorów powoduje, że do `vector` staną się nieprawidłowe.

## <a name="example"></a>Przykład

W przypadku kompilacji ten przykładowy program w trybie debugowania w czasie wykonywania go potwierdza i kończy się.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="example"></a>Przykład

Można użyć makra preprocesora [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) wyłączenia debugowania funkcji do kompilacji debugowanej iteratora. Ten program nie, ale nadal wyzwala niezdefiniowane zachowanie.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

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

## <a name="example"></a>Przykład

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

## <a name="example"></a>Przykład

Poniższy przykładowy kod powoduje potwierdzenie, ponieważ dwóch iteratorów [for_each](../standard-library/algorithm-functions.md#for_each) algorytm są niezgodne. Algorytmy Sprawdź, czy Iteratory, które są dostarczane do nich odwoływać się do tego samego kontenera.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1;
    vector<int> v2;

    v1.push_back(10);
    v1.push_back(20);

    v2.push_back(10);
    v2.push_back(20);

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

Zwróć uwagę, że w tym przykładzie użyto wyrażenia lambda `[] (int& elem) { elem *= 2; }` zamiast funktorem. Mimo że ten wybór nie ma wpływu na niepowodzenie asercji — podobne funktor mogłoby spowodować wystąpienie takiego samego błędu — wyrażenia lambda są bardzo przydatne w sposób wykonywania zadań obiektu compact funkcji. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="example"></a>Przykład

Debugowania iteratora sprawdza również powodować zmienna iteratora, który jest zadeklarowany w **dla** pętli się poza zakres, kiedy **dla** zakończeniu zakresu pętli.

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v ;

   v.push_back(10);
   v.push_back(15);
   v.push_back(20);

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="example"></a>Przykład

Debugowanie Iteratory mają nietrywialnymi destruktory. Jeśli destruktor nie jest uruchamiany z jakiegokolwiek powodu, może wystąpić naruszenia zasad dostępu i uszkodzeniem danych. Rozważmy następujący przykład:

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

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
