---
title: '&lt;mutex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <mutex>
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
ms.openlocfilehash: 4655278e312647f4e69cf48cb772df854260ce57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482566"
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Dołączyć standardowy nagłówek \<mutex > do definiowania klas `mutex`, `recursive_mutex`, `timed_mutex`, i `recursive_timed_mutex`; szablony `lock_guard` i `unique_lock`; i pomocnicze typy i funkcje, które definiują regiony kodu wzajemnego wykluczania.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 standardowej biblioteki języka C++ typów synchronizacji opierają się na podstawowych synchronizacji Windows i nie są już używane ConcRT (z wyjątkiem sytuacji, gdy platformą docelową jest Windows XP). Typy zdefiniowane w \<mutex > nie należy używać z dowolnym ConcRT typów lub funkcji.

## <a name="syntax"></a>Składnia

```cpp
#include <mutex>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, tego pliku nagłówkowego jest zablokowany.

Klasy `mutex` i `recursive_mutex` są *typów obiektu mutex*. Typ obiektu mutex ma domyślny konstruktor i destruktor, który nie generuje wyjątków. Tego rodzaju obiekty mają metody, które zapewniają wzajemne wykluczenie, gdy wiele wątków próbuje zablokować tego samego obiektu. W szczególności typu obiektu mutex zawiera metody `lock`, `try_lock`, i `unlock`:

- `lock` Metoda blokuje wątek wywołujący, aż wątek uzyskuje własność obiektu mutex. Wartość zwracana jest ignorowany.

- `try_lock` Metoda próbuje uzyskać prawo własności obiektu mutex bez blokowania. Jego typem zwracanym jest konwertowany na **bool** i **true** Jeśli metoda uzyskuje własność, ale w inny sposób **false**.

- `unlock` Metoda zwalnia własność obiektu mutex z wątku wywoływania.

Do utworzenia wystąpienia szablony można użyć typów obiektu mutex jako argumentów typu `lock_guard` i `unique_lock`. Możesz użyć obiektów tego typu jako `Lock` argument do funkcji Członkowskich oczekiwania w szablonie [condition_variable_any](../standard-library/condition-variable-any-class.md).

A *upłynął limit czasu typu obiektu mutex* spełnia wymagania dotyczące typu obiektu mutex. Ponadto ma `try_lock_for` i `try_lock_until` metody, które muszą być wywoływane za pomocą jednego argumentu i musi zwracać typ, który jest konwertowany na **bool**. Typ obiektu mutex Przekroczono limit czasu można zdefiniować te funkcje przy użyciu dodatkowych argumentów, pod warunkiem, że te dodatkowe wszystkie argumenty mają przypisane wartości domyślne.

- `try_lock_for` Metoda musi być wywoływane za pomocą jednego argumentu `Rel_time`, którego typem jest egzemplarzem z [chrono::duration](../standard-library/duration-class.md). Metoda próbuje uzyskać prawo własności obiektu mutex, ale zwraca w czasie, który jest wyznaczone przez `Rel_time`, niezależnie od tego, sukcesu. Konwertuje wartość zwracaną **true** Jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana konwertuje **false**.

- `try_lock_until` Metoda musi być wywoływane za pomocą jednego argumentu `Abs_time`, którego typem jest egzemplarzem z [chrono::time_point](../standard-library/time-point-class.md). Metoda próbuje uzyskać prawo własności obiektu mutex, ale nie później niż czas, który jest wyznaczone przez zwraca `Abs_time`, niezależnie od tego, sukcesu. Konwertuje wartość zwracaną **true** Jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracana konwertuje **false**.

Typ obiektu mutex jest także znana jako *zamykane typu*. Jeśli nie zapewnia funkcji elementu członkowskiego `try_lock`, jest *podstawowy typ zamykane*. Typ obiektu mutex Przekroczono limit czasu jest także znana jako *upłynął limit czasu zamykane typu*.

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[lock_guard, klasa](../standard-library/lock-guard-class.md)|Reprezentuje szablon, który można utworzyć wystąpienia, aby utworzyć obiekt, którego destruktor odblokowuje `mutex`.|
|[mutex, klasa (Standardowa biblioteka C++)](../standard-library/mutex-class-stl.md)|Reprezentuje typ obiektu mutex. Używanie obiektów tego typu w celu wymuszenia wzajemnego wykluczenia w ramach programu.|
|[recursive_mutex, klasa](../standard-library/recursive-mutex-class.md)|Reprezentuje typ obiektu mutex. W constrast do `mutex` klasy, zachowanie wywoływania metod blokowania dla obiektów, które są już zablokowane jest dobrze zdefiniowany.|
|[recursive_timed_mutex, klasa](../standard-library/recursive-timed-mutex-class.md)|Reprezentuje typ obiektu mutex Przekroczono limit czasu. Używanie obiektów tego typu w celu wymuszenia wzajemnego wykluczenia, który ma czas blokowania w programie. W przeciwieństwie do obiektów tego typu `timed_mutex`, efekt podczas wywoływania metody blokowania `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.|
|[timed_mutex, klasa](../standard-library/timed-mutex-class.md)|Reprezentuje typ obiektu mutex Przekroczono limit czasu. Używanie obiektów tego typu w celu wymuszenia wzajemnego wykluczenia, który ma czas blokowania w programie.|
|[unique_lock, klasa](../standard-library/unique-lock-class.md)|Reprezentuje szablon, który można utworzyć wystąpienia do tworzenia obiektów, które zarządzają blokowanie i odblokowywanie `mutex`.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[call_once](../standard-library/mutex-functions.md#call_once)|Udostępnia mechanizm do wywoływania określonego wywoływanego obiektu tylko raz podczas wykonywania.|
|[lock](../standard-library/mutex-functions.md#lock)|Próbuje zablokować wszystkie argumenty bez zakleszczenia.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[adopt_lock_t, struktura](../standard-library/adopt-lock-t-structure.md)|Reprezentuje typ, który jest używany do definiowania `adopt_lock`.|
|[defer_lock_t, struktura](../standard-library/defer-lock-t-structure.md)|Reprezentuje typ, który definiuje `defer_lock` obiekt, który jest używany do wybierania jednego z przeciążenia konstruktorów z `unique_lock`.|
|[once_flag, struktura](../standard-library/once-flag-structure.md)|Reprezentuje **struktury** używany za pomocą funkcji szablonu `call_once` aby upewnić się, że inicjowanie kodu jest wywoływana tylko raz, nawet w obecności wielu wątków wykonania.|
|[try_to_lock_t, struktura](../standard-library/try-to-lock-t-structure.md)|Reprezentuje **struktury** definiujący `try_to_lock` obiektu i umożliwia wybranie jednej z przeciążenia konstruktorów z `unique_lock`.|

### <a name="variables"></a>Zmienne

|Nazwa|Opis|
|----------|-----------------|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Reprezentuje obiekt, który może być przekazywany do konstruktory `lock_guard` i `unique_lock` do wskazania, że obiekt mutex, który również jest przekazywana do konstruktora jest zablokowany.|
|[defer_lock —](../standard-library/mutex-functions.md#defer_lock)|Reprezentuje obiekt, który może być przekazywany do konstruktora dla `unique_lock`, aby wskazać, że Konstruktor nie powinien być blokowany obiektu mutex, który również jest przekazywana do niego.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Reprezentuje obiekt, który może być przekazywany do konstruktora dla `unique_lock` do wskazania, konstruktora powinien próbować odblokować `mutex` , również przekazywaną do niego bez blokowania.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
