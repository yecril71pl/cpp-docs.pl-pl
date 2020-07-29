---
title: :::no-loc(constexpr):::Języków
description: 'Wskazówki dotyczące :::no-loc(constexpr)::: słowa kluczowego języka C++.'
ms.date: 01/28/2020
f1_keywords:
- :::no-loc(constexpr):::_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- ':::no-loc(constexpr):::'
- ':::no-loc(const):::'
- ':::no-loc(inline):::'
- ':::no-loc(goto):::'
- ':::no-loc(try):::'
- ':::no-loc(if):::'
- ':::no-loc(switch):::'
- ':::no-loc(for):::'
- ':::no-loc(while):::'
ms.openlocfilehash: d66dc333b7ac9fba94221dc4efa723c7919ef88f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229028"
---
# <a name="no-locconstexpr-c"></a>:::no-loc(constexpr):::Języków

Słowo kluczowe **`:::no-loc(constexpr):::`** zostało wprowadzone w języku c++ 11 i udoskonalone w języku c++ 14. Oznacza * :::no-loc(const)::: wyrażenie ANT*. Podobnie **`:::no-loc(const):::`** , można je stosować do zmiennych: błąd kompilatora jest wywoływany, gdy dowolny kod próbuje mod :::no-loc(if)::: t wartości. W przeciwieństwie **`:::no-loc(const):::`** **`:::no-loc(constexpr):::`** do, można również zastosować do funkcji i klasy :::no-loc(const)::: ructors. **`:::no-loc(constexpr):::`** wskazuje, że wartość lub wartość zwracana jest :::no-loc(const)::: Ant i, jeśli jest to możliwe, jest obliczana w czasie kompilacji.

**`:::no-loc(constexpr):::`** Wartość Całka może być używana wszędzie tam :::no-loc(const)::: , gdzie jest wymagana liczba całkowita, na przykład w argumentach szablonu i deklaracjach tablicowych. A gdy wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania, pomaga ona działać szybciej i używać mniejszej ilości pamięci.

