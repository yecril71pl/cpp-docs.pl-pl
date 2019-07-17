---
title: '&lt;mutex&gt; funkcje i zmienne'
ms.date: 11/04/2016
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: f6bd6a86e91c2d59fec2083dcf0ec6314d7c41ab
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240567"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; funkcje i zmienne

## <a name="adopt_lock"></a> adopt_lock —

Reprezentuje obiekt, który może być przekazywany do konstruktory [lock_guard](../standard-library/lock-guard-class.md) i [unique_lock](../standard-library/unique-lock-class.md) do wskazania, że obiekt mutex, który również jest przekazywana do konstruktora jest zablokowany.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a> call_once —

Udostępnia mechanizm do wywoływania określonego wywoływanego obiektu tylko raz podczas wykonywania.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parametry

*Flaga*\
A [once_flag](../standard-library/once-flag-structure.md) obiekt, który gwarantuje, że obiekt jest wywoływana tylko raz.

*F*\
Obiekt możliwy do wywołania.

*ELEMENT*\
Listy argumentów.

### <a name="remarks"></a>Uwagi

Jeśli *flagi* jest nieprawidłowy, funkcja zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `invalid_argument`. W przeciwnym razie używa funkcji szablonu jego *flagi* argumentu, aby upewnić się, że wywołuje on `F(A...)` pomyślnie dokładnie jeden raz, niezależnie od tego, ile razy funkcji szablonu jest wywoływana. Jeśli `F(A...)` wyjścia, zostanie zgłoszony wyjątek, wywołanie nie powiodło się.

## <a name="defer_lock"></a> defer_lock —

Reprezentuje obiekt, który może być przekazywany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md). Oznacza to, że Konstruktor nie powinien być blokowany obiektu mutex, który również jest przekazywana do niego.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a> Blokady

Próbuje zablokować wszystkie argumenty bez zakleszczenia.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Uwagi

Argumenty do funkcji szablonu musi być *typów obiektu mutex*, z wyjątkiem który wywołuje w celu `try_lock` może zgłaszać wyjątki.

Funkcja blokuje wszystkie jej argumenty bez zakleszczenia wywołań `lock`, `try_lock`, i `unlock`. Jeśli wywołanie `lock` lub `try_lock` zgłasza wyjątek, wywołania funkcji `unlock` na obiekty mutex, które zostały pomyślnie zablokowane przed ponowne generowanie wyjątku.

## <a name="swap"></a> swap

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a> try_lock —

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a> try_to_lock —

Reprezentuje obiekt, który może być przekazywany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md) do wskazania, konstruktora powinien próbować odblokować `mutex` , również przekazywaną do niego bez blokowania.

```cpp
const try_to_lock_t try_to_lock;
```
