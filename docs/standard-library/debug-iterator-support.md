---
title: "Obsługa iteratora debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ef6eead006b6e069a9b672d78700ff85aa2f8ef
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="debug-iterator-support"></a>Obsługa iteratora debugowania
Biblioteki wykonawczej programu Visual C++ wykrywa Użyj iteratora niepoprawny i potwierdzeń i wyświetla okno dialogowe w czasie wykonywania. Aby włączona obsługa iteratora debugowania, należy użyć debugowania wersji standardowa biblioteka C++ i Biblioteka środowiska wykonawczego języka C do skompilowania programu. Aby uzyskać więcej informacji, zobacz [Biblioteka CRT — funkcje](../c-runtime-library/crt-library-features.md). Aby uzyskać informacje o sposobie używania zaznaczone Iteratory, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).  
  
 C++ standard opisano, jak funkcji elementów członkowskich może spowodować Iteratory kontener staną się nieprawidłowe. Przedstawiono dwa przykłady:  
  
-   Wymazywanie elementu z kontenera powoduje, że Iteratory do elementu staną się nieprawidłowe.  
  
-   Zwiększenie rozmiaru [wektor](../standard-library/vector.md) za pomocą wypychania lub Wstaw Iteratory przyczyny do `vector` staną się nieprawidłowe.  
  
## <a name="example"></a>Przykład  
Jeśli kompilacja ten przykładowy program w trybie debugowania w czasie wykonywania go potwierdzeń i kończy.  
  
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
Można użyć makra preprocesora [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) o wyłączenie debugowania funkcji kompilacji debugowania iteratora. Ten program nie, ale nadal wyzwala niezdefiniowane zachowanie.  
  
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
Assert występuje również w przypadku, Jeśli spróbujesz użyć iteratora przed zainicjowaniem, jak pokazano poniżej:  
  
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
Poniższy przykład kodu powoduje potwierdzenia, ponieważ dwie Iteratory do [for_each](../standard-library/algorithm-functions.md#for_each) algorytm są niezgodne. Algorytmy Sprawdź, czy Iteratory, które są dostarczane do nich odwoływać się tego samego kontenera.  
  
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
  
Powiadomienie, że w tym przykładzie użyto wyrażenia lambda `[] (int& elem) { elem *= 2; }` zamiast obiekt. Mimo że ten wybór nie ma żadnego wpływu na niepowodzenie assert — podobne obiekt mogłyby spowodować niepowodzenie tej samej — wyrażenia lambda są bardzo przydatne sposobem wykonania określonych zadań obiektu compact funkcji. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example"></a>Przykład  
Kontrole iteratora debugowania powodować zmiennej iteracyjnej, która jest zadeklarowana w `for` pętli się poza zakres podczas `for` kończy się w zakresie pętli.  
  
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
Debugowanie Iteratory mają destruktory nieuproszczony. W przypadku destruktor nie jest uruchamiane, niezależnie od przyczyny, mogą wystąpić naruszenia zasad dostępu i uszkodzenie danych. Rozważmy następujący przykład:  
  
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
  
## <a name="see-also"></a>Zobacz też  
[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)




