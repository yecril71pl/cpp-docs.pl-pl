---
title: Składnia wyrażenia lambda
ms.date: 11/04/2016
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 030960cf8a301575396231cec1a37ff7bed2667f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577479"
---
# <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda

W tym artykule przedstawiono składnię i elementy strukturalne wyrażeń lambda. Aby uzyskać opis wyrażeń lambda, zobacz [wyrażeń Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>A obiekty funkcji Wyrażenia Lambda

Podczas pisania kodu, prawdopodobnie używasz wskaźników funkcji i obiektów funkcyjnych do rozwiązywania problemów i wykonywania obliczeń, zwłaszcza gdy używasz [algorytmami standardowej biblioteki C++](../cpp/algorithms-modern-cpp.md). Wskaźniki funkcji, jak i obiekty funkcyjne mają zalety i wady — na przykład wskaźniki funkcji mają minimalne obciążenie składniowe, ale nie przechowują stanu w zakresie i obiekty funkcyjne mogą przechowywać stan, lecz wymagają obciążenia składniowego definicji klasy.

Lambda łączy korzyści wskaźników funkcji i obiektów funkcyjnych, unikając ich wad. Podobnie jak obiekty funkcyjne Wyrażenie lambda jest elastyczne i może zachowywać stan, ale w przeciwieństwie do obiektów funkcyjnych jego zwarta składnia nie wymaga definicji klasy jawne. Używając wyrażeń lambda, można pisać kod, który jest mniej skomplikowany i mniej podatny na błędy niż kod dla odpowiadających im obiektów funkcyjnych.

W następującym przykładzie porównano użycie wyrażenia lambda z użyciem obiektu funkcyjnego. W pierwszym przykładzie użyto wyrażenia lambda można wyświetlić w konsoli czy każdy element w `vector` obiekt jest parzysta lub nieparzysta. W drugim przykładzie użyto obiektu funkcyjnego do zrealizowania tego samego zadania.

## <a name="example-1-using-a-lambda"></a>Przykład 1: Używanie wyrażenia lambda

Ten przykład przekazuje wyrażenia lambda **for_each** funkcji. Wyrażenie lambda drukuje wynik z informacją, czy każdy element w `vector` obiekt jest parzysta lub nieparzysta.

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
   // Create a vector object that contains 10 elements.
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

### <a name="output"></a>Dane wyjściowe

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

W przykładzie trzeci argument **for_each** funkcji jest wyrażeniem lambda. `[&evenCount]` Część określa klauzulę przechwytywania wyrażenia, `(int n)` Określa listę parametrów, a pozostała część określa treść wyrażenia.

## <a name="example-2-using-a-function-object"></a>Przykład 2: Używanie obiektu funkcyjnego

Czasami wyrażenie lambda byłoby zbyt niewygodne do rozszerzenia dalszego niż w poprzednim przykładzie. W następnym przykładzie użyto obiektu funkcyjnego zamiast wyrażenia lambda, wraz z **for_each** funkcji w celu uzyskania tych samych wyników jak z przykładu 1. Oba przykłady przechowują liczbę liczb parzystych w `vector` obiektu. Aby utrzymywać stan operacji `FunctorClass` klasa przechowuje `m_evenCount` zmiennych przez odwołanie jako zmienną składową. Do wykonania tej operacji `FunctorClass` implementuje operator wywołania funkcji **operator()**. Kompilator Visual C++ generuje kod o rozmiarze i wydajności porównywalnej z kodem wyrażenia lambda z przykładu 1. Dla podstawowego problemu, takiego jak w tym artykule, prostsza konstrukcja lambda jest prawdopodobnie lepsza niż konstrukcja obiektu funkcyjnego. Jednak, jeśli istnieje możliwość, że funkcjonalność będzie wymagać znacznego rozszerzenia w przyszłości, można użyć obiektu funkcyjnego, aby ułatwić utrzymywanie kodu.

Aby uzyskać więcej informacji na temat **operator()**, zobacz [wywołania funkcji](../cpp/function-call-cpp.md). Aby uzyskać więcej informacji na temat **for_each** funkcji, zobacz [for_each](../standard-library/algorithm-functions.md#for_each).

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
    // Create a vector object that contains 10 elements.
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

## <a name="output"></a>Dane wyjściowe

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[Generowanie](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Ostrzeżenie kompilatora (poziom 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)