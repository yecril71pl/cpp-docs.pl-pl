---
title: Klasa harmonogramu
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 1b2b4de2a0aa844f9450af9d853b11ea6f485274
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638272"
---
# <a name="scheduler-class"></a>Klasa harmonogramu

Reprezentuje klasą abstrakcyjną dla harmonogram współbieżność środowiska wykonawczego.

## <a name="syntax"></a>Składnia

```
class Scheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[Harmonogram](#ctor)|Obiekt `Scheduler` klasy można tylko utworzone za pomocą metod fabryki lub niejawnie.|
|[~ Scheduler — destruktor](#dtor)|Obiekt `Scheduler` klasy niejawnie jest niszczony, kiedy wszystkie odwołania zewnętrzne do niego przestaje istnieć.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Attach](#attach)|Dołącza harmonogram Kontekst wywołania. Po powrocie z tej metody Kontekst wywołania odbywa się przez harmonogram i harmonogram staje się bieżącego harmonogramu.|
|[Utwórz](#create)|Tworzy nowy harmonogram, którego zachowanie jest opisana przez `_Policy` parametr, umieszcza odwołaniem początkowego na harmonogram i zwraca wskaźnik do niego.|
|[CreateScheduleGroup](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramów w obrębie harmonogramu. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w ramach grupy nowo utworzony harmonogram ukierunkowane wykonywania w lokalizacji określonej w tym parametrze.|
|[Getnumberofvirtualprocessors —](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.|
|[GetPolicy](#getpolicy)|Zwraca kopię obiektu zasady, które utworzono harmonogram.|
|[Id](#id)|Zwraca unikatowy identyfikator dla harmonogramu.|
|[IsAvailableLocation](#isavailablelocation)|Określa, czy danej lokalizacji jest dostępny w ramach harmonogramu zadań.|
|[Dokumentacja](#reference)|Zwiększa liczbę odwołań harmonogramu.|
|[RegisterShutdownEvent](#registershutdownevent)|Powoduje, że dojście zdarzenia Windows przekazanej `_Event` parametr ma być zasygnalizowany, gdy harmonogram zamyka i niszczy sam. Na czas, który jest sygnalizowane zdarzenie cała praca, który miał została zaplanowana do harmonogramu jest ukończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.|
|[Wersja](#release)|Dekrementuje liczbę odwołań harmonogramu.|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Resetuje domyślne zasady harmonogramu domyślnego środowiska uruchomieniowego. Przy następnym domyślnego harmonogramu zostanie utworzony, zostanie użyty domyślne ustawienia zasad środowiska uruchomieniowego.|
|[Scheduletask —](#scheduletask)|Przeciążone. Planuje pharmonogramy zadań wagi lekkiej w obrębie harmonogramu. Pharmonogramy zadań wagi lekkiej zostaną umieszczone w grupie harmonogram ustalany w czasie wykonywania. Wersja, która przyjmuje parametr `_Placement` powoduje zadania ukierunkowane wykonywanie w określonej lokalizacji.|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Umożliwia zasady zdefiniowane przez użytkownika ma być używany do utworzenia domyślnego harmonogramu. Tę metodę można wywołać tylko wtedy, gdy nie domyślnego harmonogramu istnieje w ramach procesu. Po ustawieniu zasady domyślne on obowiązuje do następnego prawidłowe wywołania metody albo `SetDefaultSchedulerPolicy` lub [resetdefaultschedulerpolicy —](#resetdefaultschedulerpolicy) metody.|

## <a name="remarks"></a>Uwagi

Harmonogram współbieżność środowiska wykonawczego używa kontekstów wykonanie, które mapowania kontekstami wykonywania systemu operacyjnego, takich jak wątek, do wykonanie pracy w kolejce do niego przez daną aplikację. W dowolnym momencie poziom współbieżności harmonogramu jest równa liczbie procesorów wirtualnych przyznanych przez Menedżera zasobów. Procesor wirtualny jest klasą abstrakcyjną dla zasobów przetwarzania i mapuje do wątku sprzętu w systemie podstawowym. Tylko pojedynczy Kontekst harmonogramu można wykonać przy użyciu procesora wirtualnego w danym momencie.

Środowisko uruchomieniowe współbieżności utworzy domyślnego harmonogramu na proces, który można wykonać równoległą pracę. Ponadto można tworzyć własny harmonogram wystąpienia i manipulowania nimi za pomocą tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Scheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="attach"></a> Dołącz

Dołącza harmonogram Kontekst wywołania. Po powrocie z tej metody Kontekst wywołania odbywa się przez harmonogram i harmonogram staje się bieżącego harmonogramu.

```
virtual void Attach() = 0;
```

### <a name="remarks"></a>Uwagi

Dołączanie harmonogramu niejawnie odwołania są umieszczane na harmonogram.

W pewnym momencie w przyszłości, należy wywołać [currentscheduler::detach —](currentscheduler-class.md#detach) metody w celu umożliwienia harmonogramu zamknąć.

Jeśli ta metoda jest wywoływana z kontekstu, który jest już dołączony do różnych harmonogramu jako poprzedniego harmonogramu zapamiętywane jest istniejący harmonogram, a nowo utworzony harmonogram staje się bieżącego harmonogramu. Gdy wywołujesz `CurrentScheduler::Detach` metodę w późniejszym czasie, poprzednie harmonogramu jest przywracane jako bieżącego harmonogramu.

Ta metoda zgłosi [improper_scheduler_attach —](improper-scheduler-attach-class.md) wyjątek, jeśli ten harmonogram jest bieżącego harmonogramu Kontekst wywołania.

##  <a name="create"></a> Utwórz

Tworzy nowy harmonogram, którego zachowanie jest opisana przez `_Policy` parametr, umieszcza odwołaniem początkowego na harmonogram i zwraca wskaźnik do niego.

```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*Zasady _dziennika*<br/>
Zasadę harmonogram, który opisuje zachowanie nowo utworzonego harmonogramu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego harmonogramu. To `Scheduler` obiekt ma liczbą początkowej odwołania dla niej.

