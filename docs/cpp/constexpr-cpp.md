---
title: constexpr (C++)
description: Wskazówki dotyczące słowa C++ kluczowego constexpr języka.
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
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821782"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

Słowo kluczowe **constexpr** zostało wprowadzone w języku c++ 11 i udoskonalone w języku c++ 14. Oznacza *stałe wyrażenie*. Podobnie jak **const** , można go zastosować do zmiennych: błąd kompilatora jest wywoływany, gdy kod próbuje zmodyfikować wartość. W przeciwieństwie do **const** , **constexpr** można również stosować do funkcji i konstruktorów klas. **constexpr** wskazuje, że wartość lub wartość zwracana jest stała i, gdzie to możliwe, jest obliczana w czasie kompilacji.

Wartości całkowitej **constexpr** można użyć wszędzie tam, gdzie jest wymagana const liczba całkowita, na przykład w argumentach szablonu i deklaracjach tablicowych. A gdy wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania, pomaga ona działać szybciej i używać mniejszej ilości pamięci.

Aby ograniczyć złożoność obliczeń stałych czasu kompilacji i ich potencjalną wpływ na czas kompilacji, standard C++ 14 wymaga, aby typy w wyrażeniach stałych były [typami literałów](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Składnia

> **constexpr** identyfikator *typu literału* **=** *wyrażenie stałe* **;** \
> **constexpr** *Identyfikator typu literał* **{** *stała-Expression* **}** **;** \
> *Identyfikator* *typu literału* **constexpr** **(** *params* **)** **;** \
> **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*parametry*\
Co najmniej jeden parametr, z którego każdy musi być typem literału i musi być wyrażeniem stałym.

## <a name="return-value"></a>Wartość zwracana

Zmienna **constexpr** lub funkcja musi zwracać [Typ literału](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="opno-locconstexpr-variables"></a>zmienne constexpr

Podstawowa różnica między zmiennymi **const** i **constexpr** polega na tym, że inicjalizacja zmiennej **const** może zostać odroczona do czasu wykonywania. Zmienna **constexpr** musi zostać zainicjowana w czasie kompilacji.  **const** wszystkie zmienne **constexpr** .

- Zmienna może być zadeklarowana przy użyciu **constexpr** , gdy ma typ literału i jest inicjowana. Jeśli inicjalizacja jest wykonywana przez konstruktora, Konstruktor musi być zadeklarowany jako **constexpr** .

- Odwołanie może być zadeklarowane jako **constexpr** , gdy oba te warunki są spełnione: przywoływany obiekt jest inicjowany przez wyrażenie stałe i wszystkie niejawne konwersje wywoływane podczas inicjowania są również wyrażeniami stałymi.

- Wszystkie deklaracje zmiennej **constexpr** lub funkcji muszą mieć specyfikator **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funkcje constexpr

Funkcja **constexpr** to jedna, której wartość zwracana jest obliczanej w czasie kompilacji, gdy wymaga użycia kodu. Kod zużywający wymaga wartości zwracanej w czasie kompilacji w celu zainicjowania zmiennej **constexpr** lub podania argumentu szablonu bez typu. Gdy argumenty są **constexpr** wartości, funkcja **constexpr** generuje stałą czasu kompilacji. Gdy jest wywoływana z argumentami innymi niż **constexpr** lub gdy jego wartość nie jest wymagana w czasie kompilacji, generuje wartość w czasie wykonywania, jak zwykła funkcja. (To podwójne zachowanie umożliwia zapisanie **constexpr** i **nieconstexpr** wersji tej samej funkcji).

Niejawnie **inline** funkcji **constexpr** lub konstruktora.

Do funkcji constexpr są stosowane następujące reguły:

- Funkcja **constexpr** musi akceptować i zwracać tylko [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

- Funkcja **constexpr** może być cykliczna.

- Nie może być [wirtualna](../cpp/virtual-cpp.md). Nie można zdefiniować konstruktora jako **constexpr** , gdy otaczająca Klasa ma wszystkie wirtualne klasy bazowe.

- Treść można zdefiniować jako `= default` lub `= delete`.

- Treść nie może zawierać żadnych instrukcji **goto** ani bloków **try** .

- Jawna specjalizacja szablonu innego niż **constexpr** można zadeklarować jako **constexpr** :

- Jawna specjalizacja szablonu **constexpr** nie może być również **constexpr** :

Następujące reguły mają zastosowanie do funkcji **constexpr** w programie Visual Studio 2017 i nowszych:

- Może zawierać instrukcje **if** i **switch** , a także wszystkie instrukcje pętli, w tym **for** , **for** na podstawie zakresu, **while** i **dowhile** .

- Może zawierać deklaracje zmiennych lokalnych, ale zmienna musi być zainicjowana. Musi być typem literału i nie może być **statyczny** ani lokalny wątku. Zmienna zadeklarowana lokalnie nie jest wymagana do **const** i może ulec mutacji.

- **Niestatyczna** funkcja członkowska **constexpr** nie musi być niejawnie **const** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> W debugerze programu Visual Studio podczas debugowania niezoptymalizowanej kompilacji debugowania można sprawdzić, czy funkcja **constexpr** jest szacowana w czasie kompilacji, umieszczając w niej punkt przerwania. Po trafieniu punktu przerwania funkcja została wywołana w czasie wykonywania.  Jeśli nie, funkcja została wywołana w czasie kompilacji.

## <a name="extern-opno-locconstexpr"></a>constexpr extern

Opcja kompilatora [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) powoduje, że kompilator zastosuje [zewnętrzne połączenie](../c-language/external-linkage.md) do zmiennych zadeklarowanych za pomocą **constexprextern** . We wcześniejszych wersjach programu Visual Studio, domyślnie lub gdy **/Zc: externConstexpr-** jest określony, program Visual Studio stosuje połączenie wewnętrzne do zmiennych **constexpr** nawet wtedy, gdy jest używane słowo kluczowe **extern** . Opcja **/Zc: externConstexpr** jest dostępna począwszy od programu Visual Studio 2017 Update 15,6 i jest domyślnie wyłączona. Opcja [/permissive-](../build/reference/permissive-standards-conformance.md) nie włącza **/Zc: externConstexpr**.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia zmienne **constexpr** , funkcje i typ zdefiniowany przez użytkownika. W ostatniej instrukcji w `main()`, **constexpr** funkcja członkowska `GetValue()` jest wywołaniem w czasie wykonywania, ponieważ wartość nie jest wymagana, aby była znana w czasie kompilacji.

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
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

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
