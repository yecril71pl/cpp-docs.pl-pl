---
title: '&lt;mutex&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <mutex>
dev_langs:
- C++
ms.assetid: efb60c89-687a-4e38-8fe4-694e11c4e8a3
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e47f40fdc96a0df8a76a2713bd8ff02d97d714e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltmutexgt"></a>&lt;mutex&gt;

Dołącz nagłówek standardowy \<obiektu mutex > do definiowania klas `mutex`, `recursive_mutex`, `timed_mutex`, i `recursive_timed_mutex`; szablony `lock_guard` i `unique_lock`; i pomocnicze typy i funkcje, które definiują regiony wzajemne wykluczenie kodu.

> [!WARNING]
> Począwszy od programu Visual Studio 2015, typy synchronizacji standardowa biblioteka C++ są oparte na elementy podstawowe synchronizacji systemu Windows i nie są już używane ConcRT (z wyjątkiem sytuacji, gdy platforma docelowa jest Windows XP). Typy zdefiniowane w \<obiektu mutex > nie powinien być używany z dowolnym ConcRT typów lub funkcji.

## <a name="syntax"></a>Składnia

```cpp
#include <mutex>
```

## <a name="remarks"></a>Uwagi

> [!NOTE]
> W kodzie, który ma być kompilowana przy użyciu **/CLR**, ten nagłówek jest zablokowany.

Klasy `mutex` i `recursive_mutex` są *typów obiektu mutex*. Typ obiektu mutex ma domyślny konstruktor i destruktor, który nie zgłaszają wyjątki. Te obiekty mają metody udostępniające wzajemne wykluczenie, gdy wiele wątków próbuje zablokować tego samego obiektu. W szczególności typu obiektu mutex zawiera metody `lock`, `try_lock`, i `unlock`:

- `lock` Metody blokuje wątek wywołujący, dopóki wątek uzyskuje prawo własności obiektu mutex. Jego wartość zwracana jest ignorowana.

- `try_lock` Metoda próbuje uzyskać prawo własności obiektu mutex bez blokowania. Jego typem zwracanym jest możliwe do przekonwertowania na `bool` i `true` Jeśli metoda uzyskuje prawo własności, a w przeciwnym razie `false`.

- `unlock` Metoda zwalnia własności obiektu mutex z wywołania wątku.

Typy obiektu mutex jako argumentów typu służy do tworzenia wystąpienia szablony `lock_guard` i `unique_lock`. Za pomocą obiektów tego typu jako `Lock` argument do funkcji Członkowskich oczekiwania w szablonie [condition_variable_any —](../standard-library/condition-variable-any-class.md).

A *upłynął typu obiektu mutex* spełnia wymagania dotyczące typu obiektu mutex. Ponadto ma `try_lock_for` i `try_lock_until` metody, które muszą być wywoływane przy użyciu jednego argumentu i musi zwracać typ, który można przekonwertować na typ `bool`. Typ obiektu mutex czasu można zdefiniować te funkcje przy użyciu dodatkowe argumenty, pod warunkiem, że te dodatkowe wszystkie argumenty mają przypisane wartości domyślne.

- `try_lock_for` Metoda musi być można wywołać za pomocą jednego argumentu `Rel_time`, którego typ jest instancją typu [chrono::duration](../standard-library/duration-class.md). Metoda próbuje uzyskać prawo własności obiektu mutex, ale zwraca przed upływem czasu określony przez `Rel_time`bez względu na powodzenie. Konwertuje wartość zwracaną `true` Jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracaną konwertuje `false`.

- `try_lock_until` Metoda musi być można wywołać za pomocą jednego argumentu `Abs_time`, którego typ jest instancją typu [chrono::time_point](../standard-library/time-point-class.md). Metoda próbuje uzyskać prawo własności obiektu mutex, ale zwraca nie później niż czas, który jest wskazywany przez `Abs_time`bez względu na powodzenie. Konwertuje wartość zwracaną `true` Jeśli metoda uzyskuje własność; w przeciwnym razie wartość zwracaną konwertuje `false`.

