---
title: agent — Klasa
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f1d98cdc6237f182e0240a85f2fdce3410232195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213895"
---
# <a name="agent-class"></a>agent — Klasa

Klasa przeznaczona do użycia jako klasa bazowa dla wszystkich niezależnych agentów. Służy do ukrycia stanu od innych agentów i korzystania z przekazywania komunikatów.

## <a name="syntax"></a>Składnia

```cpp
class agent;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Odczynnik](#ctor)|Przeciążone. Konstruuje agenta.|
|[~ Destruktor agenta](#dtor)|Niszczy agenta.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|Przenosi agenta z `agent_created` lub `agent_runnable` Stanów do `agent_canceled` stanu.|
|[start](#start)|Przenosi agenta ze `agent_created` stanu do `agent_runnable` stanu i planuje jego wykonanie.|
|[Stany](#status)|Synchroniczne źródło informacji o stanie od agenta.|
|[status_port](#status_port)|Asynchroniczne źródło informacji o stanie od agenta.|
|[trwa](#wait)|Czeka, aż Agent ukończy zadanie.|
|[wait_for_all](#wait_for_all)|Czeka wszystkim określonym agentom na ukończenie zadań.|
|[wait_for_one](#wait_for_one)|Czeka, aż jeden z określonych agentów ukończy zadanie.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[gotowe](#done)|Przenosi agenta do `agent_done` stanu, wskazując, że Agent został ukończony.|
|[wykonane](#run)|Reprezentuje główne zadanie agenta. `run`powinien zostać zastąpiony w klasie pochodnej i określa, co Agent powinien wykonać po jego uruchomieniu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [agenci asynchroniczni](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`agent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="agent"></a><a name="ctor"></a>Odczynnik

Konstruuje agenta.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie wykonywania agenta.

*_PGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie wykonywania agenta. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PGroup` parametrów lub.

## <a name="agent"></a><a name="dtor"></a>~ Agent

Niszczy agenta.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Uwagi

Wystąpił błąd podczas niszczenia agenta, który nie znajduje się w stanie terminalu ( `agent_done` lub `agent_canceled` ). Można to uniknąć, czekając, aż Agent osiągnie stan terminalu w destruktorze klasy, która dziedziczy z `agent` klasy.

## <a name="cancel"></a><a name="cancel"></a>Anuluj

Przenosi agenta z `agent_created` lub `agent_runnable` Stanów do `agent_canceled` stanu.

```cpp
bool cancel();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli Agent został anulowany, **`false`** w przeciwnym razie. Nie można anulować agenta, jeśli został już uruchomiony lub został już ukończony.

## <a name="done"></a><a name="done"></a>odbywać

Przenosi agenta do `agent_done` stanu, wskazując, że Agent został ukończony.

```cpp
bool done();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli Agent jest przenoszony do `agent_done` stanu, **`false`** w przeciwnym razie. Agent, który został anulowany, nie może zostać przeniesiony do `agent_done` stanu.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana na końcu `run` metody, gdy wiadomo, że wykonywanie agenta zakończyło się pomyślnie.

## <a name="run"></a><a name="run"></a>wykonane

Reprezentuje główne zadanie agenta. `run`powinien zostać zastąpiony w klasie pochodnej i określa, co Agent powinien wykonać po jego uruchomieniu.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Uwagi

Stan agenta jest zmieniany na `agent_started` prawidłowy przed wywołaniem tej metody. Metoda powinna zostać wywołana `done` na agencie przy użyciu odpowiedniego stanu przed zwróceniem i może nie generować żadnych wyjątków.

## <a name="start"></a><a name="start"></a>Start

Przenosi agenta ze `agent_created` stanu do `agent_runnable` stanu i planuje jego wykonanie.

```cpp
bool start();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli Agent został uruchomiony prawidłowo, **`false`** w przeciwnym razie. Nie można uruchomić agenta, który został anulowany.

## <a name="status"></a><a name="status"></a>Stany

Synchroniczne źródło informacji o stanie od agenta.

```cpp
agent_status status();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżący stan agenta. Zwróć uwagę, że ten zwrócony stan może ulec zmianie natychmiast po zwróceniu.

## <a name="status_port"></a><a name="status_port"></a>status_port

Asynchroniczne źródło informacji o stanie od agenta.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca źródło komunikatu, które może wysyłać komunikaty o bieżącym stanie agenta.

## <a name="wait"></a><a name="wait"></a>trwa

Czeka, aż Agent ukończy zadanie.

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PAgent*<br/>
Wskaźnik do agenta, dla którego ma zostać odczekanie.

*_Timeout*<br/>
Maksymalny czas oczekiwania (w milisekundach).

### <a name="return-value"></a>Wartość zwracana

`agent_status`Agent po zakończeniu oczekiwania. Może to być `agent_canceled` albo `agent_done` .

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stany.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE` , zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu, zanim Agent ukończy jego zadanie.

## <a name="wait_for_all"></a><a name="wait_for_all"></a>wait_for_all

Czeka wszystkim określonym agentom na ukończenie zadań.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*liczbą*<br/>
Liczba wskaźników agentów znajdujących się w tablicy `_PAgents` .

*_PAgents*<br/>
Tablica wskaźników do agentów, które mają być oczekiwane.

*_PStatus*<br/>
Wskaźnik do tablicy Stanów agentów. Każda wartość stanu będzie reprezentować stan odpowiedniego agenta, gdy metoda zwraca.

*_Timeout*<br/>
Maksymalny czas oczekiwania (w milisekundach).

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stany.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE` , zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu, zanim Agent ukończy jego zadanie.

## <a name="wait_for_one"></a><a name="wait_for_one"></a>wait_for_one

Czeka, aż jeden z określonych agentów ukończy zadanie.

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*liczbą*<br/>
Liczba wskaźników agentów znajdujących się w tablicy `_PAgents` .

*_PAgents*<br/>
Tablica wskaźników do agentów, które mają być oczekiwane.

*_Status*<br/>
Odwołanie do zmiennej, w której zostanie umieszczony stan agenta.

*_Index*<br/>
Odwołanie do zmiennej, w której zostanie umieszczony indeks agenta.

*_Timeout*<br/>
Maksymalny czas oczekiwania (w milisekundach).

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stany.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE` , zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu, zanim Agent ukończy jego zadanie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
