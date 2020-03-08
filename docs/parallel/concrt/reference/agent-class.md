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
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882941"
---
# <a name="agent-class"></a>agent — Klasa

Klasa przeznaczona do użycia jako klasa bazowa dla wszystkich niezależnych agentów. Służy do ukrycia stanu od innych agentów i korzystania z przekazywania komunikatów.

## <a name="syntax"></a>Składnia

```cpp
class agent;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Odczynnik](#ctor)|Przeciążone. Konstruuje agenta.|
|[~ Destruktor agenta](#dtor)|Niszczy agenta.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Anuluj](#cancel)|Przenosi agenta ze Stanów `agent_created` lub `agent_runnable` do stanu `agent_canceled`.|
|[start](#start)|Przenosi agenta ze stanu `agent_created` do stanu `agent_runnable` i planuje jego wykonanie.|
|[Stany](#status)|Synchroniczne źródło informacji o stanie od agenta.|
|[status_port](#status_port)|Asynchroniczne źródło informacji o stanie od agenta.|
|[trwa](#wait)|Czeka, aż Agent ukończy zadanie.|
|[wait_for_all](#wait_for_all)|Czeka wszystkim określonym agentom na ukończenie zadań.|
|[wait_for_one](#wait_for_one)|Czeka, aż jeden z określonych agentów ukończy zadanie.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[odbywać](#done)|Przenosi agenta do stanu `agent_done`, wskazując, że Agent został ukończony.|
|[wykonane](#run)|Reprezentuje główne zadanie agenta. `run` powinna zostać przesłonięta w klasie pochodnej i określa, co Agent powinien wykonać po jego uruchomieniu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [agenci asynchroniczni](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`agent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>Odczynnik

Konstruuje agenta.

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie wykonywania agenta.

*_PGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie wykonywania agenta. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PGroup`.

## <a name="dtor"></a>~ Agent

Niszczy agenta.

```cpp
virtual ~agent();
```

### <a name="remarks"></a>Uwagi

Wystąpił błąd podczas niszczenia agenta, który nie znajduje się w stanie terminalu (`agent_done` lub `agent_canceled`). Można to uniknąć, czekając, aż Agent osiągnie stan terminalu w destruktorze klasy, która dziedziczy z klasy `agent`.

## <a name="cancel"></a>Anuluj

Przenosi agenta ze Stanów `agent_created` lub `agent_runnable` do stanu `agent_canceled`.

```cpp
bool cancel();
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli Agent został anulowany, w przeciwnym razie **zwraca wartość false** . Nie można anulować agenta, jeśli został już uruchomiony lub został już ukończony.

## <a name="done"></a>odbywać

Przenosi agenta do stanu `agent_done`, wskazując, że Agent został ukończony.

```cpp
bool done();
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli Agent jest przenoszony do stanu `agent_done`, w przeciwnym razie **false** . Agent, który został anulowany, nie może zostać przeniesiony do stanu `agent_done`.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana na końcu metody `run`, gdy wiadomo, że wykonywanie agenta zakończyło się pomyślnie.

## <a name="run"></a>wykonane

Reprezentuje główne zadanie agenta. `run` powinna zostać przesłonięta w klasie pochodnej i określa, co Agent powinien wykonać po jego uruchomieniu.

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>Uwagi

Stan agenta zostanie zmieniony na `agent_started` bezpośrednio przed wywołaniem tej metody. Metoda powinna wywołać `done` na agencie przy użyciu odpowiedniego stanu przed zwróceniem i może nie generować żadnych wyjątków.

## <a name="start"></a>Start

Przenosi agenta ze stanu `agent_created` do stanu `agent_runnable` i planuje jego wykonanie.

```cpp
bool start();
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli Agent został uruchomiony prawidłowo, w przeciwnym razie **false** . Nie można uruchomić agenta, który został anulowany.

## <a name="status"></a>Stany

Synchroniczne źródło informacji o stanie od agenta.

```cpp
agent_status status();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżący stan agenta. Zwróć uwagę, że ten zwrócony stan może ulec zmianie natychmiast po zwróceniu.

## <a name="status_port"></a>status_port

Asynchroniczne źródło informacji o stanie od agenta.

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca źródło komunikatu, które może wysyłać komunikaty o bieżącym stanie agenta.

## <a name="wait"></a>trwa

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

`agent_status` agenta po zakończeniu oczekiwania. Może to być `agent_canceled` lub `agent_done`.

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu przed ukończeniem zadania przez agenta.

## <a name="wait_for_all"></a>wait_for_all

Czeka wszystkim określonym agentom na ukończenie zadań.

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*count*<br/>
Liczba wskaźników agentów znajdujących się w tablicy `_PAgents`.

*_PAgents*<br/>
Tablica wskaźników do agentów, które mają być oczekiwane.

*_PStatus*<br/>
Wskaźnik do tablicy Stanów agentów. Każda wartość stanu będzie reprezentować stan odpowiedniego agenta, gdy metoda zwraca.

*_Timeout*<br/>
Maksymalny czas oczekiwania (w milisekundach).

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu przed ukończeniem zadania przez agenta.

## <a name="wait_for_one"></a>wait_for_one

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

*count*<br/>
Liczba wskaźników agentów znajdujących się w tablicy `_PAgents`.

*_PAgents*<br/>
Tablica wskaźników do agentów, które mają być oczekiwane.

*_Status*<br/>
Odwołanie do zmiennej, w której zostanie umieszczony stan agenta.

*_Index*<br/>
Odwołanie do zmiennej, w której zostanie umieszczony indeks agenta.

*_Timeout*<br/>
Maksymalny czas oczekiwania (w milisekundach).

### <a name="remarks"></a>Uwagi

Zadanie agenta jest wykonywane, gdy Agent przejdzie do `agent_canceled` lub `agent_done` Stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu przed ukończeniem zadania przez agenta.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
