---
title: '&lt;Atomic&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 07/11/2018
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
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: df0c7ea332cda65aa3621de581eb39419ee9b9d4
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028320"
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

Wykonuje niepodzielna operacja porównania i wymiany.

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

*Atom* wskaźnik do *atomic* obiekt, który przechowuje wartości typu `Ty`.

*EXP* wskaźnik do wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje niepodzielna operacja porównania i wymiany przy użyciu niejawnych `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_strong_explicit —](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit —

Wykonuje *porównanie atomowe i wymianę* operacji.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*EXP* wskaźnik do wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

*Order1* pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentu.

*Order2* drugi `memory_order` argumentu. Wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`, nie może być silniejszy niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

*Niepodzielna operacja porównania i wymiany* porównuje wartość, która jest przechowywana w obiekcie, który jest wskazywany przez *Atom* z wartością, która jest wskazywany przez *Exp*. Jeśli wartości są równe, wartość, która jest przechowywana w obiekcie, który jest wskazywany przez *atom* zostaje zastąpiona opcją `Val` przy użyciu `read-modify-write` operacji i stosowanie pamięci ograniczenia zlecenia, które są określone przez *Order1*. Jeśli wartości nie są równe, operacja zastępuje wartość, która jest wskazywany przez *Exp* z wartością, która jest przechowywana w obiekcie, który jest wskazywany przez *Atom* i stosuje ograniczenia zlecenia pamięci, które są określony przez *Order2*.

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak —

Wykonuje *weak atomic porównania i wymiany* operacji.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*EXP* wskaźnik do wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje *weak atomic porównania i wymiany operacji* ma niejawne `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_weak_explicit —](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit —

Wykonuje *weak atomic porównania i wymiany* operacji.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*EXP* wskaźnik do wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

*Order1* pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentu.

*Order2* drugi `memory_order` argumentu. Wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`, ani nie może być silniejszy niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zarówno silnych i słabych odmian *niepodzielna operacja porównania i wymiany* gwarancji, że nie przechowują nową wartość oczekiwanego i bieżących wartości nie są równe. Silne flavor gwarantuje, że nowa wartość będzie przechowywała oczekiwanego i bieżących wartości są równe. Słabe flavor czasami mogą zwracać **false** bez przechowywania nowej wartości, nawet jeśli bieżące i oczekiwane wartości są równe. Innymi słowy, funkcja zwróci **false**, ale późniejszego zbadania oczekiwanej wartości może ujawnić, że nie została zmieniona i powinny być porównywane jako równe.

## <a name="atomic_exchange"></a>  atomic_exchange

Używa *wartość* Aby zastąpić przechowywaną wartość *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

`atomic_exchange` Funkcja wykonuje `read-modify-write` operacji do programu exchange wartość, która jest przechowywana w *Atom* z *wartość*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit —

Zastępuje przechowywana wartość *Atom* z *wartość*.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

`atomic_exchange_explicit` Funkcja wykonuje `read-modify-write` operacji do programu exchange wartość, która jest przechowywana w *Atom* z *wartość*, w ramach ograniczeń pamięci, które są określone przez  *Kolejność*.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add

Dodaje wartość do istniejącej wartości przechowywanej w `atomic` obiektu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt przechowujący wskaźnik do typu `T`.

*Wartość* wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_add` Funkcja wykonuje `read-modify-write` operacji, aby przeprowadzić Dodawanie niepodzielne *wartość* do wartości przechowywanej w *Atom*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)ograniczenia.

Gdy typ niepodzielny to `atomic_address`, *wartość* ma typ `ptrdiff_t` a operacja traktuje zapisywany wskaźnik `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

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

*Atom* wskaźnik do `atomic` obiekt przechowujący wskaźnik do typu `T`.

*Wartość* wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_add_explicit` Funkcja wykonuje `read-modify-write` operacji, aby przeprowadzić Dodawanie niepodzielne *wartość* do wartości przechowywanej w *Atom*, w ramach [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia które są określone przez `Order`.

Gdy typ niepodzielny to `atomic_address`, `Value` ma typ `ptrdiff_t` a operacja traktuje zapisywany wskaźnik `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

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

