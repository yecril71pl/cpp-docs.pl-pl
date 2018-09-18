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
ms.openlocfilehash: 0e4486bc3106bd438c7a963ca241465cbc167710
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035208"
---
# <a name="range-based-for-statement-c"></a>Range-based for — instrukcja (C++)

Wykonuje `statement` wielokrotnie i sekwencyjnie dla każdego elementu w `expression`.

## <a name="syntax"></a>Składnia

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Uwagi

Użyj bazująca na zakresie **dla** instrukcji do konstruowania pętli, które muszą być wykonywane za pomocą "wielu", która jest zdefiniowana jako wszystkich elementów, które można wykonać iterację — na przykład `std::vector`, wszelkie inne standardowej biblioteki języka C++ sekwencji, której zakres jest definicją `begin()` i `end()`. Nazwa, która jest zadeklarowana w `for-range-declaration` jest lokalną grupą część **dla** instrukcji i nie może być ponownie zadeklarowany w `expression` lub `statement`. Należy pamiętać, że [automatycznie](../cpp/auto-cpp.md) — słowo kluczowe jest preferowane w `for-range-declaration` część instrukcji.

**Nowość w programie Visual Studio 2017:** opartej na zakresie dla pętli nie jest już wymagany, czy begin() i metodę end() zwracają obiektów tego samego typu. Dzięki temu metoda end() zwracać obiekt wartownik, takie jak używane przez zakresy zgodnie z definicją w propozycji zakresów V3. Aby uzyskać więcej informacji, zobacz [uogólnianie bazująca na zakresie pętli For](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) i [biblioteki zakresu v3 w serwisie GitHub](https://github.com/ericniebler/range-v3).

Ten kod przedstawia sposób użycia oparte na zakresie **dla** pętli, aby wykonać iterację tablicy i wektor:

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

Opartej na zakresie **dla** pętli skończy się, gdy jeden z tych `statement` jest wykonywana: [podziału](../cpp/break-statement-cpp.md), [zwracają](../cpp/return-statement-cpp.md), lub [przejdź do](../cpp/goto-statement-cpp.md) się etykietą instrukcji poza bazująca na zakresie **dla** pętli. A [nadal](../cpp/continue-statement-cpp.md) instrukcji w opartej na zakresie **dla** pętli kończy tylko bieżącą iterację.

Należy pamiętać fakty te informacje oparte na zakresie **dla**:

- Automatycznie rozpoznaje tablic.

- Rozpoznaje kontenerów, które mają `.begin()` i `.end()`.

- Używa wyszukiwania zależnego od argumentów `begin()` i `end()` dla żadnych innych czynności.

## <a name="see-also"></a>Zobacz także

[auto](../cpp/auto-cpp.md)<br/>
[Instrukcje iteracji](../cpp/iteration-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[while, instrukcja (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while, instrukcja (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for, instrukcja (C++)](../cpp/for-statement-cpp.md)