### <a name="remarks"></a>Uwagi

Po utworzeniu harmonogramu `Create` metody, należy wywołać `Release` metody w pewnym momencie w przyszłości, aby można było usunąć licznik odwołań początkowej i umożliwić harmonogramu zamknąć.

Harmonogram utworzony przy użyciu tej metody nie jest dołączony do Kontekst wywołania. Może być dołączane za pomocą kontekstu [Dołącz](#attach) metody.

Ta metoda może zgłosić różnych wyjątków, łącznie z [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

##  <a name="createschedulegroup"></a> Createschedulegroup —

Tworzy nową grupę harmonogramów w obrębie harmonogramu. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w ramach grupy nowo utworzony harmonogram ukierunkowane wykonywania w lokalizacji określonej w tym parametrze.

```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadania należące do grupy harmonogramu będą ukierunkowane wykonywanie w.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego harmonogramu grupy. To `ScheduleGroup` obiekt ma liczbą początkowej odwołania dla niej.

### <a name="remarks"></a>Uwagi

Należy wywołać [wersji](schedulegroup-class.md#release) metody grupy harmonogramu, po zakończeniu planowania pracy do niego. Harmonogram spowoduje zniszczenie harmonogramu grupy, gdy cała praca w kolejce do niego zostało zakończone.

Należy pamiętać, że jeśli w sposób jawny nie utworzył ten harmonogram, trzeba zwolnić wszystkie odwołania do planowania grup, to przed publikacją odwołaniami w harmonogramie.

##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors —

Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.

```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba procesorów wirtualnych dla harmonogramu.

##  <a name="getpolicy"></a> GetPolicy

Zwraca kopię obiektu zasady, które utworzono harmonogram.

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Kopia zasady, które utworzono harmonogram.

##  <a name="id"></a> Id

Zwraca unikatowy identyfikator dla harmonogramu.

```
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator dla harmonogramu.

##  <a name="isavailablelocation"></a> Isavailablelocation —

Określa, czy danej lokalizacji jest dostępny w ramach harmonogramu zadań.

```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parametry

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, aby wysłać zapytanie do harmonogramu o.

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy lokalizacja jest określona przez `_Placement` argument jest dostępny w ramach harmonogramu zadań.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że wartość zwracana jest natychmiastowe próbkowania, czy dostępna jest danej lokalizacji. W obecności wielu harmonogramów dynamiczne zarządzanie zasobami można dodawać lub usuwanie zasobów z transfery danych w dowolnym momencie. Powinno się to zdarzyć danej lokalizacji można zmienić dostępności.

##  <a name="reference"></a> Odwołanie

Zwiększa liczbę odwołań harmonogramu.

```
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Wartość zwracana

Licznik odwołań nowo zwiększona.

### <a name="remarks"></a>Uwagi

Służy to zazwyczaj zarządzania okresem istnienia harmonogram dla kompozycji. Gdy licznik odwołań wypada harmonogramu, do zera, harmonogram zostanie zamknięty i destruct sam po wszystkich pracowanie harmonogram zostało zakończone.

Metoda zgłosi [improper_scheduler_reference —](improper-scheduler-reference-class.md) wyjątek, jeśli odwołanie zliczane przed wywołaniem `Reference` metoda była zero i zostanie nawiązane połączenie z kontekstu, które nie jest posiadane przez harmonogram.

##  <a name="registershutdownevent"></a> Registershutdownevent —

Powoduje, że dojście zdarzenia Windows przekazanej `_Event` parametr ma być zasygnalizowany, gdy harmonogram zamyka i niszczy sam. Na czas, który jest sygnalizowane zdarzenie cała praca, który miał została zaplanowana do harmonogramu jest ukończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.

```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parametry

*_Zdarzenia*<br/>
Dojście do obiektu zdarzeń Windows, który zostanie zasygnalizowane przez środowisko uruchomieniowe gdy harmonogram zamyka i niszczy sam.

##  <a name="release"></a> Wydania

Dekrementuje liczbę odwołań harmonogramu.

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Licznik odwołań nowo zmniejszony.

### <a name="remarks"></a>Uwagi

Służy to zazwyczaj zarządzania okresem istnienia harmonogram dla kompozycji. Gdy licznik odwołań wypada harmonogramu, do zera, harmonogram zostanie zamknięty i destruct sam po wszystkich pracowanie harmonogram zostało zakończone.

##  <a name="resetdefaultschedulerpolicy"></a> Resetdefaultschedulerpolicy —

Resetuje domyślne zasady harmonogramu domyślnego środowiska uruchomieniowego. Przy następnym domyślnego harmonogramu zostanie utworzony, zostanie użyty domyślne ustawienia zasad środowiska uruchomieniowego.

```
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać w czasie w ramach procesu domyślnego harmonogramu. Nie zostaną zastosowane zasady istniejący harmonogram domyślny. Jednak jeśli domyślnego harmonogramu zamiar zamknięcia, a nowe rozwiązanie domyślne zostały ma zostać utworzony w dowolnym momencie, nowy harmonogram użyć domyślnych ustawień zasad środowiska uruchomieniowego.

##  <a name="ctor"></a> Harmonogram

Obiekt `Scheduler` klasy można tylko utworzone za pomocą metod fabryki lub niejawnie.

```
Scheduler();
```

### <a name="remarks"></a>Uwagi

Procesu domyślnego harmonogramu są tworzone niejawnie korzystanie z wielu funkcji środowiska uruchomieniowego, które wymagają harmonogramu do podłączenia do Kontekst wywołania. Metody w ramach `CurrentScheduler` klasy i funkcje warstw PPL i agentów zwykle wykonują niejawne załącznika.

Można również utworzyć harmonogram jawnie przy użyciu jednej `CurrentScheduler::Create` metody lub `Scheduler::Create` metody.

##  <a name="dtor"></a> ~ Scheduler

Obiekt `Scheduler` klasy niejawnie jest niszczony, kiedy wszystkie odwołania zewnętrzne do niego przestaje istnieć.

```
virtual ~Scheduler();
```

##  <a name="scheduletask"></a> Scheduletask —

Planuje pharmonogramy zadań wagi lekkiej w obrębie harmonogramu. Pharmonogramy zadań wagi lekkiej zostaną umieszczone w grupie harmonogram ustalany w czasie wykonywania. Wersja, która przyjmuje parametr `_Placement` powoduje zadania ukierunkowane wykonywanie w określonej lokalizacji.

```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Wskaźnik do funkcji wykonać, aby wykonać treści zadania lekki.

*_Dane*<br/>
Pusty wskaźnik do danych, które zostaną przekazane jako parametr do treści zadania.

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadanie lekkie będzie można ukierunkowane wykonywanie w.

##  <a name="setdefaultschedulerpolicy"></a> Setdefaultschedulerpolicy —

Umożliwia zasady zdefiniowane przez użytkownika ma być używany do utworzenia domyślnego harmonogramu. Tę metodę można wywołać tylko wtedy, gdy nie domyślnego harmonogramu istnieje w ramach procesu. Po ustawieniu zasady domyślne on obowiązuje do następnego prawidłowe wywołania metody albo `SetDefaultSchedulerPolicy` lub [resetdefaultschedulerpolicy —](#resetdefaultschedulerpolicy) metody.

```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*Zasady _dziennika*<br/>
Zasady można ustawić jako domyślne zasady usługi scheduler.

### <a name="remarks"></a>Uwagi

Jeśli `SetDefaultSchedulerPolicy` metoda jest wywoływana, gdy domyślnego harmonogramu już istnieje w ramach procesu, środowisko uruchomieniowe wygeneruje [default_scheduler_exists —](default-scheduler-exists-class.md) wyjątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

