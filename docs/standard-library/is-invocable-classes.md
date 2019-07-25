---
title: is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r, klasy
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 20fec55fc3ad1924ee85db3b2f78812e4847f447
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456233"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r, klasy

Te szablony określają, czy typ można wywołać z określonymi typami argumentów. `is_invocable_r`a `is_nothrow_invocable_r` także określić, czy wynik wywołania jest konwertowany do określonego typu. `is_nothrow_invocable`a `is_nothrow_invocable_r` także określić, czy wywołanie jest znane, aby nie zgłaszać wyjątków. Dodano w języku C++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>Parametry

*Żądanie*\
Typ możliwy do zapytania.

*Argumentów*\
Typy argumentów do zapytania.

*Dach*\
Typ wyniku możliwego do *zażądanie* musi być konwertowany na.

## <a name="remarks"></a>Uwagi

Predykat typu ma wartość true, jeśli możliwy do wywołania typ wywołujący *może być* wywoływany przy użyciu argumentów *argumenty w* nieoszacowanym kontekście. `is_invocable`

Predykat typu ma wartość true, jeśli możliwy do *wywołania typ można* wywołać za pomocą argumentów *argumenty w* nieoszacowanym kontekście, aby utworzyć konwersję typu wynik do *konwersji.* `is_invocable_r`

Predykat typu ma wartość true, jeśli możliwy do *wywołania typ można* wywołać przy użyciu argumentów *argumenty w* nieoszacowanym kontekście i że takie wywołanie jest znane, aby nie zgłosić wyjątku. `is_nothrow_invocable`

Predykat typu ma wartość true, jeśli możliwy do wywołania typ wywołujący *może być* wywoływany przy użyciu *argumentów arguments* w nieoszacowanym kontekście, aby utworzyć konwersję typu wyniku do konwersji, i że takie wywołanie jest znane.  `is_nothrow_invocable_r` wyjątek.

Każdy typ, który można *przekonwertować*, *wywołać*i typy w parametrach *pakietu parametrów* , musi być kompletnym typem, tablicą nieznanej granicy lub prawdopodobnie **void**kwalifikowaną. W przeciwnym razie zachowanie predykatu jest niezdefiniowane.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value ); 
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[wywołuje](functional-functions.md#invoke)
