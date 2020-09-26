---
title: Składnia wyrażenia lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 8db094dd14e63c08fbe8514f245c1777922224cf
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352716"
---
# <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda

W tym artykule przedstawiono składnię i elementy strukturalne wyrażeń lambda. Aby uzyskać opis wyrażeń lambda, zobacz [lambda Expressions](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Obiekty funkcyjne vs. wyrażenia lambda

Gdy piszesz kod, prawdopodobnie używasz wskaźników funkcji i obiektów funkcyjnych do rozwiązywania problemów i wykonywania obliczeń, szczególnie w przypadku korzystania z [algorytmów standardowej biblioteki języka C++](../standard-library/algorithms.md). Wskaźniki funkcji i obiekty funkcji każdy ma zalety i wady — na przykład wskaźniki funkcji mają minimalny narzut na składnię, ale nie są zachowywane w zakresie, a obiekty funkcyjne mogą zachować stan, ale wymagają obciążenia składniowego w definicji klasy.

Lambda łączy korzyści wskaźników funkcji i obiektów funkcyjnych, unikając ich wad. Podobnie jak w przypadku obiektów Functions, wyrażenie lambda jest elastyczne i może zachować stan, ale w przeciwieństwie do obiektu funkcji, jego zwarta składnia nie wymaga jawnej definicji klasy. Używając wyrażeń lambda, można pisać kod, który jest mniej skomplikowany i mniej podatny na błędy niż kod dla odpowiadających im obiektów funkcyjnych.

W następującym przykładzie porównano użycie wyrażenia lambda z użyciem obiektu funkcyjnego. Pierwszy przykład używa wyrażenia lambda do drukowania do konsoli, czy każdy element w `vector` obiekcie jest parzysty, czy nieparzysty. W drugim przykładzie użyto obiektu funkcyjnego do zrealizowania tego samego zadania.

## <a name="example-1-using-a-lambda"></a>Przykład 1: Używanie wyrażenia lambda

Ten przykład przekazuje wyrażenie lambda do funkcji **for_each** . Lambda drukuje wynik informujący, czy każdy element w `vector` obiekcie jest parzysty, czy nieparzysty.

### <a name="code"></a>Kod

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Komentarze

W przykładzie trzeci argument funkcji **for_each** jest wyrażeniem lambda. `[&evenCount]`Część określa klauzulę przechwytywania wyrażenia, `(int n)` określa listę parametrów, a pozostała część określa treść wyrażenia.

## <a name="example-2-using-a-function-object"></a>Przykład 2: Używanie obiektu funkcyjnego

Czasami wyrażenie lambda byłoby zbyt niewygodne do rozszerzenia dalszego niż w poprzednim przykładzie. W następnym przykładzie przy użyciu obiektu Function zamiast lambda wraz z funkcją **for_each** można generować te same wyniki jako przykład 1. Oba przykłady przechowują liczbę parzystych liczb w `vector` obiekcie. Aby zachować stan operacji, `FunctorClass` Klasa przechowuje `m_evenCount` zmienną przez odwołanie jako zmienną członkowską. Aby wykonać operację, `FunctorClass` implementuje operator wywołania funkcji, **operator ()**. Kompilator języka Microsoft C++ generuje kod, który jest porównywalny w rozmiarze i wydajności do kodu lambda w przykładzie 1. Dla podstawowego problemu, takiego jak w tym artykule, prostsza konstrukcja lambda jest prawdopodobnie lepsza niż konstrukcja obiektu funkcyjnego. Jednak, jeśli istnieje możliwość, że funkcjonalność będzie wymagać znacznego rozszerzenia w przyszłości, można użyć obiektu funkcyjnego, aby ułatwić utrzymywanie kodu.

Aby uzyskać więcej informacji na temat **operatora ()**, zobacz [wywołanie funkcji](../cpp/function-call-cpp.md). Aby uzyskać więcej informacji na temat funkcji **for_each** , zobacz [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Kod

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[utworzenie](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Ostrzeżenie kompilatora (poziom 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)
