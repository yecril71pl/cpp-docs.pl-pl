---
title: is_invocable, is_invocable_r, is_nothrow_invocable is_nothrow_invocable_r klas
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
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336234"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable, is_invocable_r, is_nothrow_invocable is_nothrow_invocable_r klas

Szablony te określają, jeśli typ może być wywoływana ze określone typy argumentów. `is_invocable_r` i `is_nothrow_invocable_r` również określić, czy wynik wywołania jest konwertowany na określonego typu. `is_nothrow_invocable` i `is_nothrow_invocable_r` określają również, jeśli wywołanie znanego nie zgłasza wyjątków. Dodane w języku C ++ 17.

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

*Możliwy do wywołania*<br/>
Wywoływane typ do zapytania.

*Args*<br/>
Typy argumentów do wykonywania zapytań.

*Przekonwertować*<br/>
Typ wyniku z *Callable* musi być konwertowany na.

## <a name="remarks"></a>Uwagi

`is_invocable` Typu predykatu ma wartość true, jeśli typ możliwy do wywołania *Callable* może być wywoływany przy użyciu argumentów *Args* w nieznanym kontekście.

`is_invocable_r` Typu predykatu ma wartość true, jeśli typ możliwy do wywołania *Callable* może być wywoływany przy użyciu argumentów *Args* w nieobliczonym kontekście w celu utworzenia wyniku można przekonwertować na typ  *Przekonwertować*.

`is_nothrow_invocable` Typu predykatu ma wartość true, jeśli typ możliwy do wywołania *Callable* może być wywoływany przy użyciu argumentów *Args* w nieznanym kontekście, który takie wywołanie jest znana nie zgłasza wyjątku.

`is_nothrow_invocable_r` Typu predykatu ma wartość true, jeśli typ możliwy do wywołania *Callable* może być wywoływany przy użyciu argumentów *Args* w nieobliczonym kontekście w celu utworzenia wyniku można przekonwertować na typ  *Przekonwertować*, że takie wywołanie wiadomo, że nie można zgłosić wyjątek.

Każdy z typów *przekonwertować*, *Callable*i typy w pakiecie parametr *Args* musi być typem kompletnym, tablicę powiązane z nieznanego lub prawdopodobniekwalifikowanacv**void**. W przeciwnym razie zachowanie predykatu jest niezdefiniowane.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[wywołania](functional-functions.md#invoke)<br/>
