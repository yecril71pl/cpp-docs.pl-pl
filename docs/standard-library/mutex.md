---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: e17488023d8de6eb5d341c719be8f1b36c14ffcd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228183"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Uwzględnij standardowy nagłówek, \<mutex> Aby zdefiniować klasy `mutex` , `recursive_mutex` , `timed_mutex` , i, `recursive_timed_mutex` Szablony oraz `lock_guard` oraz `unique_lock` typy pomocnicze i funkcje, które definiują regiony kodu wykluczania.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 typy synchronizacji standardowej biblioteki języka C++ są oparte na prymitywach synchronizacji systemu Windows i nie są już używane ConcRT (z wyjątkiem sytuacji, gdy platforma docelowa to system Windows XP). Typów zdefiniowanych w \<mutex> nie należy używać z żadnymi typami lub funkcjami ConcRT.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<mutex>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, ten nagłówek jest zablokowany.

Klasy `mutex` i `recursive_mutex` są *typami muteksów*. Typ muteksu ma domyślny Konstruktor i destruktor, który nie zgłasza wyjątków. Te obiekty mają metody, które zapewniają wzajemne wykluczenie, gdy wiele wątków próbuje zablokować ten sam obiekt. W każdym przypadku typ muteksu zawiera metody `lock` , `try_lock` , i `unlock` :

- `lock`Metoda blokuje wątek wywołujący do momentu, gdy wątek uzyska własność obiektu mutex. Wartość zwracana jest ignorowana.

- `try_lock`Metoda próbuje uzyskać własność obiektu mutex bez blokowania. Typ zwracany jest konwertowany na **`bool`** i jest, **`true`** Jeśli metoda uzyskuje własność, ale w przeciwnym razie **`false`** .

- `unlock`Metoda zwalnia własność obiektu mutex z wątku wywołującego.

Typów muteksów można użyć jako argumentów typu, aby utworzyć wystąpienia szablonów `lock_guard` i `unique_lock` . Możesz użyć obiektów tych typów jako `Lock` argumentu dla funkcji Członkowskich oczekiwania w [condition_variable_any](../standard-library/condition-variable-any-class.md)szablonu.

*Typ muteksu czasu* jest zgodny z wymaganiami dla typu muteksu. Ponadto ma `try_lock_for` `try_lock_until` metody i, które muszą być wywoływane przy użyciu jednego argumentu i muszą zwracać typ, który jest konwertowany na **`bool`** . Typ muteksu czasu można zdefiniować te funkcje przy użyciu dodatkowych argumentów, pod warunkiem, że te dodatkowe argumenty mają wartości domyślne.

- `try_lock_for`Metoda musi być wywoływana przy użyciu jednego argumentu, `Rel_time` którego typ jest wystąpieniem [chrono::d wersja](../standard-library/duration-class.md). Metoda próbuje uzyskać własność obiektu mutex, ale zwraca w czasie wyznaczonym przez `Rel_time` , bez względu na powodzenie. Wartość zwracana jest konwertowana na **`true`** , jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana jest konwertowana na **`false`** .

- `try_lock_until`Metoda musi być wywoływana przy użyciu jednego argumentu, `Abs_time` którego typ jest wystąpieniem elementu [chrono:: time_point](../standard-library/time-point-class.md). Metoda próbuje uzyskać własność obiektu mutex, ale zwraca wartość nie później niż godzina wyznaczenia przez `Abs_time` , bez względu na powodzenie. Wartość zwracana jest konwertowana na **`true`** , jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana jest konwertowana na **`false`** .

Typ muteksu jest również znany jako *Typ podlegającego blokowaniu*. Jeśli nie udostępnia funkcji składowej `try_lock` , jest to *Typ podstawowy*, który jest zamykany. Typ muteksu czasu jest znany również jako typ przewidzianego *czasu*.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa lock_guard](../standard-library/lock-guard-class.md)|Reprezentuje szablon, który może być skonkretyzowany do utworzenia obiektu, którego destruktor odblokowuje `mutex` .|
|[mutex — Klasa (standardowa biblioteka C++)](../standard-library/mutex-class-stl.md)|Reprezentuje typ muteksu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenie w ramach programu.|
|[Klasa recursive_mutex](../standard-library/recursive-mutex-class.md)|Reprezentuje typ muteksu. W `mutex` odniesieniu do klasy zachowanie wywoływania metod blokowania dla obiektów, które są już zablokowane jest prawidłowo zdefiniowane.|
|[Klasa recursive_timed_mutex](../standard-library/recursive-timed-mutex-class.md)|Reprezentuje typ muteksu czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenia, które mają ograniczone czasowo blokowanie w ramach programu. W przeciwieństwie do obiektów typu `timed_mutex` , efekt wywołania metod blokowania dla `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.|
|[Klasa scoped_lock](../standard-library/scoped-lock-class.md)||
|[Klasa timed_mutex](../standard-library/timed-mutex-class.md)|Reprezentuje typ muteksu czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenia, które mają ograniczone czasowo blokowanie w ramach programu.|
|[Klasa unique_lock](../standard-library/unique-lock-class.md)|Reprezentuje szablon, który może być skonkretyzowany do tworzenia obiektów, które zarządzają blokowaniem i odblokowywaniem `mutex` .|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Zapewnia mechanizm wywoływania określonego możliwego do wywołania obiektu dokładnie raz podczas wykonywania.|
|[skręt](../standard-library/mutex-functions.md#lock)|Próbuje zablokować wszystkie argumenty bez zakleszczenia.|
|[wymiany](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Struktury

|||
|-|-|
|[adopt_lock_t — Struktura](../standard-library/adopt-lock-t-structure.md)|Reprezentuje typ, który jest używany do definiowania `adopt_lock` .|
|[defer_lock_t — Struktura](../standard-library/defer-lock-t-structure.md)|Reprezentuje typ, który definiuje `defer_lock` obiekt, który jest używany do wybrania jednego z przeciążonych konstruktorów `unique_lock` .|
|[once_flag — Struktura](../standard-library/once-flag-structure.md)|Reprezentuje **`struct`** , który jest używany z funkcją szablonu, `call_once` Aby upewnić się, że kod inicjalizacji jest wywoływany tylko raz, nawet w obecności wielu wątków wykonania.|
|[try_to_lock_t — Struktura](../standard-library/try-to-lock-t-structure.md)|Reprezentuje element **`struct`** , który definiuje `try_to_lock` obiekt i służy do wybrania jednego z przeciążonych konstruktorów `unique_lock` .|

### <a name="variables"></a>Zmienne

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Reprezentuje obiekt, który może być przesłany do konstruktorów dla `lock_guard` i, `unique_lock` Aby wskazać, że obiekt mutex, który jest również przesyłany do konstruktora jest zablokowany.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Reprezentuje obiekt, który może zostać przesłany do konstruktora dla `unique_lock` , w celu wskazania, że Konstruktor nie powinien blokować obiektu mutex, który jest również przesyłany do niego.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Reprezentuje obiekt, który może zostać przesłany do konstruktora w `unique_lock` celu wskazania, że Konstruktor powinien próbować odblokować, `mutex` który jest również przekazywać do niego bez blokowania.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
