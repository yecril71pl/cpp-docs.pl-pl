---
title: Wyrażenia lambda w języku C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 6fcc26c3ed86c86264773a70ac16501c102e1861
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213336"
---
# <a name="lambda-expressions-in-c"></a>Wyrażenia lambda w języku C++

W języku C++ 11 i nowszych wyrażenia lambda — często nazywane wyrażeniem *lambda*— jest wygodnym sposobem definiowania anonimowego obiektu funkcji ( *zamykania*) w miejscu, w którym jest wywoływana lub przenoszona jako argument do funkcji. Zazwyczaj wyrażenia lambda są używane do hermetyzacji kilku wierszy kodu, które są przesyłane do algorytmów lub metod asynchronicznych. W tym artykule zdefiniowano, czym są lambdy, porównano je z innymi technikami programowania, omówiono ich zalety i dostarczono podstawowe przykłady.

## <a name="related-topics"></a>Tematy pokrewne

- [Wyrażenia lambda a obiekty funkcji](lambda-expression-syntax.md)
- [Praca z wyrażeniami lambda](examples-of-lambda-expressions.md)
- [constexpr, wyrażenia lambda](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Części wyrażenia lambda

Standard ISO C++ pokazuje proste wyrażenie lambda, które jest przesyłane jako trzeci argument do `std::sort()` funkcji:

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

Na tej ilustracji przedstawiono części wyrażenia lambda:

![Elementy strukturalne wyrażenia lambda](../cpp/media/lambdaexpsyntax.png "Elementy strukturalne wyrażenia lambda")

1. *klauzula Capture* (znana również jako *wprowadzenie wyrażenia lambda* w specyfikacji języka C++)

1. *Lista parametrów* Obowiązkowe. (Znany również jako *deklarator lambda*)

1. *Specyfikacja modyfikowalna* Obowiązkowe.

1. *Specyfikacja wyjątku* Obowiązkowe.

1. *końcowe — typ zwracany* Obowiązkowe.

1. *treść lambda*.

### <a name="capture-clause"></a>Klauzula przechwytywania

Wyrażenie lambda może wprowadzać nowe zmienne w swojej treści (w **języku C++ 14**) i może również uzyskać dostęp do zmiennych lub *przechwycić*je z zakresu otaczającego. Lambda zaczyna się od klauzuli przechwytywania (*wyrażenie lambda* w standardowej składni), która określa zmienne, które są przechwytywane oraz czy przechwytywanie jest przez wartość, czy przez odwołanie. Zmienne, które mają prefiks handlowego "i" ( `&` ) są dostępne przez odwołanie i zmienne, które nie są dostępne przez wartość.

Pusta Klauzula przechwytywania, `[ ]` , wskazuje, że treść wyrażenia lambda nie uzyskuje dostępu do żadnych zmiennych w zakresie otaczającym.

Można użyć domyślnego trybu przechwytywania (wartość*Domyślna przechwytywania* w standardowej składni), aby wskazać, jak przechwycić wszystkie zmienne zewnętrzne, do których odwołuje się wyrażenie lambda: `[&]` oznacza, że wszystkie zmienne, do których odwołuje się, są przechwytywane przez odwołanie i oznacza, że `[=]` są przechwytywane przez wartość. Można użyć domyślnego trybu przechwytywania, a następnie jawnie określić tryb odwrotny dla określonych zmiennych. Na przykład jeśli treść wyrażenia lambda uzyskuje dostęp do zewnętrznej zmiennej `total` przez odwołanie i zewnętrzną zmienną `factor` według wartości, następujące klauzule przechwytywania są równoważne:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Podczas używania przechwytywania domyślnego są przechwytywane tylko zmienne, które są wymienione w wyrażeniach lambda.

Jeśli klauzula przechwytywania zawiera funkcję przechwytywania domyślnego `&` , a następnie nie ma `identifier` jej w `capture` klauzuli przechwytywania, może mieć postać `& identifier` . Podobnie, Jeśli klauzula Capture zawiera funkcję przechwytywania domyślnego `=` , a następnie żadna `capture` z tych klauzuli przechwytywania nie może mieć formularza `= identifier` . Identyfikator lub **`this`** nie może występować więcej niż raz w klauzuli Capture. Poniższy fragment kodu ilustruje kilka przykładów.

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

Przechwytywanie, po którym następuje wielokropek, jest rozwinięciem pakietu, jak pokazano w tym przykładzie [szablonu wariadyczne](../cpp/ellipses-and-variadic-templates.md) :

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Aby użyć wyrażeń lambda w treści metody klasy, Przekaż **`this`** wskaźnik do klauzuli przechwytywania, aby zapewnić dostęp do metod i składowych danych otaczającej klasy.

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): **`this`** wskaźnik może być przechwytywany przez wartość przez określenie **`*this`** w klauzuli Capture. Przechwyć według wartości oznacza, że całe *Zamknięcie*, które jest obiektem funkcji anonimowej, który encapulates wyrażenie lambda, jest kopiowane do każdej lokacji wywołań, w której jest wywoływana lambda. Przechwytywanie według wartości jest przydatne, gdy lambda będzie wykonywana w operacjach równoległych lub asynchronicznych, szczególnie w przypadku niektórych architektur sprzętowych, takich jak NUMA.

