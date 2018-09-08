---
title: integer_sequence, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 909bcb8446c7d876828a6d020cd20a7398ec04d5
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108749"
---
# <a name="integersequence-class"></a>integer_sequence — klasa

Reprezentuje sekwencję liczby całkowitej. Może służyć do wywnioskować, a następnie rozwiń węzeł pakietów parametrów w typach ze zmienną liczbą argumentów, takich jak std::tuple\<T... > przekazywane jako argumenty do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ wartości. musi być typu całkowitego: bool, char, char16_t, char32_t, wchar_t, lub podpisane lub niepodpisane typy liczb całkowitych.

*Cyklicznych*<br/>
Pakiet parametru bez typu, który reprezentuje sekwencję liczb całkowitych typu T.

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
|`static size_t size() noexcept`|Liczba elementów w sekwencji.|
|value_type — TypeDef T|Typ każdego elementu w sekwencji. Musi być typu całkowitego.|

## <a name="remarks"></a>Uwagi

Pakiet parametrów, która jest przekazywana bezpośrednio do funkcji może być nierozpakowane bez żadnych specjalnych biblioteki pomocników. Gdy pakiet parametrów jest częścią typu, który jest przekazywany do funkcji, i potrzebujesz indeksów w celu uzyskania dostępu do elementów, a następnie Najprostszym sposobem rozpakowania go jest użycie `integer_sequence` i jego aliasy powiązanego typu `make_integer_sequence`, `index_sequence`, `make_index_sequence`i `index_sequence_for`.

## <a name="example"></a>Przykład

Poniższy przykład jest oparty na oryginalnym propozycji [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Pokazuje, jak używać `integer_sequence` utworzyć `std::tuple` z `std::array<T,N>`i sposobu używania `integer_sequence` można pobrać w spójnej kolekcji elementów członkowskich.

W `a2t` funkcji `index_sequence` jest aliasem `integer_sequence` na podstawie `size_t` typu całkowitego. `make_index_sequence` jest to w czasie kompilacji tworzy liczony od zera `index_sequence` z taką samą liczbę elementów, co tablica, który jest przekazywany przez obiekt wywołujący. `a2t` przekazuje `index_sequence` przez wartość `a2t_` , gdzie wyrażenie `a[I]...` wypakowuje `I`, a następnie elementy są są podawane w taki sposób, aby `make_tuple` co zużywa je jako oddzielne argumenty. Na przykład, jeśli sekwencja zawiera trzy elementy, następnie `make_tuple` jest wywoływana jako make_tuple — ([0], [1], a[2]). Elementy tablicy, samodzielnie kursu mogą być dowolnego typu.

Funkcja Zastosuj akceptuje [std::tuple](../standard-library/tuple-class.md)i tworzy integer_sequence przy użyciu `tuple_size` Klasa pomocy. Należy pamiętać, że [std::decay_t](../standard-library/decay-class.md)_is niezbędne ponieważ [tuple_size —](../standard-library/tuple-size-class-tuple.md) nie działa w przypadku typów referencyjnych. `apply_` Funkcji wypakowuje spójnej kolekcji elementów członkowskich i przekazuje je jako oddzielne argumenty do wywołania funkcji. W tym przykładzie funkcja jest wyrażenie lambda prostą, która wyświetla wartości.

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

Zapewnienie `index_sequence` pakiet parametrów można używać `index_sequence_for` \<T... > co jest aliasem `make_index_sequence` \<sizeof... [T] >

## <a name="requirements"></a>Wymagania

Nagłówek: \<type_traits\>

Przestrzeń nazw: standardowe

## <a name="see-also"></a>Zobacz także

[Wielokropki i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md)<br/>
