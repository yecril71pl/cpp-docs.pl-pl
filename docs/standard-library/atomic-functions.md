---
title: '&lt;niepodzielne funkcje&gt;'
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
ms.openlocfilehash: 5314db43bed913e801846341309513c239216887
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421997"
---
# <a name="ltatomicgt-functions"></a>&lt;niepodzielne funkcje&gt;

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

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

Wykonuje porównanie atomowe i wymianę operacji.

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

\ *Atom*
Wskaźnik do obiektu *niepodzielnego* , który przechowuje wartość typu `Ty`.

\ *EXP*
Wskaźnik do wartości typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje porównanie atomowe i wymianę operacji przy użyciu niejawnych argumentów `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) . Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *EXP*
Wskaźnik do wartości typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

*Order1*\
Pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2*\
Drugi argument `memory_order`. Wartość *Order2* nie może być `memory_order_release` ani `memory_order_acq_rel`, nie może być silniejszy niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

*Niepodzielna operacja porównania i wymiany* porównuje wartość, która jest przechowywana w obiekcie, który jest wskazywany przez *Atom* , względem wartości, która jest wskazywana przez *EXP*. Jeśli wartości są równe, wartość, która jest przechowywana w obiekcie, który jest wskazywany przez *Atom* , jest zastępowana *wartością* przy użyciu operacji `read-modify-write` i zastosowania ograniczeń zlecenia pamięci, które są określone przez *Order1*. Jeśli wartości nie są równe, operacja zastępuje wartość, która jest wskazywany przez *EXP* wartością przechowywaną w obiekcie, który jest wskazywany przez *Atom* i stosuje ograniczenia zlecenia pamięci, które są określone przez *Order2*.

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

Wykonuje *słabą, niepodzielną operację porównania i wymiany* .

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *EXP*
Wskaźnik do wartości typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje *słabą, niepodzielną operację porównania i wymiany* , która ma niejawne `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentów. Aby uzyskać więcej informacji, zobacz [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

Wykonuje *słabą, niepodzielną operację porównania i wymiany* .

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *EXP*
Wskaźnik do wartości typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

*Order1*\
Pierwszy [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2*\
Drugi argument `memory_order`. Wartość *Order2* nie może być `memory_order_release` ani `memory_order_acq_rel`, ani nie może być silniejszy niż wartość *Order1*.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli wartości są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zarówno silne, jak i słabe *wersje niepodzielnych operacji porównania i wymiany* gwarantują, że nie przechowują nowej wartości, jeśli wartości oczekiwane i bieżące nie są równe. Silna wersja gwarantuje, że będzie przechowywać nową wartość, jeśli oczekiwane i bieżące wartości są równe. Słaba wersja może czasami zwracać **wartość false** i nie przechowywać nowej wartości, nawet jeśli bieżące i oczekiwane wartości są równe. Innymi słowy, funkcja zwróci **wartość false**, ale późniejsze badanie oczekiwanej wartości może ujawnić, że nie uległa zmianie, i dlatego powinno być porównywane jako równe.

## <a name="atomic_exchange"></a>atomic_exchange

Używa *wartości* , aby zastąpić przechowywaną wartość *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwrócona

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_exchange` wykonuje operację `read-modify-write` do wymiany wartości przechowywanej w *Atom* z *wartością*przy użyciu [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Zastępuje przechowywaną wartość *Atom* z *wartością*.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwrócona

Przechowywana wartość *Atom* przed wymianą.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_exchange_explicit` wykonuje operację `read-modify-write` do wymiany wartości przechowywanej w *Atom* z *wartością*w ramach ograniczeń pamięci, które są określone przez *kolejność*.

## <a name="atomic_fetch_add"></a>atomic_fetch_add

Dodaje wartość do istniejącej wartości przechowywanej w obiekcie `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, który przechowuje wskaźnik do typu `T`.

\ *wartości*
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwrócona

Wartość wskaźnika zawartego przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_add` wykonuje operację `read-modify-write` do niepodzielnego dodawania *wartości* do wartości przechowywanej w *atomze*przy użyciu ograniczenia `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Gdy typ niepodzielny jest `atomic_address`, *wartość* ma typ `ptrdiff_t` i operacja traktuje przechowywany wskaźnik jako `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

Dodaje wartość do istniejącej wartości przechowywanej w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, który przechowuje wskaźnik do typu `T`.

\ *wartości*
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwrócona

Wartość wskaźnika zawartego przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_add_explicit` wykonuje operację `read-modify-write` do niepodzielnego dodawania *wartości* do wartości przechowywanej w *atomze*w ramach ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) , które są określone przez `Order`.

Gdy typ niepodzielny jest `atomic_address`, `Value` ma `ptrdiff_t` typu, a operacja traktuje przechowywany wskaźnik jako `char *`.

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

## <a name="atomic_fetch_and"></a>atomic_fetch_and

Wykonuje `and` bitowe na wartości i istniejącej wartości przechowywanej w obiekcie `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_and` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitową `and`ą *wartości* i bieżącą wartością przechowywaną w *Atom*przy użyciu ograniczenia `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

## <a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

Wykonuje `and` bitowe wartości i istniejącą wartość, która jest przechowywana w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_and_explicit` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitową `and`ą *wartości* i bieżącą wartością przechowywaną w *Atom*, w ramach ograniczeń pamięci, które są określone przez *kolejność*.

## <a name="atomic_fetch_or"></a>atomic_fetch_or

Wykonuje `or` bitowe na wartości i istniejącej wartości przechowywanej w obiekcie `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_or` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitową `or`ą *wartości* i bieżącą wartością przechowywaną w *Atom*przy użyciu `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

Wykonuje `or` bitowe na wartości i istniejącej wartości przechowywanej w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_or_explicit` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitowym `or` *wartości* i bieżącą wartością przechowywaną w *Atom*, w ramach ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) określonych przez *kolejność*.

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub

Odejmuje wartość od istniejącej wartości przechowywanej w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, który przechowuje wskaźnik do typu `T`.

\ *wartości*
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwrócona

Wartość wskaźnika zawartego przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_sub` wykonuje operację `read-modify-write` do odejmowania niepodzielnego *wartości z* wartości przechowywanej w *atomze*przy użyciu ograniczenia `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Gdy typ niepodzielny jest `atomic_address`, *wartość* ma typ `ptrdiff_t` i operacja traktuje przechowywany wskaźnik jako `char *`.

Ta operacja jest również przeciążona dla typów całkowitych:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

Odejmuje wartość od istniejącej wartości przechowywanej w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, który przechowuje wskaźnik do typu `T`.

\ *wartości*
Wartość typu `ptrdiff_t`.

### <a name="return-value"></a>Wartość zwrócona

Wartość wskaźnika zawartego przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_sub_explicit` wykonuje operację `read-modify-write` do odejmowania niepodzielnej *wartości z* wartości przechowywanej w *atomze*w ramach ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) , które są określone przez `Order`.

Gdy typ niepodzielny jest `atomic_address`, *wartość* ma typ `ptrdiff_t` i operacja traktuje przechowywany wskaźnik jako `char *`.

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

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor

Wykonuje `exclusive or` bitowe na wartości i istniejącej wartości przechowywanej w obiekcie `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_xor` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitową `exclusive or`ą *wartości* i bieżącą wartością przechowywaną w *Atom*przy użyciu `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

Wykonuje `exclusive or` bitowe na wartości i istniejącej wartości przechowywanej w obiekcie `atomic`.

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

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

\ *wartości*
Wartość typu `T`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwrócona

Wartość zawartej przez obiekt niepodzielny bezpośrednio przed wykonaniem operacji.

### <a name="remarks"></a>Uwagi

Funkcja `atomic_fetch_xor_explicit` wykonuje operację `read-modify-write`, aby zastąpić przechowywaną wartość *Atom* z bitową `exclusive or`ą *wartości* i bieżącą wartością przechowywaną w *Atom*, w ramach ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) określonych przez *kolejność*.

## <a name="atomic_flag_clear"></a>atomic_flag_clear

Ustawia flagę **bool** w obiekcie [atomic_flag](../standard-library/atomic-flag-structure.md) na **false**w [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

\ *flagi*
Wskaźnik do obiektu `atomic_flag`.

## <a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Ustawia dla flagi **bool** w obiekcie [atomic_flag](../standard-library/atomic-flag-structure.md) **wartość false**, w ramach określonych ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *flagi*
Wskaźnik do obiektu `atomic_flag`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Ustawia dla flagi **bool** w obiekcie [atomic_flag](../standard-library/atomic-flag-structure.md) **wartość true**w ramach ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

\ *flagi*
Wskaźnik do obiektu `atomic_flag`.

### <a name="return-value"></a>Wartość zwrócona

Początkowa wartość *flagi*.

## <a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Ustawia dla flagi **bool** w obiekcie [atomic_flag](../standard-library/atomic-flag-structure.md) **wartość true**w ramach określonych ograniczeń [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *flagi*
Wskaźnik do obiektu `atomic_flag`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Wartość zwrócona

Początkowa wartość *flagi*.

## <a name="atomic_init"></a>atomic_init

Ustawia wartość przechowywaną w obiekcie `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_init` nie jest operacją niepodzielną. Nie jest to bezpieczne dla wątków.

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

Określa, czy operacje niepodzielne na obiekcie `atomic` są *wolne od blokady*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, w którym jest przechowywana wartość typu `T`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli operacje niepodzielne na *atomze* są wolne od blokady. w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Typ niepodzielny jest zablokowany, jeśli żadna niepodzielna operacja na tym typie nie używa blokad. Jeśli ta funkcja zwraca wartość true, typ jest bezpieczny do użycia w obsłudze sygnałów.

## <a name="atomic_load"></a>atomic_load

Pobiera wartość przechowywaną w obiekcie `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, który zawiera wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwrócona

Pobrana wartość, która jest przechowywana w *Atom*.

### <a name="remarks"></a>Uwagi

`atomic_load` niejawnie używa `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>atomic_load_explicit

Pobiera wartość przechowywaną w obiekcie `atomic` w obrębie określonego [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu `atomic`, który zawiera wartość typu `Ty`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie należy używać `memory_order_release` ani `memory_order_acq_rel`.

### <a name="return-value"></a>Wartość zwrócona

Pobrana wartość, która jest przechowywana w *Atom*.

## <a name="atomic_signal_fence"></a>atomic_signal_fence

Działa jako *ogrodzenie*— jest to element podstawowy synchronizacji pamięci, który wymusza kolejność między operacjami ładowania/przechowywania — między innymi ogrodzeniami w wątku wywołującym, które mają programy obsługi sygnałów, które są wykonywane w tym samym wątku.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *kolejności*
Ograniczenie porządkowania pamięci określające typ ogrodzenia.

### <a name="remarks"></a>Uwagi

Argument *Order* określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Horyzont nie ma wpływu.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem pozyskiwania.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem pozyskiwania.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem wydania.|
|`memory_order_acq_rel`|Ogrodzeniem jest zarówno ogrodzeniem, jak i ogrodzeniem wydania.|
|`memory_order_seq_cst`|Horyzont jest zarówno ogrodzeniem, jak i ogrodzeniem wydania i jest sekwencyjnie spójny.|

## <a name="atomic_store"></a>atomic_store

Niepodzielne przechowuje wartość w obiekcie niepodzielnym.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Wskaźnik do obiektu niepodzielnego, który zawiera wartość typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje *wartość* w obiekcie, który jest wskazywany przez *Atom*, w ramach ograniczenia `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

## <a name="atomic_store_explicit"></a>atomic_store_explicit

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

\ *Atom*
Wskaźnik do obiektu `atomic`, który zawiera wartość typu `Ty`.

\ *wartości*
Wartość typu `Ty`.

\ *kolejności*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nie należy używać `memory_order_consume`, `memory_order_acquire`lub `memory_order_acq_rel`.

### <a name="remarks"></a>Uwagi

`atomic_store` przechowuje *wartość* w obiekcie, który jest wskazywany przez *Atom*, w `memory_order`, który jest określony przez *kolejność*.

## <a name="atomic_thread_fence"></a>atomic_thread_fence

Działa jako *ogrodzenie*— jest to element podstawowy synchronizacji pamięci, który wymusza kolejność między operacjami ładowania/przechowywania — bez skojarzonej operacji niepodzielnej.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *kolejności*
Ograniczenie porządkowania pamięci określające typ ogrodzenia.

### <a name="remarks"></a>Uwagi

Argument *Order* określa typ ogrodzenia.

|||
|-|-|
|`memory_order_relaxed`|Horyzont nie ma wpływu.|
|`memory_order_consume`|Ogrodzenie jest ogrodzeniem pozyskiwania.|
|`memory_order_acquire`|Ogrodzenie jest ogrodzeniem pozyskiwania.|
|`memory_order_release`|Ogrodzenie jest ogrodzeniem wydania.|
|`memory_order_acq_rel`|Ogrodzeniem jest zarówno ogrodzeniem, jak i ogrodzeniem wydania.|
|`memory_order_seq_cst`|Horyzont jest zarówno ogrodzeniem, jak i ogrodzeniem wydania i jest sekwencyjnie spójny.|

## <a name="kill_dependency"></a>kill_dependency

Usuwa zależność.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

\ *ARG*
Wartość typu `Ty`.

### <a name="return-value"></a>Wartość zwrócona

Wartość zwracana to *ARG*. Obliczanie wartości *ARG* nie jest zależne od wywołania funkcji. Przez podzielenie możliwego łańcucha zależności funkcja może pozwolić kompilatorowi na generowanie bardziej wydajnego kodu.

## <a name="see-also"></a>Zobacz też

[\<niepodzielne >](../standard-library/atomic.md)
