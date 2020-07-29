---
title: Range-based for — instrukcja (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: 1197080e2e96e0e5c51bc06e93026567a33c7842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223619"
---
# <a name="range-based-for-statement-c"></a>Range-based for — instrukcja (C++)

Wykonuje `statement` wielokrotnie i sekwencyjnie dla każdego elementu w `expression` .

## <a name="syntax"></a>Składnia

> **`for (`***Deklaracja* **`:`** dla zakresu *wyrażenie***`)`**\
&emsp;*instrukcja*

## <a name="remarks"></a>Uwagi

Użyj instrukcji opartej na zakresie **`for`** , aby utworzyć pętle, które muszą zostać wykonane przez *zakres*, który jest zdefiniowany jako wszystko, co można wykonać w iteracji, na przykład `std::vector` , lub dowolną inną sekwencję standardowej biblioteki języka C++, której zakres jest zdefiniowany przez `begin()` i `end()` . Nazwa zadeklarowana w `for-range-declaration` części jest lokalną **`for`** instrukcją i nie może być ponownie zadeklarowana w `expression` lub `statement` . Należy zauważyć, że [`auto`](../cpp/auto-cpp.md) słowo kluczowe jest preferowany w `for-range-declaration` części instrukcji.

**Nowość w programie Visual Studio 2017:**  Pętle oparte na zakresie **`for`** nie wymagają już, aby `begin()` obiekty tego samego typu i nie były `end()` zwracane. Umożliwia to `end()` zwrócenie obiektu wskaźnikowego, takiego jak używany przez zakresy, zgodnie z definicją w propozycjach zakres-v3. Aby uzyskać więcej informacji, zobacz [uogólnianie `For` pętli opartej na zakresie](https://wg21.link/p0184r0) oraz [biblioteki zakresu-V3 w serwisie GitHub](https://github.com/ericniebler/range-v3).

Ten kod pokazuje, jak używać pętli opartych na zakresie **`for`** do iteracji przez tablicę i wektor:

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

Pętla oparta na zakresie **`for`** kończy się, gdy jedno z nich `statement` jest wykonywane: a [`break`](../cpp/break-statement-cpp.md) , [`return`](../cpp/return-statement-cpp.md) , lub [`goto`](../cpp/goto-statement-cpp.md) do instrukcji oznaczonej poza pętlą opartą na zakresie **`for`** . [`continue`](../cpp/continue-statement-cpp.md)Instrukcja w pętli opartej na zakresie **`for`** kończy tylko bieżącą iterację.

Weź pod uwagę następujące fakty dotyczące zakresu **`for`** :

- Automatycznie rozpoznaje tablice.

- Rozpoznaje kontenery, które mają `.begin()` i `.end()` .

- Używa wyszukiwania zależnego od argumentów `begin()` i `end()` innych elementów.

## <a name="see-also"></a>Zobacz także

[`auto`](../cpp/auto-cpp.md)<br/>
[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[`while`Instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[`do-while`Instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[`for`Instrukcja (C++)](../cpp/for-statement-cpp.md)
