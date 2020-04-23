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
ms.openlocfilehash: 3de64f7855b5158f1565580d305e2a6eeaf3e76f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031475"
---
# <a name="integer_sequence-class"></a>integer_sequence — klasa

Reprezentuje sekwencję całkowitą. Może służyć do wywniania i rozwijania pakietów parametrów w typach zmiennoczycznych, takich jak std::krotka\<T...>, które są przekazywane jako argumenty do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*T*\
Typ wartości; musi być typem integralnym: bool, char, char16_t, char32_t, wchar_t lub podpisane lub niepodpisane typy całkowite.

*Vals*\
Pakiet parametrów innych niż typ, który reprezentuje sekwencję wartości typu integralnego T.

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
|`static size_t size() noexcept`|Liczba elementów w sekwencji.|
|`typedef T value_type`|Typ każdego elementu w sekwencji. Musi być typem integralnym.|

## <a name="remarks"></a>Uwagi

Pakiet parametrów, który jest przekazywany bezpośrednio do funkcji można rozpakować bez specjalnych pomocników biblioteki. Gdy pakiet parametrów jest częścią typu, który jest przekazywany do funkcji i potrzebne są indeksy, aby uzyskać `integer_sequence` dostęp do elementów, najprostszym sposobem rozpakowania go jest użycie i powiązane z nim aliasy typu `make_integer_sequence` `index_sequence`, , `make_index_sequence`i `index_sequence_for`.

## <a name="example"></a>Przykład

Poniższy przykład jest oparty na pierwotnej propozycji [N3658](https://wg21.link/n3658). Pokazuje, jak użyć `integer_sequence` do `std::tuple` utworzenia `std::array<T,N>`z programu , `integer_sequence` i jak użyć, aby uzyskać na członków krotki.

W `a2t` funkcji an `index_sequence` jest aliasem `integer_sequence` opartym na typie `size_t` integralnym. `make_index_sequence`jest aliasem, który w czasie kompilacji tworzy zero oparte `index_sequence` na tej samej liczbie elementów, jak tablica, która jest przekazywana przez wywołującego. `a2t`przekazuje `index_sequence` wartość według `a2t_` do , `a[I]...` gdzie `I`wyrażenie rozpakowuje , a `make_tuple` następnie elementy są podawane do których zużywa je jako poszczególne argumenty. Na przykład, jeśli sekwencja zawiera `make_tuple` trzy elementy, a następnie jest wywoływana jako make_tuple(a[0], a[1], a[2]). Elementy tablicy same mogą być oczywiście dowolnego typu.

Funkcja apply akceptuje [std::krotka](../standard-library/tuple-class.md)i tworzy `integer_sequence` za pomocą `tuple_size` klasy pomocnika. Należy zauważyć, że [std::decay_t](../standard-library/decay-class.md) jest [konieczne,](../standard-library/tuple-size-class-tuple.md) ponieważ tuple_size nie działa z typami odwołań. Funkcja `apply_` rozpakowuje elementy krotki i przekazuje je jako oddzielne argumenty do wywołania funkcji. W tym przykładzie funkcja jest prostym wyrażeniem lambda, które drukuje wartości.

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

Aby zrobić `index_sequence` dla pakietu parametrów, `index_sequence_for` \<należy użyć T...> który `make_index_sequence` \<jest aliasem dla sizeof... (T)>

## <a name="requirements"></a>Wymagania

Nagłówek: \<type_traits\>

Namepace: std

## <a name="see-also"></a>Zobacz też

[Szablony wielokropek i variadic](../cpp/ellipses-and-variadic-templates.md)
