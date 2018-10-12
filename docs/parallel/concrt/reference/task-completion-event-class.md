---
title: task_completion_event — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 867f94cd290e6b8ee5f9e50b266b0e4c9df63adf
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163260"
---
# <a name="taskcompletionevent-class"></a>task_completion_event — Klasa

`task_completion_event` Klasa umożliwia opóźnienie wykonania zadania, dopóki nie zostanie spełniony jakiś warunek, lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.

## <a name="syntax"></a>Składnia

```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

#### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ wyniku `task_completion_event` klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task_completion_event](#ctor)|Konstruuje `task_completion_event` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[set](#set)|Przeciążone. Ustawia zdarzenie zakończenia zadania.|
|[set_exception](#set_exception)|Przeciążone. Propaguje wyjątek wszystkie zadań skojarzonych z tym zdarzeniem.|

## <a name="remarks"></a>Uwagi

Użyj zadania utworzonego z zdarzenie zakończenia zadania w przypadku danego scenariusza należy utworzyć zadanie, które zostanie ukończone, a tym samym mają jego kontynuacje zostaną zaplanowane do wykonania w pewnym momencie w przyszłości. `task_completion_event` Muszą mieć taki sam jak zadania, tworzenie i wywoływanie metody set na zdarzenie zakończenia zadania z wartością tego typu będą spowodować zakończenie zadania skojarzonego i w efekcie dostarczy tę wartość do jego kontynuacji.

Jeśli nigdy nie jest sygnalizowane zdarzenie zakończenia zadania, każde zadanie utworzone na jego podstawie zostanie anulowane, gdy jest usuwane.

`task_completion_event` zachowuje się jak inteligentny wskaźnik i powinien być przekazywany przez wartość.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task_completion_event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks.h

**Namespace:** współbieżności

##  <a name="set"></a> Zestaw

Ustawia zdarzenie zakończenia zadania.

```
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>Parametry

*_Result*<br/>
Wynik, który ma ustawione to zdarzenie z.

### <a name="return-value"></a>Wartość zwracana

Metoda ta zwraca **true** Jeśli pomyślnie ustawiła zdarzenie. Zwraca **false** Jeśli zdarzenie jest już ustawiona.

### <a name="remarks"></a>Uwagi

Obecności wielu lub współbieżnych wywołań `set`, tylko pierwsze wywołanie zostanie wykonane pomyślnie i jego wynik (jeśli istnieje), które będą przechowywane na zdarzenie zakończenia zadania. Pozostałe zestawy są ignorowane, a metoda zwróci wartość false. Po ustawieniu zdarzenia zakończenia zadania, wszystkie zadania utworzone na podstawie że zdarzenia zostaną natychmiast ukończone, a jego kontynuacje, jeśli istnieje, zostanie zaplanowana. Obiekty ukończenia, które mają zadań `_ResultType` innych niż **void** przekazują wartość do ich kontynuacji.

##  <a name="set_exception"></a> set_exception

Propaguje wyjątek wszystkie zadań skojarzonych z tym zdarzeniem.

```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>Parametry

*_E*<br/>
Typ wyjątku.

*_Except*<br/>
Wyjątek, aby ustawić.

*_ExceptionPtr*<br/>
Wskaźnik wyjątek, aby ustawić.

### <a name="return-value"></a>Wartość zwracana

##  <a name="ctor"></a> task_completion_event —

Konstruuje `task_completion_event` obiektu.

```
task_completion_event();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
