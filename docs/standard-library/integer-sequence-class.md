---
title: integer_sequence — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: ca923933ac7a401f6a3ef14f821ceb04b844797b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451020"
---
# <a name="integersequence-class"></a>integer_sequence — klasa

Reprezentuje sekwencję całkowitą. Może służyć do wywnioskowania i powiększania pakietów parametrów w typach wariadyczne, takich jak std\<:: krotek T... >, które są przekazane jako argumenty do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*&* \
Typ wartości; musi być typem całkowitym: bool, char, char16_t, char32_t, wchar_t lub z typami całkowitymi ze znakiem lub bez znaku.

*Vals*\
Pakiet parametrów bez typu, który reprezentuje sekwencję wartości typu całkowitego T.

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
|`static size_t size() noexcept`|Liczba elementów w sekwencji.|
|`typedef T value_type`|Typ każdego elementu w sekwencji. Musi być typem całkowitym.|

## <a name="remarks"></a>Uwagi

Pakiet parametrów, który jest przesyłany bezpośrednio do funkcji można rozpakować bez żadnych specjalnych pomocników biblioteki. Gdy pakiet parametrów jest częścią typu, który jest przesyłany do funkcji, i potrzebne są indeksy w celu uzyskania dostępu do elementów, najprostszym sposobem rozpakowania jest `integer_sequence` użycie i powiązane z nim `index_sequence`aliasy `make_integer_sequence` `make_index_sequence`typów,,, i `index_sequence_for`.

## <a name="example"></a>Przykład

Poniższy przykład jest oparty na oryginalnej propozycji [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Pokazuje `integer_sequence` `std::array<T,N>`, jak użyć elementu do `std::tuple` utworzenia z i, jak używać elementu `integer_sequence` , aby uzyskać dostęp do kolekcji elementów członkowskich.

`a2t` W funkcji `index_sequence` jest alias`integer_sequence`oparty na typie całkowitym.`size_t` `make_index_sequence`jest aliasem, który w czasie kompilacji tworzy zero na podstawie `index_sequence` tej samej liczby elementów co tablica, która jest przenoszona przez obiekt wywołujący. `a2t``a2t_` `a[I]...` `I`przekazuje przez wartość do, gdzie wyrażenie rozpakuje, a następnie elementy, do `make_tuple` których są używane, jako pojedyncze argumenty. `index_sequence` Na przykład, jeśli sekwencja zawiera trzy elementy, `make_tuple` to jest wywoływana jako make_tuple (a [0], [1], [2]). Elementy tablicy mogą być oczywiście dowolnego typu.

Funkcja Apply akceptuje funkcję [std:: krotkę](../standard-library/tuple-class.md)i tworzy `integer_sequence` przy użyciu `tuple_size` klasy pomocnika. Należy zauważyć, że [std::d ecay_t](../standard-library/decay-class.md) jest konieczne, ponieważ [tuple_size](../standard-library/tuple-size-class-tuple.md) nie działa z typami referencyjnymi. `apply_` Funkcja rozpakuje składowe krotek i przekazuje je jako osobne argumenty do wywołania funkcji. W tym przykładzie funkcja jest prostym wyrażeniem lambda, które drukuje wartości.

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

Aby utworzyć `index_sequence` pakiet parametrów, należy użyć `index_sequence_for` \<T... >, który jest aliasem `make_index_sequence`dla \<operatora sizeof... (T) >

## <a name="requirements"></a>Wymagania

Nagłówek: \<type_traits\>

Statements: std

## <a name="see-also"></a>Zobacz także

[Wielokropki i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md)
