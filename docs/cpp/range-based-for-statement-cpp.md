---
title: Range-based for — instrukcja (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 504f177cf68b978642f15ba4799cab8cb517f447
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188353"
---
# <a name="range-based-for-statement-c"></a>Range-based for — instrukcja (C++)

Wykonuje `statement` wielokrotnie i sekwencyjnie dla każdego elementu w `expression`.

## <a name="syntax"></a>Składnia

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Uwagi

Użyj instrukcji **for** opartej na zakresie, aby utworzyć pętle, które muszą być wykonywane przez "zakres", który jest zdefiniowany jako wszystkie elementy, które można wykonać za pośrednictwem, na przykład C++ `std::vector`, lub dowolnej innej standardowej sekwencji biblioteki, której zakres jest definiowany przez `begin()` i `end()`. Nazwa zadeklarowana w części `for-range-declaration` jest lokalną instrukcją **for** i nie może zostać ponownie zadeklarowana w `expression` lub `statement`. Należy [zauważyć, że słowo kluczowe](../cpp/auto-cpp.md) "Select" jest preferowane w części `for-range-declaration` instrukcji.

**Nowość w programie Visual Studio 2017:**  Pętle oparte na zakresie dla pętli nie wymagają już, aby obiekty Begin () i End () były zwracane przez ten sam typ. Umożliwia to end () zwrócenie obiektu wskaźnikowego, takiego jak używany przez zakresy, zgodnie z definicją w propozycji zakres-v3. Aby uzyskać więcej informacji, zobacz [uogólnianie pętli for opartej na zakresie](https://wg21.link/p0184r0) i [biblioteki z zakresem V3 w serwisie GitHub](https://github.com/ericniebler/range-v3).

Ten kod pokazuje, w jaki sposób **używać pętli opartych na zakresie** do iterowania przez tablicę i wektor:

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

Oto dane wyjściowe:

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

Pętla **for** jest przerywana, gdy jest wykonywane jedno z następujących w `statement`: [Break](../cpp/break-statement-cpp.md), [Return](../cpp/return-statement-cpp.md)lub [goto](../cpp/goto-statement-cpp.md) do instrukcji oznaczonej poza zakresem pętli **for** . Instrukcja [Continue](../cpp/continue-statement-cpp.md) w pętli **for** opartej na zakresie kończy się tylko bieżącą iteracją.

Weź pod uwagę te fakty dotyczące zakresu **dla**:

- Automatycznie rozpoznaje tablice.

- Rozpoznaje kontenery, które mają `.begin()` i `.end()`.

- Używa `begin()` wyszukiwania zależnego od argumentów i `end()` dla innych elementów.

## <a name="see-also"></a>Zobacz też

[auto](../cpp/auto-cpp.md)<br/>
[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while, instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for, instrukcja (C++)](../cpp/for-statement-cpp.md)
