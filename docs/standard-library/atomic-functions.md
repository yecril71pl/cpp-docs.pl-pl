---
title: '&lt;Atomic&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: 5239cd975ef5a62fb63406865f457d6d1b1a86f2
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltatomicgt-functions"></a>&lt;Atomic&gt; funkcji

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load —](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong —

Wykonuje operację atomic porównania i exchange.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Exp` Wskaźnik do wartości typu `Ty`.

`Value` Wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

A `bool` wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje operacją niepodzielną porównania i programem exchange za pomocą niejawne `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_strong_explicit —](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit —

Wykonuje *atomic porównania i exchange* operacji.

```cpp
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Exp` Wskaźnik do wartości typu `Ty`.

`Value` Wartości typu `Ty`.

`Order1` Pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentu.

`Order2` Drugi `memory_order` argumentu. Wartość `Order2` nie może być `memory_order_release` lub `memory_order_acq_rel`, nie może być mocniejszy niż wartość `Order1`.

### <a name="return-value"></a>Wartość zwracana

A `bool` wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

*Atomic operacji porównywania i exchange* porównuje wartości przechowywanej w obiekcie, który jest wskazywana przez `Atom` wartość, która jest wskazywana przez `Exp`. Jeśli wartości są równe, wartość, która jest przechowywana w obiekcie, który jest wskazywana przez `atom` jest zastępowany `Val` za pomocą `read-modify-write` operacji i stosowania pamięć kolejność ograniczenia, które są określone przez `Order1`. Jeśli wartości nie są takie same, operacja zastąpi wartość, która jest wskazywana przez `Exp` o wartości przechowywanej w obiekcie, który jest wskazywana przez `Atom` i stosuje ograniczenia kolejności pamięci, które są określone przez `Order2`.

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak —

Wykonuje *weak atomic porównania i exchange* operacji.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Exp` Wskaźnik do wartości typu `Ty`.

`Value` Wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

A `bool` wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje *weak atomic porównania i operacji wymiana* ma niejawne `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_weak_explicit —](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit —

Wykonuje *weak atomic porównania i exchange* operacji.

```cpp
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Exp` Wskaźnik do wartości typu `Ty`.

`Value` Wartości typu `Ty`.

`Order1` Pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentu.

`Order2` Drugi `memory_order` argumentu. Wartość `Order2` nie może być `memory_order_release` lub `memory_order_acq_rel`, ani nie może być mocniejszy niż wartość `Order1`.

### <a name="return-value"></a>Wartość zwracana

A `bool` wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

*Atomic operacji porównywania i exchange* porównuje wartości przechowywanej w obiekcie, który jest wskazywana przez `Atom` z wartością, która jest wskazywana przez `Exp`. Jeśli wartości są równe, operacja zastąpi wartość, która jest przechowywana w obiekcie, który jest wskazywana przez `Atom` z `Val` za pomocą `read-modify-write` operacji i zastosowania ograniczeń kolejności pamięci, które są określone przez `Order1`. Jeśli wartości nie są takie same, operacja zastąpi wartość, która jest wskazywana przez `Exp` o wartości przechowywanej w obiekcie, który jest wskazywana przez `Atom` i stosuje ograniczenia kolejności pamięci, które są określone przez `Order2`.

A *słabe* niepodzielną operację porównania i exchange wykonuje exchange porównaniu wartości są równe. Jednak jeśli wartości nie są takie same, operacja nie jest gwarantowana do wykonania programu exchange.

## <a name="atomic_exchange"></a>  atomic_exchange

Używa `Value` zastąpić przechowywana wartość `Atom`.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Value` Wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość `Atom` przed programu exchange.

### <a name="remarks"></a>Uwagi

`atomic_exchange` Funkcja wykonuje `read-modify-write` operacji wymiana wartość, która jest przechowywana w `Atom` z `Value`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit —

Zastępuje przechowywana wartość `Atom` z `Value`.

```cpp
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Value` Wartości typu `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość `Atom` przed programu exchange.

### <a name="remarks"></a>Uwagi

`atomic_exchange_explicit` Funkcja wykonuje `read-modify-write` operacji wymiana wartość, która jest przechowywana w `Atom` z `Value`, w ramach ograniczeń pamięci, które są określone przez `Order`.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Dodaje wartość do istniejącej wartości przechowywanej w `atomic` obiektu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który przechowuje wskaźnika do typu `T`.

`Value` Wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_add` Funkcja wykonuje `read-modify-write` operacji dodawania atomowo `Value` do wartości przechowywanej w `Atom`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

Gdy typem atomic jest `atomic_address`, `Value` ma typ `ptrdiff_t` i operacji traktuje wskaźnika przechowywane jako `char *`.

Ta operacja jest przeciążony również w przypadku typów całkowitych:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>  atomic_fetch_add_explicit —

Dodaje wartość do istniejącej wartości przechowywanej w `atomic` obiektu.

```cpp
template <class T>
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który przechowuje wskaźnika do typu `T`.

`Value` Wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_add_explicit` Funkcja wykonuje `read-modify-write` operacji dodawania atomowo `Value` do wartości przechowywanej w `Atom`, w [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez `Order`.

Gdy typem atomic jest `atomic_address`, `Value` ma typ `ptrdiff_t` i operacji traktuje wskaźnika przechowywane jako `char *`.

Ta operacja jest przeciążony również w przypadku typów całkowitych:

```cpp
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_and"></a>  atomic_fetch_and

Wykonuje bitowej `and` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_and` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `and` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit —

Wykonuje bitowej `and` wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_and_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `and` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`, w ramach ograniczeń pamięci, które są określony przez `Order`.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Wykonuje bitowej `or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_or` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `or` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit —

Wykonuje bitowej `or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_or_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `or` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`, poziomu [memory_ kolejność](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia określony przez `Order`.

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub

Odejmuje wartość z zakresu od istniejącej wartości przechowywanej w `atomic` obiektu.

```cpp
template <class T>
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który przechowuje wskaźnika do typu `T`.

`Value` Wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_sub` Funkcja wykonuje `read-modify-write` operacji do odjęcia atomowo `Value` z wartością przechowywaną w `Atom`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

Gdy typem atomic jest `atomic_address`, `Value` ma typ `ptrdiff_t` i operacji traktuje wskaźnika przechowywane jako `char *`.

Ta operacja jest przeciążony również w przypadku typów całkowitych:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit —

Odejmuje wartość z zakresu od istniejącej wartości przechowywanej w `atomic` obiektu.

```cpp
template <class T>
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który przechowuje wskaźnika do typu `T`.

`Value` Wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_sub_explicit` Funkcja wykonuje `read-modify-write` operacji do odjęcia atomowo `Value` z wartością przechowywaną w `Atom`, poziomu [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez `Order`.

Gdy typem atomic jest `atomic_address`, `Value` ma typ `ptrdiff_t` i operacji traktuje wskaźnika przechowywane jako `char *`.

Ta operacja jest przeciążony również w przypadku typów całkowitych:

```cpp
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```

## <a name="atomic_fetch_xor"></a>  atomic_fetch_xor

Wykonuje bitowej `exclusive or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_xor` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `exclusive or` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`za pomocą `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit —

Wykonuje bitowej `exclusive or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;

template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

`Value` Wartości typu `T`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawartymi w obiekcie atomic bezpośrednio przed operacja została wykonana.

### <a name="remarks"></a>Uwagi

`atomic_fetch_xor_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywana wartość `Atom` z bitowego `exclusive or` z `Value` i bieżąca wartość, która jest przechowywana w `Atom`, poziomu [memory_ kolejność](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez `Order`.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear —

Ustawia `bool` oflagowane w [atomic_flag —](../standard-library/atomic-flag-structure.md) do obiektu `false`, poziomu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

`Flag` Wskaźnik do `atomic_flag` obiektu.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit —

Ustawia `bool` oflagowane w [atomic_flag —](../standard-library/atomic-flag-structure.md) do obiektu `false`, w ramach określonego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Flag` Wskaźnik do `atomic_flag` obiektu.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set —

Ustawia `bool` oflagowane w [atomic_flag —](../standard-library/atomic-flag-structure.md) do obiektu `true`, zgodnie z ograniczeniami `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

`Flag` Wskaźnik do `atomic_flag` obiektu.

### <a name="return-value"></a>Wartość zwracana

Początkowa wartość `Flag`.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Ustawia `bool` oflagowane w [atomic_flag —](../standard-library/atomic-flag-structure.md) do obiektu `true`, w ramach określonego [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Flag` Wskaźnik do `atomic_flag` obiektu.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Początkowa wartość `Flag`.

## <a name="atomic_init"></a>  atomic_init —

Ustawia wartość przechowywana w `atomic` obiektu.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `Ty`.

`Value` Wartości typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_init` nie jest niepodzielną operację. Nie jest bezpieczne wątkowo.

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free

Określa, czy niepodzielne operacje na `atomic` obiektu są *zwolnić blokady*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt zawierający wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli operacjach niepodzielnych na `Atom` zwolnić blokady; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Jest typem niepodzielnym blokady zwolnienia blokad użycie żadne niepodzielne operacje tego typu. Ta funkcja zwraca wartość true, ten typ nie jest bezpiecznie korzystać w obsłudze sygnału.

## <a name="atomic_load"></a>  atomic_load —

Pobiera wartość przechowywanych w `atomic` obiektu.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w `Atom`.

### <a name="remarks"></a>Uwagi

`atomic_load` niejawnie wykorzystuje `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>  atomic_load_explicit —

Pobiera wartość przechowywanych w `atomic` obiektu, w ramach określonej [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie używaj `memory_order_release` lub `memory_order_acq_rel`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w `Atom`.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence —

Zachowuje się jak *ogrodzenia*— czyli prymitywu synchronizacji pamięci, który wymusza kolejności między operacjami Załaduj/Przechowaj — między innymi ogrodzenia w wątku wywołującym mających obsługi sygnału, które są wykonywane w tym samym wątku.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Order` Pamięci, kolejność ograniczenie, które określa typ ogranicznika.

### <a name="remarks"></a>Uwagi

`Order` Argument określa typ ogranicznika.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenia nie ma znaczenia.|
|`memory_order_consume`|Ogrodzenia jest ogranicznika pobierania.|
|`memory_order_acquire`|Ogrodzenia jest ogranicznika pobierania.|
|`memory_order_release`|Ogrodzenia jest ogranicznika wersji.|
|`memory_order_acq_rel`|Ogrodzenia jest ogranicznika pobierania i ogranicznika wersji.|
|`memory_order_seq_cst`|Ogrodzenia jest ogranicznika pobierania i ogranicznika wersji i jest spójna sekwencyjnie.|

## <a name="atomic_store"></a>  atomic_store —

Automatycznie zapisuje wartość w obiekcie atomic.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do obiektu atomic, który zawiera wartości typu `Ty`.

`Value` Wartości typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje `Value` w obiekcie, który jest wskazywana przez `Atom`, poziomu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

## <a name="atomic_store_explicit"></a>  atomic_store_explicit —

Automatycznie zapisuje wartość w obiekcie atomic.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom,
    T Value,
    memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Atom` Wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

`Value` Wartości typu `Ty`.

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie używaj `memory_order_consume`, `memory_order_acquire`, lub `memory_order_acq_rel`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje `Value` w obiekcie, który jest wskazywana przez `Atom`, poziomu `memory_order` określonym przez `Order`.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence —

Zachowuje się jak *ogrodzenia*— czyli prymitywu synchronizacji pamięci, który wymusza kolejności między operacjami Załaduj/Przechowaj — bez skojarzone niepodzielną operację.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

`Order` Pamięci, kolejność ograniczenie, które określa typ ogranicznika.

### <a name="remarks"></a>Uwagi

`Order` Argument określa typ ogranicznika.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenia nie ma znaczenia.|
|`memory_order_consume`|Ogrodzenia jest ogranicznika pobierania.|
|`memory_order_acquire`|Ogrodzenia jest ogranicznika pobierania.|
|`memory_order_release`|Ogrodzenia jest ogranicznika wersji.|
|`memory_order_acq_rel`|Ogrodzenia jest ogranicznika pobierania i ogranicznika wersji.|
|`memory_order_seq_cst`|Ogrodzenia jest ogranicznika pobierania i ogranicznika wersji i jest spójna sekwencyjnie.|

## <a name="kill_dependency"></a>  kill_dependency —

Usuwa zależność.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

`Arg` Wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest `Arg`. Ocena `Arg` nie zawiera zależności do wywołania funkcji. Dzięki pozbyciu się łańcuch zależności możliwe, funkcja może pozwalać na kompilator, aby wygenerować bardziej wydajne kodu.

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