Typ obiektu mutex jest także znana jako *zamykane typu*. Jeśli nie zawiera funkcji członkowskiej `try_lock`, jest *podstawowy typ zamykane*. Typ obiektu mutex czasu jest także znana jako *upłynął zamykane typu*.

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[lock_guard, klasa](../standard-library/lock-guard-class.md)|Reprezentuje szablon, który można wdrożyć do utworzenia obiektu, którego destruktora odblokowuje `mutex`.|
|[mutex, klasa (Standardowa biblioteka C++)](../standard-library/mutex-class-stl.md)|Reprezentuje typ obiektu mutex. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenie w programie.|
|[recursive_mutex, klasa](../standard-library/recursive-mutex-class.md)|Reprezentuje typ obiektu mutex. W constrast do `mutex` klasy, zachowanie dla obiektów, które są już zablokowane podczas wywoływania metody blokowania jest dobrze zdefiniowany.|
|[recursive_timed_mutex, klasa](../standard-library/recursive-timed-mutex-class.md)|Reprezentuje typ obiektu mutex czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenie, który ma czas blokowania w programie. W przeciwieństwie do obiektów typu `timed_mutex`, efekt podczas wywoływania metody blokowania `recursive_timed_mutex` obiektów jest dobrze zdefiniowany.|
|[timed_mutex, klasa](../standard-library/timed-mutex-class.md)|Reprezentuje typ obiektu mutex czasu. Użyj obiektów tego typu, aby wymusić wzajemne wykluczenie, który ma czas blokowania w programie.|
|[unique_lock, klasa](../standard-library/unique-lock-class.md)|Reprezentuje szablon, który można wdrożyć do tworzenia obiektów, które zarządzają blokowanie i odblokowywanie `mutex`.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[call_once](../standard-library/mutex-functions.md#call_once)|Udostępnia mechanizm wywoływania dokładnie raz określony obiekt można wywołać podczas wykonywania.|
|[lock](../standard-library/mutex-functions.md#lock)|Próbuje zablokować wszystkie argumenty bez zakleszczenia.|

### <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[adopt_lock_t, struktura](../standard-library/adopt-lock-t-structure.md)|Reprezentuje typ, który służy do definiowania `adopt_lock`.|
|[defer_lock_t, struktura](../standard-library/defer-lock-t-structure.md)|Reprezentuje typ, który definiuje `defer_lock` obiekt, który umożliwia wybranie jednego z konstruktorów przeciążone `unique_lock`.|
|[once_flag, struktura](../standard-library/once-flag-structure.md)|Reprezentuje `struct` używany przy użyciu funkcji szablonu `call_once` aby upewnić się, że inicjowania kodu zostanie wywołana tylko raz, nawet w obecności wielu wątków wykonywania.|
|[try_to_lock_t, struktura](../standard-library/try-to-lock-t-structure.md)|Reprezentuje `struct` definiuje `try_to_lock` obiektu i umożliwia wybranie jednego z konstruktorów przeciążone `unique_lock`.|

### <a name="variables"></a>Zmienne

|Nazwa|Opis|
|----------|-----------------|
|[adopt_lock](../standard-library/mutex-functions.md#adopt_lock)|Reprezentuje obiekt, który może być przekazane do konstruktorów dla `lock_guard` i `unique_lock` aby wskazać, że obiektu mutex, który również jest przekazywany do konstruktora jest zablokowany.|
|[defer_lock —](../standard-library/mutex-functions.md#defer_lock)|Reprezentuje obiekt, który może zostać przekazany do konstruktora dla `unique_lock`, aby wskazać, że konstruktora nie powinna zablokować obiektu mutex, który również jest przekazywany do niego.|
|[try_to_lock](../standard-library/mutex-functions.md#try_to_lock)|Reprezentuje obiekt, który może zostać przekazany do konstruktora dla `unique_lock` wskazująca, czy konstruktora należy dążyć do odblokowania `mutex` który jest również przekazywany do niego bez blokowania.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
