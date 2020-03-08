---
title: '&lt;muteksy&gt; funkcje i zmienne'
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856303"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;muteksy&gt; funkcje i zmienne

## <a name="adopt_lock"></a>adopt_lock

Reprezentuje obiekt, który może zostać przesłany do konstruktorów dla [lock_guard](../standard-library/lock-guard-class.md) i [unique_lock](../standard-library/unique-lock-class.md) , aby wskazać, że obiekt mutex, który jest również przesyłany do konstruktora jest zablokowany.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>call_once

Zapewnia mechanizm wywoływania określonego możliwego do wywołania obiektu dokładnie raz podczas wykonywania.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parametry

\ *flagi*
Obiekt [once_flag](../standard-library/once-flag-structure.md) , który zapewnia, że obiekt możliwy do wywołania jest wywoływany tylko raz.

\ *F*
Obiekt możliwy do narzutu.

*\*
Lista argumentów.

### <a name="remarks"></a>Uwagi

Jeśli *Flaga* jest nieprawidłowa, funkcja zgłasza [system_error](../standard-library/system-error-class.md) , która ma kod błędu `invalid_argument`. W przeciwnym razie funkcja szablonu używa jej argumentu *flagi* , aby upewnić się, że wywołuje `F(A...)` prawidłowo, niezależnie od tego, ile razy funkcja szablonu jest wywoływana. Jeśli `F(A...)` opuszcza przez wyrzucanie wyjątku, wywołanie zakończyło się niepowodzeniem.

## <a name="defer_lock"></a>defer_lock

Reprezentuje obiekt, który może zostać przesłany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md). Oznacza to, że Konstruktor nie powinien blokować obiektu mutex, który jest również przekazywać do niego.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>skręt

Próbuje zablokować wszystkie argumenty bez zakleszczenia.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Uwagi

Argumenty funkcji szablonu muszą być *typami muteksów*, z tą różnicą, że wywołania `try_lock` mogą zgłaszać wyjątki.

Funkcja blokuje wszystkie argumenty bez zakleszczenia przez wywołania do `lock`, `try_lock`i `unlock`. Jeśli wywołanie `lock` lub `try_lock` zgłasza wyjątek, funkcja wywołuje `unlock` na dowolnym obiekcie mutex, który został pomyślnie zablokowany przed ponownym zgłoszeniem wyjątku.

## <a name="swap"></a>wymiany

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a>try_lock

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a>try_to_lock

Reprezentuje obiekt, który może zostać przesłany do konstruktora dla [unique_lock](../standard-library/unique-lock-class.md) , aby wskazać, że Konstruktor powinien próbować odblokować `mutex`, który jest również przekazywać do niego bez blokowania.

```cpp
const try_to_lock_t try_to_lock;
```
