---
title: constexpr Języków
description: Wskazówki dotyczące constexpr słowa kluczowego języka C++.
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 57ebf4bf69c768bfcd2e4d26a5c3334ca788b08f
ms.sourcegitcommit: a6b97f5d78299ad93675de2fe0f0561f528d26c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90569556"
---
# <a name="no-locconstexpr-c"></a>constexpr Języków

Słowo kluczowe **`constexpr`** zostało wprowadzone w języku c++ 11 i udoskonalone w języku c++ 14. Oznacza * const wyrażenie ANT*. Podobnie **`const`** , można je stosować do zmiennych: błąd kompilatora jest wywoływany, gdy dowolny kod próbuje mod if t wartości. W przeciwieństwie **`const`** **`constexpr`** do, można również zastosować do funkcji i klasy const ructors. **`constexpr`** wskazuje, że wartość lub wartość zwracana jest const Ant i, jeśli jest to możliwe, jest obliczana w czasie kompilacji.

**`constexpr`** Wartość Całka może być używana wszędzie tam const , gdzie jest wymagana liczba całkowita, na przykład w argumentach szablonu i deklaracjach tablicowych. A gdy wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania, pomaga ona działać szybciej i używać mniejszej ilości pamięci.

Aby ograniczyć złożoność obliczeń ANT w czasie kompilacji const i ich potencjalną wpływ na czas kompilacji, w standardzie c++ 14 wymagane są typy w const wyrażeniach ANT, które mają być [typami literałów](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Składnia

> **`constexpr`***Literal-Type* *ident if IER* **=** * const ANT-Expression* **;**\
> **`constexpr`***Literal-Type* *ident if IER* **{** * const ANT-Expression* **}** **;**\
> **`constexpr`***Literal-Type* *ident if IER* **(** *params* **)** **;**\
> **`constexpr`***ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*Krocz*\
Co najmniej jeden parametr, z którego każdy musi być typem literału i musi być const wyrażeniem ANT.

## <a name="return-value"></a>Wartość zwracana

**`constexpr`** Zmienna lub funkcja musi zwracać [Typ literału](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="no-locconstexpr-variables"></a>constexpr modyfikacj

Podstawowy zbiór d if między **`const`** i **`constexpr`** zmienne polega na tym, że inicjalizacja **`const`** zmiennej może zostać odroczona do czasu wykonywania. **`constexpr`** Zmienna musi być inicjowana w czasie kompilacji.  Wszystkie **`constexpr`** zmienne są **`const`** .

- Zmienna może być zadeklarowana przy użyciu **`constexpr`** , gdy ma typ literału i jest inicjowana. Jeśli inicjalizacja jest na for wartość Med przez const ructor, const ructor musi być zadeklarowany jako **`constexpr`** .

- Odwołanie może być zadeklarowane jako, **`constexpr`** gdy oba te warunki są spełnione: obiekt, do którego się odwoływano, jest inicjowany przez const wyrażenie Ant i wszystkie niejawne konwersje wywoływane podczas inicjowania również są const wyrażeniami ANT.

- Wszystkie deklaracje **`constexpr`** zmiennej lub funkcji muszą mieć **`constexpr`** specyfikację if Ier.

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="no-locconstexpr-functions"></a><a name="constexpr_functions"></a>constexprfunkcje

**`constexpr`** Funkcja jest jedną, której wartością zwracaną jest obliczanej w czasie kompilacji, gdy wymaga użycia kodu. Kod zużywający wymaga wartości zwracanej w czasie kompilacji w celu zainicjowania **`constexpr`** zmiennej lub podania argumentu szablonu, który nie jest typem. Gdy argumenty są **`constexpr`** wartościami, **`constexpr`** Funkcja tworzy ANT w czasie kompilacji const . Gdy jest wywoływana z **`constexpr`** argumentami innymi niż argumenty lub gdy jej wartość nie jest wymagana w czasie kompilacji, generuje wartość w czasie wykonywania, jak zwykła funkcja. (To podwójne zachowanie umożliwia zapisanie **`constexpr`** i **`constexpr`** niewersja tej samej funkcji).

**`constexpr`** Funkcja lub const ructor jest niejawnie **`inline`** .

Do funkcji są stosowane następujące reguły constexpr :

- **`constexpr`** Funkcja musi akceptować i zwracać tylko [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

- **`constexpr`** Funkcja może być cykliczna.

- Nie może być [wirtualna](../cpp/virtual-cpp.md). constNie można zdefiniować elementu ructor, tak jakby **`constexpr`** otaczająca Klasa ma jakiekolwiek wirtualne klasy bazowe.

- Treść można zdefiniować jako `= default` lub `= delete` .

- Treść nie może zawierać żadnych **`goto`** instrukcji ani **`try`** bloków.

- Jawna specjalizacja niebędąca **`constexpr`** szablonem może być zadeklarowana jako **`constexpr`** :

- Jawna specjalizacja **`constexpr`** szablonu nie musi być **`constexpr`** :

Następujące reguły mają zastosowanie do **`constexpr`** funkcji w programie Visual Studio 2017 i nowszych:

- Może zawierać **`if`** i **`switch`** instrukcje oraz wszystkie instrukcje pętli, takie jak, **`for`** oparte na zakresie **`for`** , **`while`** ** while **, i do.

- Może zawierać deklaracje zmiennych lokalnych, ale zmienna musi być zainicjowana. Musi być typem literału i nie może być **`static`** ani elementem lokalnym wątku. Zmienna zadeklarowana lokalnie nie jest wymagana **`const`** i może ulec mutacji.

- Funkcja niebędąca **`constexpr`** **`static`** członkiem nie musi być niejawnie **`const`** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}
```

> [!TIP]
> W debugerze programu Visual Studio podczas debugowania niezoptymalizowanej kompilacji debugowania można sprawdzić, czy **`constexpr`** Funkcja jest szacowana w czasie kompilacji, umieszczając w niej punkt przerwania. Po trafieniu punktu przerwania funkcja została wywołana w czasie wykonywania.  Jeśli nie, funkcja została wywołana w czasie kompilacji.

## <a name="extern-no-locconstexpr"></a>modyfikator constexpr

Opcja kompilatora [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) powoduje, że kompilator zastosuje [zewnętrzne połączenie](../c-language/external-linkage.md) ze zmiennymi zadeklarowanymi przy **użyciu constexpr extern **. We wcześniejszych wersjach programu Visual Studio, domyślnie lub gdy **/Zc: externConstexpr-** is spec if IED, program Visual Studio stosuje wewnętrzne połączenie ze **`constexpr`** zmiennymi nawet wtedy, gdy **`extern`** słowo kluczowe jest używane. Opcja **/Zc: externConstexpr** jest dostępna począwszy od programu Visual Studio 2017 Update 15,6 i jest domyślnie wyłączona. Opcja [/permissive-](../build/reference/permissive-standards-conformance.md) nie włącza **/Zc: externConstexpr**.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia **`constexpr`** zmienne, funkcje i typ zdefiniowany przez użytkownika. W ostatniej instrukcji w `main()` , **`constexpr`** funkcja członkowska `GetValue()` jest wywołaniem w czasie wykonywania, ponieważ wartość nie jest wymagana, aby była znana w czasie kompilacji.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
}

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
}

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Wymagania

Program Visual Studio 2015 lub nowszy.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
