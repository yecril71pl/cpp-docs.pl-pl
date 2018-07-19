---
title: '&lt;mutex&gt; funkcje i zmienne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: df52b5bdf9b7054fd838b1892c4e641cdf9d4dcc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962191"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;mutex&gt; funkcje i zmienne

||||
|-|-|-|
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock —](#defer_lock)|
|[lock](#lock)|[try_to_lock](#try_to_lock)|

## <a name="adopt_lock"></a>  adopt_lock — zmienna

Reprezentuje obiekt, który może być przekazywany do konstruktory [lock_guard](../standard-library/lock-guard-class.md) i [unique_lock](../standard-library/unique-lock-class.md) do wskazania, że obiekt mutex, który również jest przekazywana do konstruktora jest zablokowany.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>  call_once —

Udostępnia mechanizm do wywoływania określonego wywoływanego obiektu tylko raz podczas wykonywania.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parametry

*Flaga* A [once_flag](../standard-library/once-flag-structure.md) obiekt, który gwarantuje, że obiekt jest wywoływana tylko raz.

*F* wywoływanego obiektu.

*A* listy argumentów.

### <a name="remarks"></a>Uwagi

Jeśli *flagi* jest nieprawidłowy, funkcja zgłasza [system_error](../standard-library/system-error-class.md) zawierający kod błędu `invalid_argument`. W przeciwnym razie używa funkcji szablonu jego *flagi* argumentu, aby upewnić się, że wywołuje on `F(A...)` pomyślnie dokładnie jeden raz, niezależnie od tego, ile razy funkcji szablonu jest wywoływana. Jeśli `F(A...)` wyjścia, zostanie zgłoszony wyjątek, wywołanie nie powiodło się.

## <a name="defer_lock"></a>  defer_lock — zmienna

Reprezentuje obiekt, który może być przekazywany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md). Oznacza to, że Konstruktor nie powinien być blokowany obiektu mutex, który również jest przekazywana do niego.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>  Blokady

Próbuje zablokować wszystkie argumenty bez zakleszczenia.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Uwagi

Argumenty do funkcji szablonu musi być *typów obiektu mutex*, z wyjątkiem który wywołuje w celu `try_lock` może zgłaszać wyjątki.

Funkcja blokuje wszystkie jej argumenty bez zakleszczenia wywołań `lock`, `try_lock`, i `unlock`. Jeśli wywołanie `lock` lub `try_lock` zgłasza wyjątek, wywołania funkcji `unlock` na obiekty mutex, które zostały pomyślnie zablokowane przed ponowne generowanie wyjątku.

## <a name="try_to_lock"></a>  try_to_lock — zmienna

Reprezentuje obiekt, który może być przekazywany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md) do wskazania, konstruktora powinien próbować odblokować `mutex` , również przekazywaną do niego bez blokowania.

```cpp
const try_to_lock_t try_to_lock;
```

## <a name="see-also"></a>Zobacz także

[\<mutex>](../standard-library/mutex.md)<br/>