Wykonuje bitową operację `and` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_and` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `and` z *wartość* i bieżącą wartość przechowywaną w *Atom*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit —

Wykonuje bitową operację `and` wartości i istniejącej wartości przechowywanej w `atomic` obiektu.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_and_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `and` z *wartość* i bieżącą wartość przechowywaną w *Atom*, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or

Wykonuje bitową operację `or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_or` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `or` z *wartość* i bieżącą wartość przechowywaną w *Atom*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit —

Wykonuje bitową operację `or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_or_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `or` z *wartość* i bieżącą wartość przechowywaną w *Atom*, w ramach [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia określone przez *kolejności*.

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub

Odejmuje wartość z istniejącej wartości przechowywanej w `atomic` obiektu.

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

*Atom* wskaźnik do `atomic` obiekt przechowujący wskaźnik do typu `T`.

*Wartość* wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_sub` Funkcja wykonuje `read-modify-write` operacji, aby przeprowadzić odejmowanie niepodzielne *wartość* z wartości przechowywanej w *Atom*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

Gdy typ niepodzielny to `atomic_address`, *wartość* ma typ `ptrdiff_t` a operacja traktuje zapisywany wskaźnik `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit —

Odejmuje wartość z istniejącej wartości przechowywanej w `atomic` obiektu.

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

*Atom* wskaźnik do `atomic` obiekt przechowujący wskaźnik do typu `T`.

*Wartość* wartości typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_sub_explicit` Funkcja wykonuje `read-modify-write` operacji, aby przeprowadzić odejmowanie niepodzielne *wartość* z wartości przechowywanej w *Atom*, w ramach [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez `Order`.

Gdy typ niepodzielny to `atomic_address`, *wartość* ma typ `ptrdiff_t` a operacja traktuje zapisywany wskaźnik `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

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

Wykonuje bitową operację `exclusive or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_xor` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `exclusive or` z *wartość* i bieżącą wartość przechowywaną w *Atom*przy użyciu `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit —

Wykonuje bitową operację `exclusive or` na wartość i istniejącą wartość, która jest przechowywana w `atomic` obiektu.

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

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

*Wartość* wartości typu `T`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawierana przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

`atomic_fetch_xor_explicit` Funkcja wykonuje `read-modify-write` operację, aby zastąpić przechowywaną wartość *Atom* wartością bitową `exclusive or` z *wartość* i bieżącą wartość przechowywaną w *Atom*, w ramach [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez *kolejności*.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Zestawy **bool** znacznik w [atomic_flag](../standard-library/atomic-flag-structure.md) obiekt **false**, w ramach `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga* wskaźnik do `atomic_flag` obiektu.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Zestawy **bool** znacznik w [atomic_flag](../standard-library/atomic-flag-structure.md) obiekt **false**, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga* wskaźnik do `atomic_flag` obiektu.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Zestawy **bool** znacznik w [atomic_flag](../standard-library/atomic-flag-structure.md) obiekt **true**, zgodnie z ograniczeniami `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga* wskaźnik do `atomic_flag` obiektu.

### <a name="return-value"></a>Wartość zwracana

Początkowa wartość *flagi*.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Zestawy **bool** znacznik w [atomic_flag](../standard-library/atomic-flag-structure.md) obiekt **true**, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga* wskaźnik do `atomic_flag` obiektu.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Początkowa wartość *flagi*.

## <a name="atomic_init"></a>  atomic_init —

Ustawia wartość przechowywaną w `atomic` obiektu.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_init` nie jest operacją niepodzielną. Nie jest metodą o bezpiecznych wątkach.

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free

Określa, czy niepodzielne operacje na `atomic` obiekt są *wolne od blokady*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który przechowuje wartości typu `T`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli niepodzielne operacje na *Atom* są wolne od blokady; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Typ niepodzielny wolne od blokady Jeśli żadne operacje niepodzielne tego typu nie używają blokady. Jeśli ta funkcja zwróci wartość true, typ jest bezpieczny w użyciu w procedurach obsługi sygnału.

## <a name="atomic_load"></a>  atomic_load —

Pobiera wartość przechowywaną w `atomic` obiektu.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w *Atom*.

### <a name="remarks"></a>Uwagi

`atomic_load` niejawnie wykorzystuje `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>  atomic_load_explicit —

Pobiera wartość przechowywaną w `atomic` obiektu, w ramach określonych [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie używaj `memory_order_release` lub `memory_order_acq_rel`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w *Atom*.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence —

Działa jako *horyzont*— która jest elementem synchronizacji pamięci, który wymusza kolejność między operacjami obciążenia/magazynowania — między innymi zaporami wywołującymi wątek wywołujący, które posiadają procedury obsługi sygnału wykonywane w tym samym wątku.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność* pamięci ograniczenie, które określa typ ogrodzenia.

### <a name="remarks"></a>Uwagi

*Kolejności* argument określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenie nie ma znaczenia.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem horyzontalnym.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem horyzontalnym.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem wydania.|
|`memory_order_acq_rel`|Ogrodzenia jest zarówno ogrodzeniem horyzontalnym, jak i ogrodzeniem wydania.|
|`memory_order_seq_cst`|Ogrodzenia jest zarówno ogrodzeniem horyzontalnym, jak i ogrodzeniem wydania i jest sekwencyjnie spójne.|

## <a name="atomic_store"></a>  atomic_store —

Niepodzielne przechowuje wartość w obiekcie niepodzielnym.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* wskaźnik do obiektu niepodzielnego, który zawiera wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje *wartość* w obiekcie, który jest wskazywany przez *Atom*, w ramach `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia.

## <a name="atomic_store_explicit"></a>  atomic_store_explicit —

Niepodzielne przechowuje wartość w obiekcie niepodzielnym.

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

*Atom* wskaźnik do `atomic` obiekt, który zawiera wartości typu `Ty`.

*Wartość* wartości typu `Ty`.

*Kolejność* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie używaj `memory_order_consume`, `memory_order_acquire`, lub `memory_order_acq_rel`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje *wartość* w obiekcie, który jest wskazywany przez *Atom*, w ramach `memory_order` określonej przez *kolejności*.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence —

Działa jako *horyzont*— która jest elementem synchronizacji pamięci, który wymusza kolejność między operacjami obciążenia/magazynowania — bez skojarzonych, niepodzielnych operacji.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność* pamięci ograniczenie, które określa typ ogrodzenia.

### <a name="remarks"></a>Uwagi

*Kolejności* argument określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenie nie ma znaczenia.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem horyzontalnym.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem horyzontalnym.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem wydania.|
|`memory_order_acq_rel`|Ogrodzenia jest zarówno ogrodzeniem horyzontalnym, jak i ogrodzeniem wydania.|
|`memory_order_seq_cst`|Ogrodzenia jest zarówno ogrodzeniem horyzontalnym, jak i ogrodzeniem wydania i jest sekwencyjnie spójne.|

## <a name="kill_dependency"></a>  kill_dependency —

Usuwa zależność.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*ARG* wartości typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana jest *Arg*. Ocena *Arg* nie posiadają zależności do wywołania funkcji. Dzięki pozbyciu się łańcuchem zależności możliwe, funkcja może pozwalać na kompilator, aby wygenerować kod bardziej wydajne.

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