Aby ograniczyć złożoność obliczeń ANT w czasie kompilacji :::no-loc(const)::: i ich potencjalną wpływ na czas kompilacji, w standardzie c++ 14 wymagane są typy w :::no-loc(const)::: wyrażeniach ANT, które mają być [typami literałów](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Składnia

> **`:::no-loc(constexpr):::`***Literal-Type* *ident :::no-loc(if)::: IER* **=** * :::no-loc(const)::: ANT-Expression* **;**\
> **`:::no-loc(constexpr):::`***Literal-Type* *ident :::no-loc(if)::: IER* **{** * :::no-loc(const)::: ANT-Expression* **}** **;**\
> **`:::no-loc(constexpr):::`***Literal-Type* *ident :::no-loc(if)::: IER* **(** *params* **)** **;**\
> **`:::no-loc(constexpr):::`***ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parametry

*Krocz*\
Co najmniej jeden parametr, z którego każdy musi być typem literału i musi być :::no-loc(const)::: wyrażeniem ANT.

## <a name="return-value"></a>Wartość zwracana

**`:::no-loc(constexpr):::`** Zmienna lub funkcja musi zwracać [Typ literału](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="no-locconstexpr-variables"></a>:::no-loc(constexpr):::modyfikacj

Podstawowy zbiór d :::no-loc(if)::: między **`:::no-loc(const):::`** i **`:::no-loc(constexpr):::`** zmienne polega na tym, że inicjalizacja **`:::no-loc(const):::`** zmiennej może zostać odroczona do czasu wykonywania. **`:::no-loc(constexpr):::`** Zmienna musi być inicjowana w czasie kompilacji.  Wszystkie **`:::no-loc(constexpr):::`** zmienne są **`:::no-loc(const):::`** .

- Zmienna może być zadeklarowana przy użyciu **`:::no-loc(constexpr):::`** , gdy ma typ literału i jest inicjowana. Jeśli inicjalizacja jest na :::no-loc(for)::: wartość Med przez :::no-loc(const)::: ructor, :::no-loc(const)::: ructor musi być zadeklarowany jako **`:::no-loc(constexpr):::`** .

- Odwołanie może być zadeklarowane jako, **`:::no-loc(constexpr):::`** gdy oba te warunki są spełnione: obiekt, do którego się odwoływano, jest inicjowany przez :::no-loc(const)::: wyrażenie Ant i wszystkie niejawne konwersje wywoływane podczas inicjowania również są :::no-loc(const)::: wyrażeniami ANT.

- Wszystkie deklaracje **`:::no-loc(constexpr):::`** zmiennej lub funkcji muszą mieć **`:::no-loc(constexpr):::`** specyfikację :::no-loc(if)::: Ier.

```cpp
:::no-loc(constexpr)::: float x = 42.0;
:::no-loc(constexpr)::: float y{108};
:::no-loc(constexpr)::: float z = exp(5, 3);
:::no-loc(constexpr)::: int i; // Error! Not initialized
int j = 0;
:::no-loc(constexpr)::: int k = j + 1; //Error! j not a :::no-loc(const):::ant expression
```

## <a name="no-locconstexpr-functions"></a><a name=":::no-loc(constexpr):::_functions"></a>:::no-loc(constexpr):::funkcje

**`:::no-loc(constexpr):::`** Funkcja jest jedną, której wartością zwracaną jest obliczanej w czasie kompilacji, gdy wymaga użycia kodu. Kod zużywający wymaga wartości zwracanej w czasie kompilacji w celu zainicjowania **`:::no-loc(constexpr):::`** zmiennej lub podania argumentu szablonu, który nie jest typem. Gdy argumenty są **`:::no-loc(constexpr):::`** wartościami, **`:::no-loc(constexpr):::`** Funkcja tworzy ANT w czasie kompilacji :::no-loc(const)::: . Gdy jest wywoływana z **`:::no-loc(constexpr):::`** argumentami innymi niż argumenty lub gdy jej wartość nie jest wymagana w czasie kompilacji, generuje wartość w czasie wykonywania, jak zwykła funkcja. (To podwójne zachowanie umożliwia zapisanie **`:::no-loc(constexpr):::`** i **`:::no-loc(constexpr):::`** niewersja tej samej funkcji).

**`:::no-loc(constexpr):::`** Funkcja lub :::no-loc(const)::: ructor jest niejawnie **`:::no-loc(inline):::`** .

Do funkcji są stosowane następujące reguły :::no-loc(constexpr)::: :

- **`:::no-loc(constexpr):::`** Funkcja musi akceptować i zwracać tylko [typy literałów](trivial-standard-layout-and-pod-types.md#literal_types).

- **`:::no-loc(constexpr):::`** Funkcja może być cykliczna.

- Nie może być [wirtualna](../cpp/virtual-cpp.md). :::no-loc(const):::Nie można zdefiniować elementu ructor, tak jakby **`:::no-loc(constexpr):::`** otaczająca Klasa ma jakiekolwiek wirtualne klasy bazowe.

- Treść można zdefiniować jako `= default` lub `= delete` .

- Treść nie może zawierać żadnych **`:::no-loc(goto):::`** instrukcji ani **`:::no-loc(try):::`** bloków.

- Jawna specjalizacja niebędąca **`:::no-loc(constexpr):::`** szablonem może być zadeklarowana jako **`:::no-loc(constexpr):::`** :

- Jawna specjalizacja **`:::no-loc(constexpr):::`** szablonu nie musi być **`:::no-loc(constexpr):::`** :

Następujące reguły mają zastosowanie do **`:::no-loc(constexpr):::`** funkcji w programie Visual Studio 2017 i nowszych:

- Może zawierać **`:::no-loc(if):::`** i **`:::no-loc(switch):::`** instrukcje oraz wszystkie instrukcje pętli, takie jak, **`:::no-loc(for):::`** oparte na zakresie **`:::no-loc(for):::`** , **`:::no-loc(while):::`** ** :::no-loc(while)::: **, i do.

- Może zawierać deklaracje zmiennych lokalnych, ale zmienna musi być zainicjowana. Musi być typem literału i nie może być **`static`** ani elementem lokalnym wątku. Zmienna zadeklarowana lokalnie nie jest wymagana **`:::no-loc(const):::`** i może ulec mutacji.

- Funkcja niebędąca **`:::no-loc(constexpr):::`** **`static`** członkiem nie musi być niejawnie **`:::no-loc(const):::`** .

```cpp
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> W debugerze programu Visual Studio podczas debugowania niezoptymalizowanej kompilacji debugowania można sprawdzić, czy **`:::no-loc(constexpr):::`** Funkcja jest szacowana w czasie kompilacji, umieszczając w niej punkt przerwania. Po trafieniu punktu przerwania funkcja została wywołana w czasie wykonywania.  Jeśli nie, funkcja została wywołana w czasie kompilacji.

## <a name="extern-no-locconstexpr"></a>modyfikator:::no-loc(constexpr):::

Opcja kompilatora [/Zc: externConstexpr](../build/reference/zc-extern:::no-loc(constexpr):::.md) powoduje, że kompilator zastosuje [zewnętrzne połączenie](../c-language/external-linkage.md) ze zmiennymi zadeklarowanymi przy **użyciu :::no-loc(constexpr)::: extern **. We wcześniejszych wersjach programu Visual Studio, domyślnie lub gdy **/Zc: externConstexpr-** is spec :::no-loc(if)::: IED, program Visual Studio stosuje wewnętrzne połączenie ze **`:::no-loc(constexpr):::`** zmiennymi nawet wtedy, gdy **`extern`** słowo kluczowe jest używane. Opcja **/Zc: externConstexpr** jest dostępna począwszy od programu Visual Studio 2017 Update 15,6 i jest domyślnie wyłączona. Opcja [/permissive-](../build/reference/permissive-standards-con:::no-loc(for):::mance.md) nie włącza **/Zc: externConstexpr**.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia **`:::no-loc(constexpr):::`** zmienne, funkcje i typ zdefiniowany przez użytkownika. W ostatniej instrukcji w `main()` , **`:::no-loc(constexpr):::`** funkcja członkowska `GetValue()` jest wywołaniem w czasie wykonywania, ponieważ wartość nie jest wymagana, aby była znana w czasie kompilacji.

```cpp
// :::no-loc(constexpr):::.cpp
// Compile with: cl /EHsc /W4 :::no-loc(constexpr):::.cpp
#include <iostream>

using namespace std;

// Pass by value
:::no-loc(constexpr)::: float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
:::no-loc(constexpr)::: float exp2(:::no-loc(const)::: float& x, :::no-loc(const)::: int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
:::no-loc(constexpr)::: int length(:::no-loc(const)::: T(&)[N])
{
    return N;
}

// Recursive :::no-loc(constexpr)::: function
:::no-loc(constexpr)::: int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    :::no-loc(constexpr)::: explicit Foo(int i) : _i(i) {}
    :::no-loc(constexpr)::: int GetValue() :::no-loc(const):::
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is :::no-loc(const)::::
    :::no-loc(constexpr)::: Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    :::no-loc(constexpr)::: float x = exp(5, 3);
    :::no-loc(constexpr)::: float y { exp(2, 5) };
    :::no-loc(constexpr)::: int val = foo.GetValue();
    :::no-loc(constexpr)::: int f5 = fac(5);
    :::no-loc(const)::: int nums[] { 1, 2, 3, 4 };
    :::no-loc(const)::: int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Wymagania

Program Visual Studio 2015 lub nowszy.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)\
[:::no-loc(const):::](../cpp/:::no-loc(const):::-cpp.md)