Aby zapoznać się z przykładem, który pokazuje, jak używać wyrażeń lambda z metodami klasy, zobacz "przykład: Używanie wyrażenia lambda w metodzie" w [przykładach wyrażeń lambda](../cpp/examples-of-lambda-expressions.md).

W przypadku korzystania z klauzuli Capture zaleca się pozostawienie tych punktów, szczególnie w przypadku używania wyrażeń lambda z wielowątkowością:

- Przechwytywania odwołań można użyć do modyfikacji zmiennych poza, ale przechwytywanie wartości nie może. ( **`mutable`** umożliwia modyfikowanie kopii, ale nie ich oryginałów).

- Przechwytywanie odwołań odzwierciedla aktualizacje zmiennych poza, ale przechwycenia wartości nie.

- Przechwytywanie odwołań wprowadza zależność okresu istnienia, ale przechwycenia wartości nie ma zależności okresu istnienia. Jest to szczególnie ważne, gdy lambda przebiega asynchronicznie. W przypadku przechwycenia elementu lokalnego przez odwołanie w asynchronicznym wyrażeniu lambda, ten lokalny będzie bardzo prawdopodobnie wypadał przez czas, gdy zostanie uruchomione wyrażenie lambda, co spowodowało naruszenie zasad dostępu w czasie wykonywania.

### <a name="generalized-capture-c-14"></a>Przechwytywanie uogólnione (C++ 14)

W języku C++ 14 można wprowadzać i inicjować nowe zmienne w klauzuli Capture bez konieczności, aby te zmienne istniały w zakresie otaczającym funkcję lambda. Inicjowanie można wyrazić jako dowolne dowolne wyrażenie; Typ nowej zmiennej jest wywnioskowany na podstawie typu utworzonego przez wyrażenie. Jedną z zalet tej funkcji jest to, że w języku C++ 14 można przechwytywać zmienne tylko do przenoszenia (takie jak std:: unique_ptr) z otaczającego zakresu i używać ich w wyrażeniach lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Lista parametrów

Oprócz zmiennych przechwytywania wyrażenie lambda może akceptować parametry wejściowe. Lista parametrów (*lambda deklarator* w standardowej składni) jest opcjonalna i w większości aspektów przypomina listę parametrów dla funkcji.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

W **języku C++ 14**, jeśli typem parametru jest ogólne, można użyć **`auto`** słowa kluczowego jako specyfikatora typu. Nakazuje kompilatorowi utworzenie operatora wywołania funkcji jako szablonu. Każde wystąpienie elementu **`auto`** na liście parametrów jest równoważne parametrowi typu DISTINCT.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Wyrażenie lambda może przyjmować inne wyrażenie lambda jako argument. Aby uzyskać więcej informacji, zobacz "wyrażenia lambda wyższego rzędu" w temacie [Przykłady wyrażeń lambda](../cpp/examples-of-lambda-expressions.md).

Ponieważ lista parametrów jest opcjonalna, można pominąć puste nawiasy, jeśli nie przechodzą argumentów do wyrażenia lambda, a jego lambda-deklarator nie zawiera *specyfikacji wyjątku*, *końcowego-return-Type*lub **`mutable`** .

### <a name="mutable-specification"></a>Specyfikacja modyfikowalna

Zazwyczaj operator wywołania funkcji lambda to stała wartość, ale użycie **`mutable`** słowa kluczowego anuluje to. Nie produkuje modyfikowalnych elementów członkowskich danych. Specyfikacja modyfikowalna umożliwia treści wyrażenia lambda modyfikację zmiennych, które są przechwytywane przez wartość. W niektórych przykładach w dalszej części tego artykułu pokazano, jak korzystać z programu **`mutable`** .

### <a name="exception-specification"></a>Specyfikacja wyjątku

Można użyć **`noexcept`** specyfikacji wyjątku, aby wskazać, że wyrażenie lambda nie generuje żadnych wyjątków. Podobnie jak w przypadku funkcji zwykłych, kompilator języka Microsoft C++ generuje ostrzeżenie [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) , jeśli wyrażenie lambda deklaruje **`noexcept`** specyfikację wyjątku i treść lambda zgłasza wyjątek, jak pokazano poniżej:

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

Aby uzyskać więcej informacji, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).

### <a name="return-type"></a>Typ zwracany

Zwracany typ wyrażenia lambda jest automatycznie wywnioskowany. Nie trzeba używać [`auto`](../cpp/auto-cpp.md) słowa kluczowego, chyba że zostanie określony *końcowy typ zwracany*. *Końcowy typ zwracany* jest podobny do części typu zwracanego zwykłej metody lub funkcji. Jednak zwracany typ musi być zgodny z listą parametrów i musi zawierać słowo kluczowe końcowego typu zwracanego **`->`** przed typem zwracanym.

