---
title: '&lt;funkcje atomowe&gt;'
ms.date: 07/11/2018
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
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376897"
---
# <a name="ltatomicgt-functions"></a>&lt;funkcje atomowe&gt;

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

Wykonuje atomowej operacji porównania i wymiany.

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

*Atom*\
Wskaźnik do obiektu *atomowego,* który `Ty`przechowuje wartość typu .

*Exp*\
Wskaźnik do wartości typu `Ty`.

*Wartość*\
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje niepodzielną operację porównania `memory_order_seq_cst`i wymiany przy użyciu argumentów [memory_order](../standard-library/atomic-enums.md#memory_order_enum) niejawnych. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Wykonuje atomowej *operacji porównania i wymiany.*

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Exp*\
Wskaźnik do wartości typu `Ty`.

*Wartość*\
Wartość typu `Ty`.

*Zamówienie1*\
Pierwszy [argument memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

*Order2*\
Drugi `memory_order` argument. Wartość *Order2* nie `memory_order_release` może `memory_order_acq_rel`być lub , nie może być silniejsza niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

*Atomowej operacji porównania i wymiany* porównuje wartość, która jest przechowywana w obiekcie, który jest wskazywał przez *Atom* względem wartości, która jest wskazywalna przez *Exp*. Jeśli wartości są równe, wartość, która jest przechowywana w obiekcie, który jest `read-modify-write` wskazywał przez *atom,* jest zastępowana *wartością* za pomocą operacji i stosowania ograniczeń kolejności pamięci określonych przez *Order1*. Jeśli wartości nie są równe, operacja zastępuje wartość wskazywalną przez *Exp* wartością przechowywaną w obiekcie, który jest wskazywał *atom* i stosuje ograniczenia kolejności pamięci określone przez *Order2*.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

Wykonuje *słabe atomowej porównania i wymiany* operacji.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Exp*\
Wskaźnik do wartości typu `Ty`.

*Wartość*\
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje *słabe atomic compare i exchange operacji,* która ma niejawne `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

Wykonuje *słabe atomowej porównania i wymiany* operacji.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Exp*\
Wskaźnik do wartości typu `Ty`.

*Wartość*\
Wartość typu `Ty`.

*Zamówienie1*\
Pierwszy [argument memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

*Order2*\
Drugi `memory_order` argument. Wartość *Order2* nie `memory_order_release` może `memory_order_acq_rel`być ani , ani nie może być silniejsza niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zarówno silne i słabe smaki *atomic compare i exchange operacji* gwarancji, że nie przechowują nową wartość, jeśli oczekiwane i bieżące wartości nie są równe. Silny smak gwarantuje, że będzie przechowywać nową wartość, jeśli wartości oczekiwane i bieżące są równe. Słaby smak może czasami zwracać **false** i nie przechowywać nową wartość, nawet jeśli bieżące i oczekiwane wartości są równe. Innymi słowy funkcja zwróci **false**, ale późniejsze badanie oczekiwanej wartości może ujawnić, że nie zmieniła się i dlatego powinna być porównana jako równa.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Używa *wartości,* aby zastąpić przechowywaną wartość *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Wartość*\
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_exchange` `read-modify-write` wykonuje operację w celu wymiany wartości przechowywanej w *Atom* z *Wartością* `memory_order_seq_cst`, używając [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Zastępuje zapisaną wartość *Atom* *wartością*.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Wartość*\
Wartość typu `Ty`.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_exchange_explicit` `read-modify-write` wykonuje operację w celu wymiany wartości przechowywanej w *Atom* z *Wartością,* w ramach ograniczeń pamięci określonych przez *Kolejność*.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Dodaje wartość do istniejącej wartości, `atomic` która jest przechowywana w obiekcie.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wskaźnik do wpisywalnego .

*Wartość*\
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartego przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_add` wykonuje `read-modify-write` operację, aby niepodzielnie dodać *wartość* do przechowywanej wartości w *Atom*, przy użyciu `memory_order_seq_cst`ograniczenia [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Gdy typem `atomic_address`niepodzielnym jest *, Wartość* ma typ `ptrdiff_t` `char *`i operacja traktuje przechowywany wskaźnik jako .

Ta operacja jest również przeciążona dla typów całkowitych:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

Dodaje wartość do istniejącej wartości, `atomic` która jest przechowywana w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wskaźnik do wpisywalnego .

*Wartość*\
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartego przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_add_explicit` wykonuje `read-modify-write` operację, aby niepodzielnie dodać *wartość* do przechowywanej wartości w *Atom,* w `Order` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczenia, które są określone przez .

Gdy typ niepodzielny jest `atomic_address`, `Value` ma typ `ptrdiff_t` i `char *`operacja traktuje przechowywany wskaźnik jako .

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

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

Wykonuje bitowy `and` na wartość i istniejącą wartość, `atomic` która jest przechowywana w obiekcie.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_and` `read-modify-write` wykonuje operację, aby zastąpić przechowywaną wartość *Atom* bitowym `and` *wartością* i bieżącą wartością `memory_order_seq_cst`przechowywaną w *Atom*, przy użyciu wiązania [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

Wykonuje `and` bitowy wartości i istniejącej wartości, która `atomic` jest przechowywana w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_and_explicit` wykonuje operację, aby zastąpić `read-modify-write` zapisaną wartość *Atom* `and` bitowym *wartością* i bieżącą wartością przechowywaną w *Atom,* w ramach ograniczeń pamięci określonych przez *Kolejność*.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Wykonuje bitowy `or` na wartość i istniejącą wartość, `atomic` która jest przechowywana w obiekcie.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_or` wykonuje operację, aby zastąpić zapisaną `read-modify-write` wartość *Atom* `or` bitowym *wartością* i bieżącą wartością przechowywaną w *Atom*, używając `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

Wykonuje bitowy `or` na wartość i istniejącą wartość, `atomic` która jest przechowywana w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_or_explicit` wykonuje operację, `read-modify-write` aby zastąpić zapisaną wartość *Atom* bitowym `or` *wartością* i bieżącą wartością przechowywaną w *Atom,* w [ramach ograniczeń memory_order](../standard-library/atomic-enums.md#memory_order_enum) określonych przez *Kolejność*.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

Odejmuje wartość od istniejącej wartości `atomic` przechowywanej w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wskaźnik do wpisywalnego .

*Wartość*\
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartego przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_sub` wykonuje `read-modify-write` operację, aby niepodzielnie odejmować *Wartość* od przechowywanej wartości w *Atom*, używając `memory_order_seq_cst`wiązania [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

Gdy typem `atomic_address`niepodzielnym jest *, Wartość* ma typ `ptrdiff_t` `char *`i operacja traktuje przechowywany wskaźnik jako .

Ta operacja jest również przeciążona dla typów całkowitych:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

Odejmuje wartość od istniejącej wartości `atomic` przechowywanej w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wskaźnik do wpisywalnego .

*Wartość*\
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwracana

Wartość wskaźnika zawartego przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_sub_explicit` wykonuje `read-modify-write` operację, aby niepodzielnie odejmować *Wartość* od wartości przechowywanej w *Atom,* w [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczeniach, które są określone przez `Order`.

Gdy typem `atomic_address`niepodzielnym jest *, Wartość* ma typ `ptrdiff_t` `char *`i operacja traktuje przechowywany wskaźnik jako .

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

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

Wykonuje bitowy `exclusive or` na wartość i istniejącą wartość, `atomic` która jest przechowywana w obiekcie.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_xor` wykonuje operację, aby zastąpić zapisaną `read-modify-write` wartość *Atom* `exclusive or` bitowym *wartością* i bieżącą wartością przechowywaną w *Atom*, używając `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

Wykonuje bitowy `exclusive or` na wartość i istniejącą wartość, `atomic` która jest przechowywana w obiekcie.

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

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

*Wartość*\
Wartość typu `T`.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość zawarta przez obiekt atomowy bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_xor_explicit` wykonuje operację, aby zastąpić `read-modify-write` zapisaną wartość *Atom* bitowym `exclusive or` *wartością* i bieżącą wartością przechowywaną w *Atom,* w [memory_order](../standard-library/atomic-enums.md#memory_order_enum) ograniczeniach określonych przez *Order*.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Ustawia flagę **bool** w [atomic_flag](../standard-library/atomic-flag-structure.md) obiektu na **false,** w `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga*\
Wskaźnik do `atomic_flag` obiektu.

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Ustawia flagę **bool** w [atomic_flag](../standard-library/atomic-flag-structure.md) obiekt na **false,** w ramach określonych [ograniczeń memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga*\
Wskaźnik do `atomic_flag` obiektu.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Ustawia flagę **bool** w [atomic_flag](../standard-library/atomic-flag-structure.md) obiektu na **true,** w `memory_order_seq_cst`granicach [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga*\
Wskaźnik do `atomic_flag` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość początkowa *Flaga*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Ustawia flagę **bool** w [atomic_flag](../standard-library/atomic-flag-structure.md) obiektu na **true,** w ramach określonych [ograniczeń memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Flaga*\
Wskaźnik do `atomic_flag` obiektu.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwracana

Wartość początkowa *Flaga*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Ustawia przechowywaną wartość `atomic` w obiekcie.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `Ty`wartość typu .

*Wartość*\
Wartość typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_init`nie jest operacją atomową. Nie jest bezpieczny dla wątków.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

Określa, czy operacje `atomic` niepodzielne na obiekcie są *wolne od blokady*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu, który przechowuje `T`wartość typu .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli operacje atomowe na *Atom* są wolne od blokad; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Typ niepodzielny jest wolny od blokady, jeśli żadne operacje niepodzielne na tym typie używają blokad. Jeśli ta funkcja zwraca true, typ jest bezpieczny do użycia w programach obsługi sygnału.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

Pobiera przechowywaną wartość `atomic` w obiekcie.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu zawierającego wartość `Ty`typu .

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość przechowywana w *Atom*.

### <a name="remarks"></a>Uwagi

`atomic_load`niejawnie używa `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

Pobiera przechowywaną wartość `atomic` w obiekcie w określonym [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do `atomic` obiektu zawierającego wartość `Ty`typu .

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie używać `memory_order_release` `memory_order_acq_rel`lub .

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość przechowywana w *Atom*.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Działa jako *ogrodzenie*— co jest prymitywne synchronizacji pamięci, która wymusza kolejność między operacjami ładowania/przechowywania — między innymi ogrodzeniami w wątku wywołującym, które mają programy obsługi sygnału, które są wykonywane w tym samym wątku.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Zamówienia*\
Ograniczenie kolejności pamięci, które określa typ ogrodzenia.

### <a name="remarks"></a>Uwagi

*Order,* argument określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenie nie ma wpływu.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem nabywanym.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem nabywanym.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem zwalnianym.|
|`memory_order_acq_rel`|Ogrodzenie jest zarówno ogrodzeniem nabywanym, jak i ogrodzeniem zwalnianym.|
|`memory_order_seq_cst`|Ogrodzenie jest zarówno ogrodzeniem nabytym, jak i ogrodzeniem zwalnianym i jest sekwencyjnie spójne.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

Niepodzielnie przechowuje wartość w obiekcie atomowym.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Wskaźnik do obiektu atomowego, który `Ty`zawiera wartość typu .

*Wartość*\
Wartość typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_store`przechowuje *Wartość* w obiekcie, który jest `memory_order_seq_cst`wskazywał *atom*, w ramach ograniczenia [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

Niepodzielnie przechowuje wartość w obiekcie atomowym.

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

*Atom*\
Wskaźnik do `atomic` obiektu zawierającego wartość `Ty`typu .

*Wartość*\
Wartość typu `Ty`.

*Zamówienia*\
[A memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie `memory_order_consume`używaj `memory_order_acquire`, `memory_order_acq_rel`lub .

### <a name="remarks"></a>Uwagi

`atomic_store`przechowuje *Wartość* w obiekcie, który jest `memory_order` wskazywał *atom*, w obrębie, który jest określony przez *Kolejność*.

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Działa jako *ogrodzenie*— które jest prymitywne synchronizacji pamięci, które wymusza kolejność między operacjami ładowania/magazynu — bez skojarzonej operacji atomowej.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Zamówienia*\
Ograniczenie kolejności pamięci, które określa typ ogrodzenia.

### <a name="remarks"></a>Uwagi

*Order,* argument określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Ogrodzenie nie ma wpływu.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem nabywanym.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem nabywanym.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem zwalnianym.|
|`memory_order_acq_rel`|Ogrodzenie jest zarówno ogrodzeniem nabywanym, jak i ogrodzeniem zwalnianym.|
|`memory_order_seq_cst`|Ogrodzenie jest zarówno ogrodzeniem nabytym, jak i ogrodzeniem zwalnianym i jest sekwencyjnie spójne.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

Usuwa zależność.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Arg*\
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwracana

Zwracaną wartością jest *Arg*. Ocena *Arg* nie posiada zależności do wywołania funkcji. Przez przerwanie łańcucha zależności możliwe, funkcja może zezwolić kompilatorowi do generowania bardziej wydajnego kodu.

## <a name="see-also"></a>Zobacz też

[\<>atomowy](../standard-library/atomic.md)
