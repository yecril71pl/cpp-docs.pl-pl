---
title: Agent — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbc8542af8073b2cb95517ea39d89258afac633c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="agent-class"></a>agent — Klasa
Klasa przeznaczona do użycia jako klasę podstawową dla wszystkich agentów niezależne. Służy do ukrycia stanu z innych agentów i interakcji, przy użyciu przekazywania wiadomości.  
  
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
|[cancel](#cancel)|Przenosi agenta z albo `agent_created` lub `agent_runnable` stany do `agent_canceled` stanu.|  
|[start](#start)|Przenosi agenta z `agent_created` stan `agent_runnable` stanu i harmonogramy wykonywania.|  
|[status](#status)|Synchroniczne źródło informacji o stanie od agenta.|  
|[status_port](#status_port)|Asynchroniczne źródło informacji o stanie od agenta.|  
|[oczekiwania](#wait)|Czeka na agenta zakończy się.|  
|[wait_for_all](#wait_for_all)|Czeka na wszystkich agentów określony do wykonywania swoich zadań.|  
|[wait_for_one](#wait_for_one)|Czeka na jeden z określonych agentów zakończy się.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Gotowe](#done)|Przenosi agenta do `agent_done` stan wskazujący, że agenta zostało ukończone.|  
|[run](#run)|Reprezentuje głównym zadaniem agenta. `run` powinna zostać zastąpiona w klasie pochodnej i określa, jakie działanie ma wykonać agenta po jego uruchomieniu.|  
  
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
 `_PScheduler`  
 `Scheduler` Obiektów w ramach jest zaplanowane wykonanie zadania agenta.  
  
 `_PGroup`  
 `ScheduleGroup` Obiektów w ramach jest zaplanowane wykonanie zadania agenta. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PGroup` parametrów.  
  
##  <a name="dtor"></a> ~ agenta 

 Niszczy agenta.  
  
```
virtual ~agent();
```  
  
### <a name="remarks"></a>Uwagi  
 Występuje błąd do zniszczenia agenta, który nie jest w stanie terminali (albo `agent_done` lub `agent_canceled`). Można tego uniknąć przez oczekiwanie na agenta do przejścia terminali w destruktor klasy, która dziedziczy `agent` klasy.  
  
##  <a name="cancel"></a> Anuluj 

 Przenosi agenta z albo `agent_created` lub `agent_runnable` stany do `agent_canceled` stanu.  
  
```
bool cancel();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli agent został anulowany, `false` inaczej. Nie można anulować agenta, jeśli rozpoczął już uruchomione lub zostało już zakończone.  
  
##  <a name="done"></a> Gotowe 

 Przenosi agenta do `agent_done` stan wskazujący, że agenta zostało ukończone.  
  
```
bool done();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli agent jest przenoszony do `agent_done` stanu, `false` inaczej. Agent został anulowany, nie można przenieść do `agent_done` stanu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powinna być wywoływana na końcu `run` metody, gdy wiesz, wykonywania agenta zostało ukończone.  
  
##  <a name="run"></a> Uruchom 

 Reprezentuje głównym zadaniem agenta. `run` powinna zostać zastąpiona w klasie pochodnej i określa, jakie działanie ma wykonać agenta po jego uruchomieniu.  
  
```
virtual void run() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Stan agenta jest zmieniana na `agent_started` prawym przyciskiem myszy, aby ta metoda jest wywoływana. Należy wywołać metodę `done` agenta ze stanem odpowiednie przed zwróceniem i nie może zgłaszać wyjątki.  
  
##  <a name="start"></a> Początek 

 Przenosi agenta z `agent_created` stan `agent_runnable` stanu i harmonogramy wykonywania.  
  
```
bool start();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli agent został uruchomiony poprawnie, `false` inaczej. Nie można uruchomić agenta, który został anulowany.  
  
##  <a name="status"></a> Stan 

 Synchroniczne źródło informacji o stanie od agenta.  
  
```
agent_status status();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżący stan agenta. Należy pamiętać, że ten stan zwrócony można zmienić bezpośrednio po zostały zwrócone.  
  
##  <a name="status_port"></a> status_port 

 Asynchroniczne źródło informacji o stanie od agenta.  
  
```
ISource<agent_status>* status_port();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca źródła komunikat, który może wysyłać komunikaty o bieżący stan agenta.  
  
##  <a name="wait"></a> oczekiwania 

 Czeka na agenta zakończy się.  
  
```
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `_PAgent`  
 Wskaźnik do agenta oczekiwania.  
  
 `_Timeout`  
 Maksymalny czas, dla którego oczekiwania w milisekundach.  
  
### <a name="return-value"></a>Wartość zwracana  
 `agent_status` Agenta po zakończeniu czas oczekiwania. Może to być `agent_canceled` lub `agent_done`.  
  
### <a name="remarks"></a>Uwagi  
 Zadanie agenta zostało ukończone, po przekroczeniu agenta `agent_canceled` lub `agent_done` stanów.  
  
 Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany po przekroczeniu określoną ilość czasu, zanim agent ukończył zadanie.  
  
##  <a name="wait_for_all"></a> wait_for_all 

 Czeka na wszystkich agentów określony do wykonywania swoich zadań.  
  
```
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba w tablicy wskaźników agenta `_PAgents`.  
  
 `_PAgents`  
 Tablicy wskaźników do agentów oczekiwania.  
  
 `_PStatus`  
 Wskaźnik do tablicy stanów agenta. Wszystkie wartości stanu będzie reprezentować stan odpowiedniego agenta, gdy metoda zwróci wartość.  
  
 `_Timeout`  
 Maksymalny czas, dla którego oczekiwania w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Zadanie agenta zostało ukończone, po przekroczeniu agenta `agent_canceled` lub `agent_done` stanów.  
  
 Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany po przekroczeniu określoną ilość czasu, zanim agent ukończył zadanie.  
  
##  <a name="wait_for_one"></a> wait_for_one 

 Czeka na jeden z określonych agentów zakończy się.  
  
```
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba w tablicy wskaźników agenta `_PAgents`.  
  
 `_PAgents`  
 Tablicy wskaźników do agentów oczekiwania.  
  
 `_Status`  
 Odwołanie do zmiennej rozmieszczenia stan agenta.  
  
 `_Index`  
 Odwołanie do zmiennej rozmieszczenia indeksu agenta.  
  
 `_Timeout`  
 Maksymalny czas, dla którego oczekiwania w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Zadanie agenta zostało ukończone, po przekroczeniu agenta `agent_canceled` lub `agent_done` stanów.  
  
 Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany po przekroczeniu określoną ilość czasu, zanim agent ukończył zadanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
