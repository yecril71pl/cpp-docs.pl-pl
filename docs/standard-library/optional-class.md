---
title: Klasa opcjonalna
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: f664df6493a7ee20361d49531a930aeb810d3d2a
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957147"
---
# <a name="optional-class"></a>Klasa opcjonalna

Klasa `optional<T>` szablonu opisuje obiekt, który może lub nie może zawierać wartości typu `T`, znanej jako *wartość zawartej*.

Gdy wystąpienie `optional<T>` zawiera wartość, zawartej wartości jest przypisywany w ramach magazynu `optional` obiektu, w regionie odpowiednio wyrównanym do typu `T`. Gdy jest konwertowany na `bool`, wynikiem jest `true` Jeśli obiekt `false`zawiera wartość; w przeciwnym razie jest to. `optional<T>`

Typ `T` zawartego obiektu nie może być [in_place_t](in-place-t-struct.md) ani [nullopt_t](nullopt-t-structure.md). `T`musi być *zniszczalnych*, czyli destruktor musi odwoływać wszystkie posiadane zasoby i może zgłosić brak wyjątków.

`optional` Klasa jest nowa w języku c++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
| **Konstruktory i destruktor** | |
|[optional](#optional) | Konstruuje obiekt typu `optional`. |
|[~ opcjonalne](#optional-destructor) | Niszczy obiekt typu `optional`. |
| **Przypisanie** | |
| [operator=](#op_eq) | Zastępuje kopię inną `optional`. `optional` |
| [emplace](#op_eq) | Inicjuje zawartej wartości z określonymi argumentami. |
| **Wymiany** | |
| [swap](#swap) | Zamienia zawarty w niej wartość lub pusty stan na inny `optional`. |
| **Obserwatorów** | |
| [has_value](#has_value) | Zwraca czy `optional` obiekt zawiera wartość. |
| [value](#value) | Zwraca zawartej wartości. |
| [value_or](#value_or) | Zwraca wartość zawartej lub alternatywę, jeśli żadna wartość nie jest obecna. |
| [operator — >](#op_as) | Odwołuje się do zawartej `optional` wartości obiektu. |
| [zakład](#op_mem) | Odwołuje się do zawartej `optional` wartości obiektu. |
| [wartość logiczna operatora](#op_bool) | Zwraca czy `optional` obiekt zawiera wartość. |
| **Modyfikatory** | |
| [zresetować](#reset) | Resetuje `optional` przez zniszczenie dowolnej zawartej wartości. |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>Konstruktor opcjonalny

Konstruuje obiekt typu `optional`.

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>Parametry

*RHS*\
`optional` Do kopiowania lub przenoszenia konstruowania zawartej wartości z.

*i_list*\
Lista inicjatorów do konstruowania zawartej wartości z.

*argumentów*\
Lista argumentów do konstruowania zawartej wartości z.

### <a name="remarks"></a>Uwagi

`constexpr optional() noexcept;`
`constexpr optional(nullopt_t nullopt) noexcept;`Konstruktory te konstruują `optional` , która nie zawiera wartości.

`constexpr optional(const optional& rhs);`Konstruktor kopiujący inicjuje zawartej wartości z wartości zawartej w argumencie. Jest ono zdefiniowane jako **usunięte** , `is_copy_constructible_v<T>` chyba że ma wartość true i jest proste `is_trivially_copy_constructible_v<T>` , jeśli ma wartość true.

`constexpr optional(optional&& rhs) noexcept;`Konstruktor przenoszący inicjuje zawartą wartość poprzez przechodzenie z zawartej wartości argumentu. Nie uczestniczy w rozpoznawaniu przeciążenia `is_move_constructible_v<T>` , chyba że ma wartość true i jest `is_trivially_move_constructible_v<T>` proste, jeśli ma wartość true.

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);`Bezpośrednie inicjowanie zawartej wartości tak, jakby przy użyciu `std::forward<Args>(args)`argumentów. Ten konstruktor jest `constexpr` , `T` Jeśli używany jest `constexpr`Konstruktor. Nie uczestniczy w rozpoznawaniu przeciążenia `is_constructible_v<T, Args...>` , chyba że ma wartość true.

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);`Bezpośrednie inicjowanie zawartej wartości tak, jakby przy użyciu `i_list, std::forward<Args>(args)`argumentów. Ten konstruktor jest `constexpr` , `T` Jeśli używany jest `constexpr`Konstruktor. Nie uczestniczy w rozpoznawaniu przeciążenia `is_constructible_v<T, initializer_list<U>&, Args&&...>` , chyba że ma wartość true.

`template <class U = T> explicit constexpr optional(U&& rhs);`Bezpośrednie inicjowanie zawartej wartości w przypadku użycia `std::forward<U>(v)`. Ten konstruktor jest `constexpr` , `T` Jeśli używany jest `constexpr`Konstruktor. Nie uczestniczy w rozpoznawaniu przeciążenia `is_constructible_v<T, U&&>` , chyba że jest `is_same_v<remove_cvref_t<U>, in_place_t>` spełniony `is_same_v<remove_cvref_t<U>, optional>` i i ma wartość false.

`template <class U> explicit optional(const optional<U>& rhs);`Jeśli *RHS* zawiera wartość, bezpośrednie inicjuje zawartej wartości z zawartej wartości argumentu. Nie uczestniczy w rozpoznawaniu przeciążenia `is_constructible_v<T, const U&>` , chyba że ma wartość `is_constructible_v<T, optional<U>&&>`true, i `is_convertible_v<optional<U>&, T>` `is_constructible_v<T, optional<U>&>` `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>`,,, `is_convertible_v<const optional<U>&&, T>` ,, i to wszystkie wartości false.

`template <class U> explicit optional(optional<U>&& rhs);`Jeśli *RHS* zawiera wartość, bezpośrednie inicjuje wartość zawartej w, jeśli jest `std::move(*rhs)`używana. Nie uczestniczy w rozpoznawaniu przeciążenia `is_constructible_v<T, U&&>` , chyba że ma wartość `is_constructible_v<T, optional<U>&&>`true, i `is_convertible_v<optional<U>&, T>` `is_constructible_v<T, optional<U>&>` `is_convertible_v<optional<U>&&, T>`, `is_convertible_v<const optional<U>&, T>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>`,,, `is_convertible_v<const optional<U>&&, T>` ,, i to wszystkie wartości false.

## <a name="optional-destructor"></a>~ opcjonalny destruktor

Niszczy jakąkolwiek niezniszczalnychą wartość, jeśli jest obecna, przez wywołanie jej destruktora.

```cpp
~optional();
```

### <a name="remarks"></a>Uwagi

Jeśli `T` jest bardzo zniszczalnych `optional<T>` , to również zniszczalnych.

## <a name="op_eq"></a>operator =

Zamienia zawartej wartości elementu `optional` z kopią lub przenosi z innej `optional` zawartej wartości.

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>operator — >

Odwołuje się do zawartej wartości `optional` obiektu.

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>zakład

Odwołuje się do zawartej wartości `optional` obiektu.

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>wartość logiczna operatora

Informuje, `optional` czy obiekt ma zawartą wartość.

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>zresetować

Efektywnie wywołuje destruktor zawartego obiektu, jeśli istnieje, i ustawia go na stanie niezainicjowanym.

```cpp
void reset() noexcept;
```

## <a name="swap"></a>wymiany

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>wartościami

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>Zobacz także

[\<> opcjonalne](optional.md)
