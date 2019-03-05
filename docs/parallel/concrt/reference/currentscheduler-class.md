---
title: CurrentScheduler — Klasa
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: a27ec7c25962b6addd26e61af8f33130d4c653ba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326793"
---
# <a name="currentscheduler-class"></a>CurrentScheduler — Klasa

Reprezentuje klasą abstrakcyjną dla bieżącego harmonogramu skojarzony kontekst wywołania.

## <a name="syntax"></a>Składnia

```
class CurrentScheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Tworzenie](#create)|Tworzy nowy harmonogram, którego zachowanie jest opisana przez `_Policy` parametru i dołącza go do wywoływania kontekstu. Nowo utworzony harmonogram staną się bieżący harmonogram Kontekst wywołania.|
|[CreateScheduleGroup](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramów w obrębie harmonogramu, skojarzony kontekst wywołania. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w ramach grupy nowo utworzony harmonogram ukierunkowane wykonywania w lokalizacji określonej w tym parametrze.|
|[Detach](#detach)|Odłącza bieżącego harmonogramu z Kontekst wywołania i przywraca wcześniej dołączone harmonogram jako bieżącego harmonogramu, jeśli taka istnieje. Po powrocie z tej metody Kontekst wywołania jest wtedy zarządzana przez harmonogram, który wcześniej został dołączony do kontekstu przy użyciu `CurrentScheduler::Create` lub `Scheduler::Attach` metody.|
|[Get](#get)|Zwraca wskaźnik do harmonogramu skojarzony kontekst wywołania, nazywana także bieżącego harmonogramu.|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu skojarzony kontekst wywołania.|
|[GetPolicy](#getpolicy)|Zwraca kopię obiektu zasady, które utworzono bieżącego harmonogramu.|
|[Identyfikator](#id)|Zwraca unikatowy identyfikator dla bieżącego harmonogramu.|
|[IsAvailableLocation](#isavailablelocation)|Określa, czy w danej lokalizacji dostępnej bieżącego harmonogramu.|
|[RegisterShutdownEvent](#registershutdownevent)|Powoduje, że dojście zdarzenia Windows przekazanej `_ShutdownEvent` parametr ma być zasygnalizowany, gdy harmonogram skojarzone z bieżącym kontekstem zamyka i niszczy sam. Na czas, który jest sygnalizowane zdarzenie cała praca, który miał została zaplanowana do harmonogramu jest ukończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.|
|[Scheduletask —](#scheduletask)|Przeciążone. Planuje pharmonogramy zadań wagi lekkiej w obrębie harmonogramu, skojarzony kontekst wywołania. Pharmonogramy zadań wagi lekkiej zostaną umieszczone w grupie harmonogram ustalany w czasie wykonywania. Wersja, która przyjmuje parametr `_Placement` powoduje zadania ukierunkowane wykonywanie w określonej lokalizacji.|

## <a name="remarks"></a>Uwagi

W przypadku harmonogramu nie (zobacz [harmonogramu](scheduler-class.md)) skojarzony kontekst wywołania wiele metod w obrębie `CurrentScheduler` załącznika procesu domyślnego harmonogramu spowoduje klasy. To może również oznaczać, że procesu domyślnego harmonogramu jest tworzony podczas tych wywołań.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CurrentScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="create"></a> Utwórz

Tworzy nowy harmonogram, którego zachowanie jest opisana przez `_Policy` parametru i dołącza go do wywoływania kontekstu. Nowo utworzony harmonogram staną się bieżący harmonogram Kontekst wywołania.

```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zasadę harmonogram, który opisuje zachowanie nowo utworzonego harmonogramu.

### <a name="remarks"></a>Uwagi

Dołączanie usługi scheduler do Kontekst wywołania niejawnie umieszcza licznik odwołań w harmonogramie.

