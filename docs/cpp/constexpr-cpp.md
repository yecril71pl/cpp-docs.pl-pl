---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821100"
---
# <a name="constexpr-c"></a>constexpr (C++)

Słowo kluczowe **constexpr** zostało wprowadzone w języku c++ 11 i udoskonalone w języku c++ 14. Oznacza *stałe wyrażenie*. Podobnie jak **stała**, może być stosowana do zmiennych, aby błąd kompilatora był wywoływany, jeśli którykolwiek kod próbuje zmodyfikować wartość. W przeciwieństwie do **const**, **constexpr** można również zastosować do funkcji i konstruktorów klas. **constexpr** wskazuje, że wartość lub wartość zwracana jest stała i, jeśli to możliwe, jest obliczana w czasie kompilacji.

Wartość Całka **constexpr** może być używana wszędzie tam, gdzie jest wymagana stała liczba całkowita, na przykład w argumentach szablonu i deklaracjach tablicowych. A jeśli wartość może być obliczana w czasie kompilacji, a nie w czasie wykonywania, może pomóc programowi szybciej pracować i używać mniejszej ilości pamięci.

Aby ograniczyć złożoność obliczeń stałych czasu kompilacji i ich potencjalną wpływ na czas kompilacji, standard C++ 14 wymaga, aby typy w wyrażeniach stałych były [typami literałów](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Składnia

> **wyrażenia constexpr** *typem literału* *identyfikator* **=** *wyrażenie_stałe* **;** 
>  **constexpr** *typem literału* *identyfikator* **{** *wyrażenia stałego* **}** **;** 
>  **constexpr** *typem literału* *identyfikator* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*params*<br/>
Co najmniej jeden parametr, z którego każdy musi być typem literału i musi być wyrażeniem stałym.

## <a name="return-value"></a>Wartość zwracana

Zmienna constexpr lub funkcja musi zwracać [Typ literału](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>zmienne constexpr

Podstawowa różnica między zmiennymi const i constexpr polega na tym, że inicjalizacja zmiennej stałej może zostać odroczona do czasu wykonywania. Zmienna constexpr musi zostać zainicjowana w czasie kompilacji.  Wszystkie zmienne constexpr to const.

- Zmienna może być zadeklarowana z wyrażeniem **constexpr**, jeśli ma typ literału i jest inicjowana. Jeśli inicjalizacja jest wykonywana przez konstruktora, Konstruktor musi być zadeklarowany jako **constexpr**.

- Odwołanie może być zadeklarowane jako constexpr, jeśli obiekt, do którego się odwołuje, został zainicjowany przez wyrażenie stałe i wszystkie niejawne konwersje, które są wywoływane podczas inicjowania, również są wyrażeniami stałymi.

- Wszystkie deklaracje zmiennej lub funkcji **constexpr** muszą mieć specyfikator **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funkcje constexpr

Funkcja **constexpr** jest jedną, której wartość zwracana może być obliczana w czasie kompilacji, gdy wymaga użycia kodu. Kod zużywający wymaga wartości zwracanej w czasie kompilacji, na przykład w celu zainicjowania zmiennej **constexpr** lub podania argumentu szablonu bez typu. Gdy argumenty są wartościami **constexpr** , funkcja **constexpr** generuje stałą czasu kompilacji. Gdy jest wywoływana z argumentami**nieconstexpr** lub gdy jego wartość nie jest wymagana w czasie kompilacji, generuje wartość w czasie wykonywania, jak zwykła funkcja. (To podwójne zachowanie powoduje, że nie trzeba pisać elementów **constexpr** i non-**constexpr** tej samej funkcji).

Funkcja **constexpr** lub Konstruktor jest niejawnie **wbudowana**.

Następujące reguły mają zastosowanie do funkcji constexpr:

- Funkcja **constexpr** musi akceptować i zwracać tylko [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

- Funkcja **constexpr** może być cykliczna.

- Nie może być [wirtualna](../cpp/virtual-cpp.md). Nie można zdefiniować konstruktora jako constexpr, jeśli otaczająca Klasa ma jakiekolwiek wirtualne klasy bazowe.

- Treść można zdefiniować jako `= default` lub. `= delete`

- Treść nie może zawierać instrukcji **goto** ani bloków try.

- Jawna specjalizacja szablonu innego niż constexpr może być zadeklarowana jako **constexpr**:

- Jawna specjalizacja szablonu **constexpr** nie musi również być wyrażeniem **constexpr**:

Następujące reguły mają zastosowanie do funkcji **constexpr** w programie Visual Studio 2017 i nowszych:

- Może zawierać instrukcje **if** i **Switch** oraz wszystkie instrukcje pętli, w tym **dla**,, **while**, i do **-while**.

- Może zawierać deklaracje zmiennych lokalnych, ale zmienna musi być zainicjowana, musi być typem literału i nie może być statyczna ani lokalna wątku. Lokalna zadeklarowana zmienna nie jest wymagana jako stała i może być mutacja.

- Niestatyczna funkcja członkowska constexpr nie musi być niejawnie stałą.

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> W debugerze programu Visual Studio podczas debugowania niezoptymalizowanej kompilacji debugowania można określić, czy funkcja **constexpr** jest szacowana w czasie kompilacji, umieszczając w niej punkt przerwania. Po trafieniu punktu przerwania funkcja została wywołana w czasie wykonywania.  Jeśli nie, funkcja została wywołana w czasie kompilacji.

## <a name="extern-constexpr"></a>extern constexpr

Opcja kompilatora [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) powoduje, że kompilator zastosuje [zewnętrzny związek](../c-language/external-linkage.md) do zmiennych zadeklarowanych za pomocą elementu **constexpr extern**. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc: externConstexpr-** jest określony, program Visual Studio stosuje wewnętrzne połączenie ze zmiennymi **constexpr** nawet wtedy, gdy jest używane słowo kluczowe **extern** . Opcja **/Zc: externConstexpr** jest dostępna począwszy od programu Visual Studio 2017 Update 15,6 i jest domyślnie wyłączona. Opcja/permissive-nie włącza **/Zc: externConstexpr**.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zmienne **constexpr** , Functions i typ zdefiniowany przez użytkownika. W ostatniej instrukcji w Main (), funkcja elementu członkowskiego **constexpr** GetValue () jest wywołaniem w czasie wykonywania, ponieważ wartość nie jest wymagana, aby była znana w czasie kompilacji.

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
