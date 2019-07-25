---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 515318cda2155db81406a5c23cb64e46e79c4e19
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448410"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Dołącz do > standardowego \<nagłówka mutex, aby zdefiniować klasy `mutex`, `recursive_mutex`, `timed_mutex`, i `recursive_timed_mutex`; szablony `lock_guard` i `unique_lock`; oraz obsługiwane typy i funkcje, które definiują regiony kodu wzajemnego wykluczania.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 typy C++ synchronizacji biblioteki standardowej są oparte na prymitywach synchronizacji systemu Windows i nie używają już ConcRT (z wyjątkiem sytuacji, gdy platforma docelowa to system Windows XP). Typów zdefiniowanych w \<elemencie mutex > nie należy używać z żadnymi typami lub funkcjami ConcRT.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> mutex

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, ten nagłówek jest zablokowany.

Klasy `mutex` i `recursive_mutex` są *typami muteksów*. Typ muteksu ma domyślny Konstruktor i destruktor, który nie zgłasza wyjątków. Te obiekty mają metody, które zapewniają wzajemne wykluczenie, gdy wiele wątków próbuje zablokować ten sam obiekt. W każdym przypadku typ muteksu zawiera metody `lock`, `try_lock`, i `unlock`:

- `lock` Metoda blokuje wątek wywołujący do momentu, gdy wątek uzyska własność obiektu mutex. Wartość zwracana jest ignorowana.

- `try_lock` Metoda próbuje uzyskać własność obiektu mutex bez blokowania. Typ zwracany jest konwertowany na **bool** i ma **wartość true** , jeśli metoda uzyskuje własność, ale w przeciwnym razie ma **wartość false**.

- `unlock` Metoda zwalnia własność obiektu mutex z wątku wywołującego.

Typów muteksów można użyć jako argumentów typu, aby utworzyć wystąpienia `lock_guard` szablonów `unique_lock`i. Możesz użyć obiektów tych typów jako `Lock` argumentu dla funkcji Członkowskich oczekiwania w szablonie [condition_variable_any](../standard-library/condition-variable-any-class.md).

*Typ muteksu czasu* jest zgodny z wymaganiami dla typu muteksu. Ponadto ma `try_lock_for` metody i `try_lock_until` , które muszą być wywoływane przy użyciu jednego argumentu i muszą zwracać typ, który jest konwertowany na **bool**. Typ muteksu czasu można zdefiniować te funkcje przy użyciu dodatkowych argumentów, pod warunkiem, że te dodatkowe argumenty mają wartości domyślne.

- Metoda musi być wywoływana przy użyciu jednego argumentu, `Rel_time`którego typ jest wystąpieniem [chrono::d wersja](../standard-library/duration-class.md). `try_lock_for` Metoda próbuje uzyskać własność obiektu mutex, ale zwraca w czasie wyznaczonym przez `Rel_time`, bez względu na powodzenie. Wartość zwracana jest konwertowana na **wartość true** , jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana jest konwertowana na **wartość false**.

- Metoda musi być wywoływana przy użyciu jednego argumentu, `Abs_time`którego typ jest wystąpieniem elementu [chrono:: time_point](../standard-library/time-point-class.md). `try_lock_until` Metoda próbuje uzyskać własność obiektu mutex, ale zwraca wartość nie później niż godzina wyznaczenia przez `Abs_time`, bez względu na powodzenie. Wartość zwracana jest konwertowana na **wartość true** , jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana jest konwertowana na **wartość false**.

Typ muteksu jest również znany jako *Typ*podlegającego blokowaniu. Jeśli nie udostępnia funkcji `try_lock`składowej, jest to *Typ podstawowy*, który jest zamykany. Typ muteksu czasu jest znany również jako typ przewidzianego *czasu*.

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[lock_guard, klasa](../standard-library/lock-guard-class.md)|Reprezentuje szablon, który może być skonkretyzowany do utworzenia obiektu, którego destruktor odblokowuje `mutex`.|
|[mutex, klasa (Standardowa biblioteka C++)](../standard-library/mutex-class-stl.md)|Reprezentuje typ muteksu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenie w ramach programu.|
|[recursive_mutex, klasa](../standard-library/recursive-mutex-class.md)|Reprezentuje typ muteksu. W odniesieniu do `mutex` klasy zachowanie wywoływania metod blokowania dla obiektów, które są już zablokowane jest prawidłowo zdefiniowane.|
|[recursive_timed_mutex, klasa](../standard-library/recursive-timed-mutex-class.md)|Reprezentuje typ muteksu czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenia, które mają ograniczone czasowo blokowanie w ramach programu. W przeciwieństwie do obiektów `timed_mutex`typu, efekt wywołania metod blokowania dla `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.|
|[Klasa scoped_lock](../standard-library/scoped-lock-class.md)||
|[timed_mutex, klasa](../standard-library/timed-mutex-class.md)|Reprezentuje typ muteksu czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenia, które mają ograniczone czasowo blokowanie w ramach programu.|
|[unique_lock, klasa](../standard-library/unique-lock-class.md)|Reprezentuje szablon, który może być skonkretyzowany do tworzenia obiektów, które zarządzają blokowaniem i odblokowywaniem `mutex`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[call_once](../standard-library/mutex-functions.md#call_once)|Zapewnia mechanizm wywoływania określonego możliwego do wywołania obiektu dokładnie raz podczas wykonywania.|
|[lock](../standard-library/mutex-functions.md#lock)|Próbuje zablokować wszystkie argumenty bez zakleszczenia.|
|[swap](../standard-library/mutex-functions.md#swap)||
|[try_lock](../standard-library/mutex-functions.md#try_lock)||

### <a name="structs"></a>Struktury

|||
|-|-|
|[adopt_lock_t, struktura](../standard-library/adopt-lock-t-structure.md)|Reprezentuje typ, który jest używany do definiowania `adopt_lock`.|
|[defer_lock_t, struktura](../standard-library/defer-lock-t-structure.md)|Reprezentuje typ, który definiuje `defer_lock` obiekt, który jest używany do wybrania jednego z przeciążonych `unique_lock`konstruktorów.|
|[once_flag, struktura](../standard-library/once-flag-structure.md)|Reprezentuje **strukturę** , która jest używana z funkcją `call_once` szablonu, aby upewnić się, że kod inicjalizacji jest wywoływany tylko raz, nawet w obecności wielu wątków wykonania.|
|[try_to_lock_t, struktura](../standard-library/try-to-lock-t-structure.md)|Reprezentuje **strukturę** , która definiuje `try_to_lock` obiekt i służy do wybrania jednego z przeciążonych konstruktorów. `unique_lock`|

### <a name="variables"></a>Zmienne

|||
|-|-|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Reprezentuje obiekt, który może być przesłany do konstruktorów `unique_lock` dla `lock_guard` i, aby wskazać, że obiekt mutex, który jest również przesyłany do konstruktora jest zablokowany.|
|[defer_lock](../standard-library/mutex-functions.md#defer_lock)|Reprezentuje obiekt, który może zostać przesłany do konstruktora dla `unique_lock`, w celu wskazania, że Konstruktor nie powinien blokować obiektu mutex, który jest również przesyłany do niego.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Reprezentuje obiekt, który może zostać przesłany do konstruktora `unique_lock` w celu wskazania, że Konstruktor powinien próbować `mutex` odblokować, który jest również przekazywać do niego bez blokowania.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
