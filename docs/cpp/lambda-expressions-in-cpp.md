---
title: Wyrażenia lambda w języku C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: c7543b3558da88b41102fa7b790bb9d9f3f18463
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222383"
---
# <a name="lambda-expressions-in-c"></a>Wyrażenia lambda w języku C++

W języku C ++ 11 i nowszych wersjach Wyrażenie lambda — często nazywana *lambda*— to wygodny sposób definiowania obiektu funkcja anonimowa ( *zamknięcia*) bezpośrednio w lokalizacji, gdzie jest wywoływana lub przekazywany jako argument do funkcji. Wyrażenia lambda są zazwyczaj używane w celu hermetyzacji kilku wierszy kodu, które są przekazywane do algorytmów lub metod asynchronicznych. W tym artykule zdefiniowano, czym są lambdy, porównano je z innymi technikami programowania, omówiono ich zalety i dostarczono podstawowe przykłady.

## <a name="related-topics"></a>Tematy pokrewne

- [Wyrażenia lambda, a obiekty funkcji](lambda-expression-syntax.md)
- [Praca z wyrażenia lambda](examples-of-lambda-expressions.md)
- [constexpr lambda expressions](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Części wyrażenia Lambda

Standard ISO C++ pokazuje prosty lambda, który jest przekazywany jako trzeci argument `std::sort()` funkcji:

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

Ta ilustracja przedstawia części wyrażenia lambda:

![Elementy strukturalne wyrażenia lambda](../cpp/media/lambdaexpsyntax.png "elementy strukturalne wyrażenia lambda")

1. *Klauzula przechwytywania* (znany także jako *lambda-introducer* w specyfikacji języka C++.)

1. *Lista parametrów* atrybut opcjonalny. (Nazywane również *lambda declarator*)

1. *Specyfikacja modyfikowalna* atrybut opcjonalny.

1. *Specyfikacja wyjątku* atrybut opcjonalny.

1. *trailing-return-type* atrybut opcjonalny.

1. *Treść lambda*.

### <a name="capture-clause"></a>Klauzula przechwytywania

Wyrażenia lambda mogą wprowadzać nowe zmienne w jej treści (w **C ++ 14**), a także dostęp, lub *przechwytywania*, zmiennych z otaczającego zakresu. Zaczyna się klauzuli przechwytywania wyrażenia lambda (*lambda-introducer* w standardowej składni), który określa zmienne, które są przechwytywane oraz czy przechwytywania to przez wartość lub przez odwołanie. Zmienne, które mają znak ampersand (`&`) prefiks są dostępne dla odwołań i zmienne, które nie mają są dostępne przez wartość.

Klauzula przechwytywania pustego `[ ]`, wskazuje, że treść wyrażenia lambda uzyskuje dostęp do żadnych zmiennych w obejmującym zakresie.

Można użyć domyślny tryb przechwytywania (*domyślna przechwytywania* w standardowej składni) do wskazania sposobu przechwytywania wszelkich zewnętrznych zmiennych, które są określone w wyrażeniu lambda: `[&]` oznacza, że wszystkie zmienne odwołujące do są przechwytywane przez odwołania, a `[=]` oznacza, że są one przechwytywane przez wartość. Można użyć domyślny tryb przechwytywania, a następnie określ tryb przeciwny jawnie określonych zmiennych. Na przykład, jeśli treść lambda uzyskuje dostęp do zewnętrznej zmiennej `total` przez odwołanie, a do zewnętrznej zmiennej `factor` według wartości, następnie następujące klauzule przechwytywania są równoważne:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Tylko te zmienne, które są wymienione w lambdzie są przechwytywane, gdy jest używana wartość domyślna przechwytywania.

Jeśli klauzula przechwytywania zawiera wartość domyślna przechwytywania `&`, a następnie nie `identifier` w `capture` przechwytywania tej klauzuli mogą mieć postaci `& identifier`. Podobnie jeśli klauzula przechwytywania zawiera wartość domyślna przechwytywania `=`, a następnie nie `capture` przechwytywania tej klauzuli mogą mieć postaci `= identifier`. Identyfikator lub **to** nie może występować więcej niż jeden raz w klauzuli przechwytywania. Poniższy fragment kodu ilustruje kilka przykładów.

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

Przechwytywanie następuje wielokropek jest rozwinięciem pakietu, jak pokazano w tym [szablonu wariadycznego](../cpp/ellipses-and-variadic-templates.md) przykładu:

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Aby używać wyrażeń lambda w treści metody klasy, należy przekazać **to** wskaźnik do klauzuli przechwytywania, aby zapewnić dostęp do metod i składowych danych otaczającej klasy.

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **To** wskaźnik mogą być przechwytywane przez wartość, określając `*this` w klauzuli przechwytywania. Przechwytywania przez wartość oznacza, że cały *zamknięcia*, które jest obiektem funkcja anonimowa tego encapulates Wyrażenie lambda, jest kopiowany do każdej lokacji wywołania, gdy wyrażenie lambda jest wywoływana. Przechwytywania przez wartość jest przydatne, gdy wyrażenie lambda będzie wykonywany w operacji równoległych lub asynchroniczny, zwłaszcza w przypadku niektórych architektur sprzętu, takich jak architektura NUMA.

Na przykład, który pokazuje, jak używać wyrażeń lambda z metodami klasy, zobacz "przykład: Użycie wyrażenia Lambda w metodzie"w [przykłady wyrażeń Lambda](../cpp/examples-of-lambda-expressions.md).

Użycie klauzuli przechwytywania, zaleca się utrzymywanie tych punktów należy pamiętać, szczególnie w przypadku, gdy używasz wyrażeń lambda z wielowątkowością:

- Przechwytywania przez odniesienie może służyć do modyfikacji zmiennych na zewnątrz, ale nie przechwytywania przez wartość. (**mutable** umożliwia kopii, które ma zostać zmodyfikowana, ale nie oryginału.)

- Przechwytywania przez odniesienie odzwierciedlały aktualizacje zmiennych na zewnątrz, ale nie obsługują przechwytywania przez wartość.

- Przechwytywania przez odniesienie wprowadzają zależność okresu istnienia, ale przechwytywania przez wartość nie ma żadnych zależności okresu istnienia. Jest to szczególnie ważne w przypadku, gdy wyrażenie lambda jest uruchamiane asynchronicznie. Jeśli lokalny jest przechwytywane przez odwołanie w lambdy asynchronicznej, że lokalny bardzo prawdopodobnie znikną przez przy uruchomieniu Wyrażenie lambda, spowodowało naruszenie zasad dostępu w czasie wykonywania.

### <a name="generalized-capture-c-14"></a>Przechwytywanie uogólnionej (C++ 14)

W języku C ++ 14 możesz wprowadzić, a zainicjować nowe zmienne w klauzuli przechwytywania, bez konieczności posiadania tych zmiennych w zasięgu funkcji lambda. Inicjowanie mogą być wyrażone jako dowolne wyrażenie dowolnego; Typ nowej zmiennej jest wnioskowany z typu, o których produkowane przez wyrażenie. Jedną z zalet tej funkcji jest, że w języku C ++ 14 można przechwytywać obsługujące tylko przenoszenie zmienne (na przykład std::unique_ptr) z otaczającego zakresu i używać ich w wyrażenia lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Lista parametrów

Oprócz zmiennych, wyrażenia lambda może akceptować parametry wejściowe. Lista parametrów (*lambda declarator* w standardowej składni) jest opcjonalny, a w większości aspektów odpowiada liście parametrów dla funkcji.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

W **C++ 14**, jeśli typ parametru jest ogólna, można użyć słowa kluczowego auto jako Specyfikator typu. Informuje kompilator, aby utworzyć operator wywołania funkcji jako szablon. Każde wystąpienie automatycznie na liście parametrów jest równoważna z parametrem distinct typu.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Wyrażenie lambda może przyjmować inne wyrażenie lambda jako argument. Aby uzyskać więcej informacji, zobacz "Wyrażenia Lambda wyższego rzędu" w temacie [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

Ponieważ parametr jest opcjonalny, puste nawiasy można pominąć, jeśli nie przepuszczasz argumentów do wyrażenia lambda i nie zawiera jego lambda-declarator *Specyfikacja wyjątku*,  *trailing-return-type*, lub **mutable**.

### <a name="mutable-specification"></a>Specyfikacja modyfikowalna

Zazwyczaj operator wywołania funkcji lambda to stała wartość, ale użytkowania **mutable** to anuluje przez słowo kluczowe. Nie generuje to modyfikowalnych elementów członkowskich danych. Specyfikacja modyfikowalna umożliwia treści wyrażenia lambda modyfikację zmiennych, które są przechwytywane przez wartość. Przykłady w dalszej części tego artykułu przedstawiono sposoby używania **mutable**.

### <a name="exception-specification"></a>Specyfikacja wyjątku

Możesz użyć `noexcept` Specyfikacja wyjątku, aby wskazać, że wyrażenie lambda nie generuje żadnych wyjątków. Podobnie jak w przypadku zwykłej funkcji Microsoft C++ kompilator generuje ostrzeżenie [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) jeżeli wyrażenie lambda deklaruje `noexcept` Specyfikacja wyjątku i treść lambda zgłasza wyjątek, jak pokazano poniżej:

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

Zwracany typ wyrażenia lambda jest wyprowadzony automatycznie. Nie trzeba stosować [automatycznie](../cpp/auto-cpp.md) — słowo kluczowe, chyba że określisz *trailing-return-type*. *Trailing-return-type* przypomina część zwracanego typu zwykłej metody lub funkcji. Jednak zwracany typ musi stosować się na liście parametrów i musi zawierać słowo kluczowe trailing-return-type `->` przed zwracanym typem.

Możesz pominąć część zwracanego typu wyrażenia lambda, jeżeli treść lambda zawiera tylko jedną instrukcję return lub wyrażenie nie zwraca wartości. Jeżeli treść lambda zawiera jedną instrukcję return, kompilator określi typ zwracany z typu wyrażenia return. W przeciwnym razie kompilator określi typ zwrotu na **void**. Rozważmy następujące przykładowe fragmenty kodu, które ilustrują tę zasadę.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Wyrażenie lambda może generować inne wyrażenie lambda jako wartość zwracaną. Aby uzyskać więcej informacji, zobacz "Wyrażenia Lambda wyższego rzędu" w [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Treść lambda

Treść lambda (*compound-statement* w standardowej składni) wyrażenia lambda wyrażenia może zawierać wszystko, co może zawierać treść zwykłej metody lub funkcji. Treść zwykłej funkcji i wyrażenia lambda mogą uzyskiwać dostęp do tego rodzaju zmiennych:

- Przechwycone zmienne z otaczającego zakresu, zgodnie z wcześniejszym opisem.

- Parametry

- Lokalnie deklarowane zmienne

- Składowe danych, klasy, gdy zadeklarowana wewnątrz klasy i **to** są przechwytywane

- Jakakolwiek zmienna, która ma statyczny czas magazynowania — na przykład, zmienne globalne

Poniższy przykład zawiera wyrażenie lambda, które jawnie przechwytuje zmienną `n` według wartości i niejawnie przechwytuje zmienną `m` przez odwołanie:

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

Ponieważ zmienna `n` jest przechwytywana przez wartość, jej wartośc pozostaje `0` po wywołaniu wyrażneia lambda. **Mutable** umożliwia specyfikację `n` można zmodyfikować w ramach lambda.

Mimo że wyrażenie lambda może przechwytywać tylko zmienne, które mają automatyczny czas trwania przechowywania, można używać zmiennych o statycznym czasie trwania przechowywania w treści wyrażenia lambda. W poniższym przykładzie użyto `generate` funkcji i wyrażenia lambda do przypisania wartości do każdego elementu w `vector` obiektu. Wyrażenie lambda modyfikuje zmienną statyczną, aby wygenerować wartość następnego elementu.

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

Aby uzyskać więcej informacji, zobacz [Generowanie](../standard-library/algorithm-functions.md#generate).

Poniższy przykład kodu używa funkcji z poprzedniego przykładu i dodano przykład wyrażenia lambda, które używa algorytmu standardowej biblioteki języka C++ `generate_n`. To wyrażenie lambda przypisuje element obiektu `vector` do sumy dwóch poprzednich elementów. **Mutable** słowo kluczowe jest używane, tak aby treść wyrażenia lambda mogła modyfikować swoje kopie zmiennych zewnętrznych `x` i `y`, które Wyrażenie lambda przechwytuje przez wartość. Ponieważ wyrażenie lambda przechwytuje oryginalne zmienne `x` i `y` według wartości, ich wartości pozostają `1` po wykonaniu lambdy.

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

## <a name="constexpr-lambda-expressions"></a>wyrażenia constexpr, wyrażenia lambda

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Wyrażenie lambda może być zadeklarowana jako `constexpr` lub używany w wyrażeniu stałym, podczas inicjowania każdej składowej danych, który przechwytuje, lub wprowadza jest dozwolona w wyrażeniu stałym.

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

Wyrażenie lambda jest niejawnie `constexpr` Jeśli wynik nie spełnia wymagań `constexpr` funkcji:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Jeśli wyrażenie lambda jest jawnie lub niejawnie `constexpr`, konwersja wskaźnika funkcji tworzy `constexpr` funkcji:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft-Specific

Wyrażenia lambda nie są obsługiwane w następujących jednostkach zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego: **klasy referencyjnej**, **ref struct**, **klasę wartości**, lub **wartość — Struktura** .

Jeśli używasz Modyfikatory specyficzne dla firmy Microsoft takich jak [__declspec](../cpp/declspec.md), Wstaw go do wyrażenia lambda natychmiast po `parameter-declaration-clause`— na przykład:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Aby ustalić, czy modyfikatorem jest obsługiwane przez wyrażenia lambda, zobacz artykuł o nim w [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md) sekcji dokumentacji.

Oprócz funkcje C ++ 11 standardowa lambda program Visual Studio obsługuje bezstanowe lambdy, które można uniwersalnie przekonwertować do wskaźników funkcji, które używają dowolne Konwencje wywoływania.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Obiekty funkcji w standardowej bibliotece C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Wywołanie funkcji](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
