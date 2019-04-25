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
ms.openlocfilehash: 98ad5f817361d8410e5a60648fb23baec06c42d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337755"
---
# <a name="agent-class"></a>agent — Klasa

Klasa przeznaczona do użycia jako klasę bazową dla wszystkich agentów niezależne. Służy do ukrywania stanu z innych agentów i wchodzić w interakcje przy użyciu przekazywania komunikatów.

## <a name="syntax"></a>Składnia

```
class agent;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[agent](#ctor)|Przeciążone. Tworzy agenta.|
|[~ agent — destruktor](#dtor)|Niszczy agenta.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancel](#cancel)|Przenosi agenta z poziomu `agent_created` lub `agent_runnable` stany `agent_canceled` stanu.|
|[start](#start)|Przenosi agenta z `agent_created` do stanu `agent_runnable` stanu i planuje wykonanie.|
|[status](#status)|Synchroniczne źródło informacji o stanie od agenta.|
|[status_port](#status_port)|Asynchroniczne źródło informacji o stanie od agenta.|
|[Czekaj](#wait)|Czeka, aż agenta w celu zakończenia zadania.|
|[wait_for_all](#wait_for_all)|Czeka, aż wszystkie określonego agentów do wykonywania swoich zadań.|
|[wait_for_one](#wait_for_one)|Czeka, aż jeden określony agentów do zakończenia zadania.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Gotowe](#done)|Przenosi agenta do `agent_done` stan, wskazujący, że agenta została ukończona.|
|[run](#run)|Reprezentuje głównego zadania agenta. `run` powinna zostać zastąpiona w klasie pochodnej i określa, co zrobić w agencie po jego uruchomieniu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [agentów asynchronicznych](../../../parallel/concrt/asynchronous-agents.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`agent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="ctor"></a> Agent

Tworzy agenta.

```
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
`Scheduler` Obiektów w ramach jest zaplanowane zadanie wykonywania agenta.

*_PGroup*<br/>
`ScheduleGroup` Obiektów w ramach jest zaplanowane zadanie wykonywania agenta. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PGroup` parametrów.

##  <a name="dtor"></a> ~ agenta

Niszczy agenta.

```
virtual ~agent();
```

### <a name="remarks"></a>Uwagi

Jest to błąd, aby zniszczyć agenta, który nie znajduje się w stan końcowy (albo `agent_done` lub `agent_canceled`). To można uniknąć, oczekiwanie na agenta do osiągnie stan końcowy w destruktor klasy, która dziedziczy po elemencie `agent` klasy.

##  <a name="cancel"></a> Anuluj

Przenosi agenta z poziomu `agent_created` lub `agent_runnable` stany `agent_canceled` stanu.

```
bool cancel();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** jeśli agent został anulowany, **false** inaczej. Nie można anulować agenta, jeśli został już uruchomiony, uruchomiony lub został już ukończony.

##  <a name="done"></a> Gotowe

Przenosi agenta do `agent_done` stan, wskazujący, że agenta została ukończona.

```
bool done();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** jeśli agent jest przenoszony do `agent_done` stanu, **false** inaczej. Nie można przenieść agenta, który został anulowany `agent_done` stanu.

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana na końcu `run` metody, gdy wiadomo, wykonanie agenta została ukończona.

##  <a name="run"></a> Uruchom

Reprezentuje głównego zadania agenta. `run` powinna zostać zastąpiona w klasie pochodnej i określa, co zrobić w agencie po jego uruchomieniu.

```
virtual void run() = 0;
```

### <a name="remarks"></a>Uwagi

Stan agenta jest zmieniana na `agent_started` bezpośrednio przed wywołaniem tej metody. Należy wywołać metodę `done` agenta przy użyciu odpowiedniego stanu przed zwróceniem i może nie generuje żadnych wyjątków.

##  <a name="start"></a> Rozpocznij

Przenosi agenta z `agent_created` do stanu `agent_runnable` stanu i planuje wykonanie.

```
bool start();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** jeśli agent jest uruchomiony prawidłowo, **false** inaczej. Nie można uruchomić agenta, który został anulowany.

##  <a name="status"></a> Stan

Synchroniczne źródło informacji o stanie od agenta.

```
agent_status status();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżący stan agenta. Należy pamiętać o tym, czy ten stan zwrócony można zmienić natychmiast po zwracanego.

##  <a name="status_port"></a> status_port —

Asynchroniczne źródło informacji o stanie od agenta.

```
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca źródło komunikatu, który może wysyłać komunikaty dotyczące bieżącego stanu agenta.

##  <a name="wait"></a> Czekaj

Czeka, aż agenta w celu zakończenia zadania.

```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PAgent*<br/>
Wskaźnik do agenta oczekiwania.

*_Limit czasu*<br/>
Maksymalny czas, dla którego ma zostać oczekiwania w milisekundach.

### <a name="return-value"></a>Wartość zwracana

`agent_status` Agenta po zakończeniu czas oczekiwania. Może to być `agent_canceled` lub `agent_done`.

### <a name="remarks"></a>Uwagi

Zadanie agenta zostało ukończone, gdy agent wprowadza `agent_canceled` lub `agent_done` stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany, jeśli określony przedział czasu upłynie zanim agent ukończył zadanie.

##  <a name="wait_for_all"></a> wait_for_all —

Czeka, aż wszystkie określonego agentów do wykonywania swoich zadań.

```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczbą wskaźników agenta obecnego w tablicy `_PAgents`.

*_PAgents*<br/>
Tablica wskaźników do agentów oczekiwania.

*_PStatus*<br/>
Wskaźnik do tablicy stany agentów. Wszystkie wartości stanu będzie reprezentować stan odpowiedniego agenta, gdy metoda zwróci wartość.

*_Limit czasu*<br/>
Maksymalny czas, dla którego ma zostać oczekiwania w milisekundach.

### <a name="remarks"></a>Uwagi

Zadanie agenta zostało ukończone, gdy agent wprowadza `agent_canceled` lub `agent_done` stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany, jeśli określony przedział czasu upłynie zanim agent ukończył zadanie.

##  <a name="wait_for_one"></a> wait_for_one —

Czeka, aż jeden określony agentów do zakończenia zadania.

```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczbą wskaźników agenta obecnego w tablicy `_PAgents`.

*_PAgents*<br/>
Tablica wskaźników do agentów oczekiwania.

*_Status*<br/>
Odwołanie do zmiennej, w którym zostaną umieszczone stan agenta.

*Parametr _Index*<br/>
Odwołanie do zmiennej, w którym zostaną umieszczone indeksu agenta.

*_Limit czasu*<br/>
Maksymalny czas, dla którego ma zostać oczekiwania w milisekundach.

### <a name="remarks"></a>Uwagi

Zadanie agenta zostało ukończone, gdy agent wprowadza `agent_canceled` lub `agent_done` stanów.

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany, jeśli określony przedział czasu upłynie zanim agent ukończył zadanie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