Po utworzeniu harmonogramu `Create` metody, należy wywołać [currentscheduler::detach —](#detach) metody w pewnym momencie w przyszłości w celu umożliwienia harmonogramu zamknąć.

Jeśli ta metoda jest wywoływana z kontekstu, który jest już dołączony do różnych harmonogramu jako poprzedniego harmonogramu zapamiętywane jest istniejący harmonogram, a nowo utworzony harmonogram staje się bieżącego harmonogramu. Gdy wywołujesz `CurrentScheduler::Detach` metodę w późniejszym czasie, poprzednie harmonogramu jest przywracane jako bieżącego harmonogramu.

Ta metoda może zgłosić różnych wyjątków, łącznie z [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

##  <a name="createschedulegroup"></a> Createschedulegroup —

Tworzy nową grupę harmonogramów w obrębie harmonogramu, skojarzony kontekst wywołania. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w ramach grupy nowo utworzony harmonogram ukierunkowane wykonywania w lokalizacji określonej w tym parametrze.

```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadania należące do grupy harmonogramu będzie można ukierunkowane wykonywanie w.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego harmonogramu grupy. To `ScheduleGroup` obiekt ma liczbą początkowej odwołania dla niej.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

Należy wywołać [wersji](schedulegroup-class.md#release) metody grupy harmonogramu, po zakończeniu planowania pracy do niego. Harmonogram spowoduje zniszczenie harmonogramu grupy, gdy cała praca w kolejce do niego zostało zakończone.

Należy pamiętać, że jeśli w sposób jawny nie utworzył ten harmonogram, trzeba zwolnić wszystkie odwołania do planowania grup, to przed publikacją której można się odwołać w harmonogramie, odłączając bieżącego kontekstu z niego.

##  <a name="detach"></a> Detach

Odłącza bieżącego harmonogramu z Kontekst wywołania i przywraca wcześniej dołączone harmonogram jako bieżącego harmonogramu, jeśli taka istnieje. Po powrocie z tej metody Kontekst wywołania jest wtedy zarządzana przez harmonogram, który wcześniej został dołączony do kontekstu przy użyciu `CurrentScheduler::Create` lub `Scheduler::Attach` metody.

```
static void __cdecl Detach();
```

### <a name="remarks"></a>Uwagi

`Detach` Metody powoduje niejawne usunięcie liczby odwołań z harmonogramu.

Jeśli nie ma żadnych harmonogramu dołączyć do kontekstu wywołania, wywołanie tej metody spowoduje [scheduler_not_attached —](scheduler-not-attached-class.md) zgłaszanego wyjątku.

Wywołanie tej metody z kontekstu jest wewnętrznym i zarządzane przez harmonogram i kontekst, który został dołączony przy użyciu metody innej niż [Scheduler::attach —](scheduler-class.md#attach) lub [currentscheduler::CREATE —](#create) metod spowoduje [improper_scheduler_detach —](improper-scheduler-detach-class.md) zgłaszanego wyjątku.

##  <a name="get"></a> Pobierz

Zwraca wskaźnik do harmonogramu skojarzony kontekst wywołania, nazywana także bieżącego harmonogramu.

```
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do harmonogramu skojarzony kontekst wywołania (bieżącego harmonogramu).

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania. Brak dodatkowych odwołania jest umieszczany na `Scheduler` obiektu zwróconego przez tę metodę.

##  <a name="getnumberofvirtualprocessors"></a> Getnumberofvirtualprocessors —

Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu skojarzony kontekst wywołania.

```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli harmonogram jest skojarzony z Kontekst wywołania bieżącą liczbę procesorów wirtualnych dla tego harmonogramu; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Ta metoda nie powoduje załącznika harmonogram, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.

Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania, liczby procesorów wirtualnych dla harmonogramu skojarzony kontekst wywołania. Ta wartość może być nieaktualne moment, który jest zwracany.

##  <a name="getpolicy"></a> GetPolicy

Zwraca kopię obiektu zasady, które utworzono bieżącego harmonogramu.

```
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Wartość zwracana

Kopię bieżącego harmonogramu utworzony za pomocą zasad.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

##  <a name="id"></a> Id

Zwraca unikatowy identyfikator dla bieżącego harmonogramu.

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli harmonogram jest skojarzony z Kontekst wywołania Unikatowy identyfikator dla tego harmonogramu; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Ta metoda nie powoduje załącznika harmonogram, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.

##  <a name="isavailablelocation"></a> Isavailablelocation —

Określa, czy w danej lokalizacji dostępnej bieżącego harmonogramu.

```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, aby zbadać bieżącego harmonogramu o.

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy lokalizacja jest określona przez `_Placement` argument jest dostępny na bieżącego harmonogramu.

### <a name="remarks"></a>Uwagi

Ta metoda nie powoduje załącznika harmonogram, jeśli kontekst wywołania nie jest już skojarzony z harmonogramu.

Należy pamiętać, że wartość zwracana jest natychmiastowe próbkowania, czy dostępna jest danej lokalizacji. W obecności wielu harmonogramów dynamiczne zarządzanie zasobami można dodawać lub usuwanie zasobów z transfery danych w dowolnym momencie. Powinno się to zdarzyć danej lokalizacji można zmienić dostępności.

##  <a name="registershutdownevent"></a> Registershutdownevent —

Powoduje, że dojście zdarzenia Windows przekazanej `_ShutdownEvent` parametr ma być zasygnalizowany, gdy harmonogram skojarzone z bieżącym kontekstem zamyka i niszczy sam. Na czas, który jest sygnalizowane zdarzenie cała praca, który miał została zaplanowana do harmonogramu jest ukończona. Za pomocą tej metody można zarejestrować wiele zdarzeń zamknięcia systemu.

```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Parametry

*_ShutdownEvent*<br/>
Dojście do obiektu zdarzeń Windows, który zostanie zasygnalizowane przez środowisko uruchomieniowe gdy harmonogram skojarzone z bieżącym kontekstem zamyka i niszczy sam.

### <a name="remarks"></a>Uwagi

Jeśli nie ma żadnych harmonogramu dołączyć do kontekstu wywołania, wywołanie tej metody spowoduje [scheduler_not_attached —](scheduler-not-attached-class.md) zgłaszanego wyjątku.

##  <a name="scheduletask"></a> Scheduletask —

Planuje pharmonogramy zadań wagi lekkiej w obrębie harmonogramu, skojarzony kontekst wywołania. Pharmonogramy zadań wagi lekkiej zostaną umieszczone w grupie harmonogram ustalany w czasie wykonywania. Wersja, która przyjmuje parametr `_Placement` powoduje zadania ukierunkowane wykonywanie w określonej lokalizacji.

```
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Proc*<br/>
Wskaźnik do funkcji wykonać, aby wykonać treści zadania lekki.

*_Dane*<br/>
Pusty wskaźnik do danych, które zostaną przekazane jako parametr do treści zadania.

*_Umieszczenia.*<br/>
Odwołanie do lokalizacji, w którym zadanie lekkie będzie można ukierunkowane wykonywanie w.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
