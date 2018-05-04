---
title: Range-based for — instrukcja (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc60c1efc307f30c06accdd7404cb35c135dae5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="range-based-for-statement-c"></a>Range-based for — instrukcja (C++)
Wykonuje `statement` wielokrotnie i sekwencyjnie dla każdego elementu w `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj opartej na zakresie `for` instrukcji do skonstruowania pętli, które muszą być wykonywane za pomocą "wielu", który jest zdefiniowany jako wszystko, co można wykonać iterację — na przykład `std::vector`, lub inne sekwencji standardowa biblioteka C++, których zakresem jest definiowana za pomocą `begin()` i `end()`. Nazwa, która jest zadeklarowana w `for-range-declaration` części jest lokalny dla `for` instrukcji i nie może być ponownie zadeklarowany w `expression` lub `statement`. Należy pamiętać, że [automatycznie](../cpp/auto-cpp.md) — słowo kluczowe jest preferowane w `for-range-declaration` część instrukcji. 

 **Nowa w programie Visual Studio 2017:** opartej na zakresie dla pętli nie wymagają już czy begin() i end() zwracać obiekty tego samego typu. Dzięki temu end() zwrócić obiekt wartownik, takie jak używany przez zakresy zgodnie z definicją w propozycji V3 zakresów. Aby uzyskać więcej informacji, zobacz [uogólnianie opartej na zakresie pętli For](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) i [biblioteki zakresu v3 w serwisie GitHub](https://github.com/ericniebler/range-v3).
  
 Ten kod przedstawia sposób użycia opartej na zakresie `for` pętli do iteracji tablicy i wektora:  
  
```cpp  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by const reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 Poniżej przedstawiono dane wyjściowe:  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
  
 Opartej na zakresie `for` kończy pętlę, gdy jeden z tych `statement` jest wykonywana: [podziału](../cpp/break-statement-cpp.md), [zwracać](../cpp/return-statement-cpp.md), lub [goto](../cpp/goto-statement-cpp.md) etykietą instrukcji poza oparta na zakresie **dla** pętli. A [kontynuować](../cpp/continue-statement-cpp.md) instrukcji w opartej na zakresie `for` pętli kończy bieżącą iterację.  
  
 Należy pamiętać, te faktów o opartej na zakresie `for`:  
  
-   Automatycznie rozpoznaje tablic.  
  
-   Rozpoznaje kontenery zawierające `.begin()` i `.end()`.  
  
-   Używa wyszukiwania zależnego od argumentów `begin()` i `end()` dla żadnych innych czynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatycznie](../cpp/auto-cpp.md)   
 [Iteracja — instrukcje](../cpp/iteration-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [while — instrukcja (C++)](../cpp/while-statement-cpp.md)   
 [czy-while — instrukcja (C++)](../cpp/do-while-statement-cpp.md)   
 [for, instrukcja (C++)](../cpp/for-statement-cpp.md)