---
title: integer_sequence — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
dev_langs:
- C++
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58700d1f52189afb1d8baf3456bac4ed84920fab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="integersequence-class"></a>integer_sequence — klasa

Reprezentuje sekwencji liczby całkowitej. Można wywnioskować i rozwiń listę pakietów parametrów w typach ze zmienną liczbą argumentów, takich jak std::tuple\<T... > przekazywane jako argumenty do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

T typu wartości. musi być typem całkowitym: bool, char, char16_t, char32_t, wchar_t, podpisane lub niepodpisanych typów całkowitych.

Cyklicznych A stała parametryzująca pakietu, który reprezentuje sekwencję wartości typu całkowitego T.

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
|`static size_t size() noexcept`|Liczba elementów w sekwencji.|
|value_type — TypeDef T|Typ każdego elementu w sekwencji. Musi być typem całkowitym.|

## <a name="remarks"></a>Uwagi

Pakiet parametrów przesyłanych bezpośrednio do funkcji można rozpakować bez żadnych specjalnych Biblioteka pomocników. Gdy pakiet parametrów jest częścią typu, który jest przekazywany do funkcji, i należy indeksów w celu uzyskania dostępu do elementów, a następnie jest najprostszym sposobem rozpakowania go do użycia `integer_sequence` i jego aliasy powiązanego typu `make_integer_sequence`, `index_sequence`, `make_index_sequence`i `index_sequence_for`.

## <a name="example"></a>Przykład

Poniższy przykład jest oparty na oryginalnym propozycji [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Przedstawiono użycie `integer_sequence` utworzyć `std::tuple` z `std::array<T,N>`i sposobu użycia `integer_sequence` można uzyskać w spójnej kolekcji elementów członkowskich.

W `a2t` funkcji `index_sequence` jest aliasem `integer_sequence` na podstawie `size_t` typ całkowity. `make_index_sequence` jest to w czasie kompilacji tworzy liczony od zera `index_sequence` z taką samą liczbę elementów co tablica, która jest przekazany przez wywołującego. `a2t` przekazuje `index_sequence` przez wartość `a2t_` , gdzie wyrażenie `a[I]...` wypakowuje `I`, a następnie elementy są zasilana do `make_tuple` co zużywa je jako oddzielne argumenty. Na przykład, jeśli sekwencja zawiera trzy elementy, następnie `make_tuple` nosi nazwę jako make_tuple — ([0], [1], a[2]). Elementy tablicy, same oczywiście mogą być dowolnego typu.

Funkcja Zastosuj akceptuje [std::tuple](../standard-library/tuple-class.md)i tworzy integer_sequence — za pomocą `tuple_size` Klasa pomocy. Należy pamiętać, że [std::decay_t](../standard-library/decay-class.md)_is niezbędne ponieważ [tuple_size —](../standard-library/tuple-size-class-tuple.md) nie działa z typy referencyjne. `apply_` Funkcji wypakowuje spójnej kolekcji elementów członkowskich i przekazuje je jako osobne argumentów dla wywołania funkcji. W tym przykładzie funkcja jest drukowany wartości wyrażenia lambda proste.

```

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

Aby `index_sequence` pakiet parametrów można używać `index_sequence_for` \<T... > czyli aliasu dla `make_index_sequence` \<sizeof... [T] >

## <a name="requirements"></a>Wymagania

Nagłówek: < type_traits >

Zaimportowane: Standard

## <a name="see-also"></a>Zobacz także

[Wielokropki i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md)<br/>