Możesz pominąć część typu zwracanego wyrażenia lambda, jeśli treść lambda zawiera tylko jedną instrukcję return lub wyrażenie nie zwraca wartości. Jeśli treść lambda zawiera jedną instrukcję return, kompilator wywnioskuje typ zwracany z typu wyrażenia Return. W przeciwnym razie kompilator wywnioskuje typ zwracany **`void`** . Rozważmy następujące przykładowe fragmenty kodu, które ilustrują tę zasadę.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Wyrażenie lambda może generować inne wyrażenie lambda jako wartość zwracaną. Aby uzyskać więcej informacji, zobacz sekcję "wyrażenia lambda o wyższej kolejności" w [przykładach wyrażeń lambda](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Treść lambda

Treść lambda (*instrukcja złożona* w standardowej składni) wyrażenia lambda może zawierać wszystko, co może zawierać treść zwykłej metody lub funkcji. Treść zwykłej funkcji i wyrażenia lambda może uzyskiwać dostęp do tego rodzaju zmiennych:

- Przechwycone zmienne z otaczającego zakresu, jak opisano wcześniej.

- Parametry

- Lokalnie deklarowane zmienne

- Elementy członkowskie danych klasy, gdy zadeklarowano wewnątrz klasy i **`this`** są przechwytywane

- Jakakolwiek zmienna, która ma statyczny czas przechowywania — na przykład zmienne globalne

Poniższy przykład zawiera wyrażenie lambda, które jawnie przechwytuje zmienną `n` według wartości i niejawnie przechwytuje zmienną `m` według odwołania:

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

Ponieważ zmienna `n` jest przechwytywana przez wartość, jej wartość pozostaje `0` po wywołaniu wyrażenia lambda. **`mutable`** Specyfikacja może `n` być modyfikowana w wyrażeniu lambda.

Mimo że wyrażenie lambda może przechwytywać tylko zmienne, które mają automatyczny czas trwania przechowywania, można używać zmiennych o statycznym czasie trwania przechowywania w treści wyrażenia lambda. Poniższy przykład używa `generate` funkcji i wyrażenia lambda do przypisania wartości do każdego elementu w `vector` obiekcie. Wyrażenie lambda modyfikuje zmienną statyczną, aby wygenerować wartość następnego elementu.

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

Aby uzyskać więcej informacji, zobacz [generowanie](../standard-library/algorithm-functions.md#generate).

Poniższy przykład kodu używa funkcji z poprzedniego przykładu i dodaje przykład wyrażenia lambda, które używa standardowej biblioteki języka C++ `generate_n` . To wyrażenie lambda przypisuje element `vector` obiektu do sumy poprzednich dwóch elementów. **`mutable`** Słowo kluczowe jest używane, aby treść wyrażenia lambda mogła zmodyfikować jego kopie zmiennych zewnętrznych `x` i `y` , które wyrażenie lambda przechwytuje przez wartość. Ponieważ wyrażenie lambda przechwytuje oryginalne zmienne `x` i `y` według wartości, ich wartości pozostają `1` po wykonaniu lambda.

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

Aby uzyskać więcej informacji, zobacz [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="constexpr-lambda-expressions"></a>`constexpr`wyrażenia lambda

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępne z [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): wyrażenie lambda może być zadeklarowane jako **`constexpr`** lub używane w wyrażeniu stałym, gdy Inicjalizacja każdego elementu członkowskiego danych, który przechwytuje lub wprowadza, jest dozwolony w wyrażeniu stałym.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Wyrażenie lambda jest niejawnie, **`constexpr`** jeśli jego wynik spełnia wymagania **`constexpr`** funkcji:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Jeśli wyrażenie lambda jest niejawnie lub jawne **`constexpr`** , konwersja na wskaźnik funkcji generuje **`constexpr`** funkcję:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

Wyrażenia lambda nie są obsługiwane w następujących jednostkach zarządzanych środowiska uruchomieniowego języka wspólnego (CLR): **`ref class`** , **`ref struct`** , **`value class`** , lub **`value struct`** .

Jeśli używasz modyfikatora specyficznego dla firmy Microsoft, takiego jak [`__declspec`](../cpp/declspec.md) , możesz wstawić go do wyrażenia lambda bezpośrednio po `parameter-declaration-clause` — na przykład:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Aby określić, czy modyfikator jest obsługiwany przez wyrażenia lambda, zobacz artykuł dotyczący tego elementu w sekcji [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md) w dokumentacji.

Poza standardowymi funkcjami lambda języka C++ 11 program Visual Studio obsługuje bezstanowe wyrażenia lambda, które są zamiennie konwertowane do wskaźników funkcji, które korzystają z dowolnych konwencji wywoływania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Obiekty funkcji w standardowej bibliotece języka C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Wywołanie funkcji](../cpp/function-call-cpp.md)<br/>
[`for_each`](../standard-library/algorithm-functions.md#for_each)
