---
title: task_completion_event — Klasa
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: b63e8c6986508806cedc8c094a4e8844491dd2fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219512"
---
# <a name="task_completion_event-class"></a>task_completion_event — Klasa

`task_completion_event`Klasa pozwala opóźnić wykonywanie zadania do momentu spełnienia warunku lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.

## <a name="syntax"></a>Składnia

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ wyniku tej `task_completion_event` klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_completion_event](#ctor)|Konstruuje `task_completion_event` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[zbiór](#set)|Przeciążone. Ustawia zdarzenie ukończenia zadania.|
|[set_exception](#set_exception)|Przeciążone. Propaguje wyjątek do wszystkich zadań skojarzonych z tym zdarzeniem.|

## <a name="remarks"></a>Uwagi

Użyj zadania utworzonego na podstawie zdarzenia ukończenia zadania, gdy scenariusz wymaga utworzenia zadania, które zostanie ukończone, a tym samym zaplanowano kontynuację wykonywania w pewnym momencie w przyszłości. `task_completion_event`Musi mieć ten sam typ co zadanie, które tworzysz, i wywołanie metody Set dla zdarzenia ukończenia zadania o wartości tego typu spowoduje zakończenie skojarzonego zadania i podanie tej wartości w wyniku kontynuacji.

Jeśli zdarzenie ukończenia zadania nigdy nie zostanie sygnalizowane, wszystkie zadania utworzone na podstawie tego zdarzenia zostaną anulowane po jego zarejestrowaniu.

`task_completion_event`zachowuje się jak inteligentny wskaźnik i powinny być przesyłane przez wartość.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_completion_event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks. h

**Przestrzeń nazw:** współbieżność

## <a name="set"></a><a name="set"></a>zbiór

Ustawia zdarzenie ukończenia zadania.

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parametry

*_Result*<br/>
Wynik do ustawienia dla tego zdarzenia.

### <a name="return-value"></a>Wartość zwracana

Metoda zwraca, **`true`** Jeśli zakończyło się pomyślnie podczas ustawiania zdarzenia. Zwraca **`false`** , jeśli zdarzenie jest już ustawione.

### <a name="remarks"></a>Uwagi

W obecności wielu lub współbieżnych wywołań do `set` , tylko pierwsze wywołanie powiedzie się, a jego wynik (jeśli istnieje) będzie przechowywany w zdarzeniu ukończenia zadania. Pozostałe zestawy są ignorowane, a metoda zwróci wartość false. Po ustawieniu zdarzenia ukończenia zadania wszystkie zadania utworzone na podstawie tego zdarzenia zostaną wykonane natychmiast, a jego kontynuacje (jeśli istnieją) zostaną zaplanowane. Obiekty uzupełniania zadań, które mają `_ResultType` inne niż **`void`** przekazują wartość do ich kontynuacji.

## <a name="set_exception"></a><a name="set_exception"></a>set_exception

Propaguje wyjątek do wszystkich zadań skojarzonych z tym zdarzeniem.

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parametry

*_E*<br/>
Typ wyjątku.

*_Except*<br/>
Wyjątek do ustawienia.

*_ExceptionPtr*<br/>
Wskaźnik wyjątku do ustawienia.

### <a name="return-value"></a>Wartość zwracana

## <a name="task_completion_event"></a><a name="ctor"></a>task_completion_event

Konstruuje `task_completion_event` obiekt.

```cpp
task_completion_event();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
