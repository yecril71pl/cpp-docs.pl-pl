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
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422186"
---
# <a name="currentscheduler-class"></a>CurrentScheduler — Klasa

Reprezentuje abstrakcję bieżącego harmonogramu skojarzonego z kontekstem wywołującym.

## <a name="syntax"></a>Składnia

```cpp
class CurrentScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Tworzenie](#create)|Tworzy nowy harmonogram, którego zachowanie jest opisane przez parametr `_Policy` i dołącza go do kontekstu wywołującego. Nowo utworzony harmonogram stanie się bieżącym harmonogramem dla kontekstu wywołującego.|
|[CreateScheduleGroup —](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramu w ramach harmonogramu skojarzonego z kontekstem wywołującym. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w nowo utworzonej grupie harmonogramu zostaną rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.|
|[Detach](#detach)|Odłącza bieżący harmonogram od kontekstu wywołującego i przywraca poprzednio dołączony harmonogram jako bieżący harmonogram, jeśli taki istnieje. Po powrocie tej metody kontekst wywołujący jest następnie zarządzany przez harmonogram, który został wcześniej dołączony do kontekstu przy użyciu metody `CurrentScheduler::Create` lub `Scheduler::Attach`.|
|[Get](#get)|Zwraca wskaźnik do harmonogramu skojarzonego z kontekstem wywołującym, nazywany również bieżącym harmonogramem.|
|[GetNumberOfVirtualProcessors —](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu skojarzonego z kontekstem wywoływania.|
|[GetPolicy —](#getpolicy)|Zwraca kopię zasad, za pomocą której został utworzony bieżący harmonogram.|
|[Identyfikator](#id)|Zwraca unikatowy identyfikator dla bieżącego harmonogramu.|
|[IsAvailableLocation —](#isavailablelocation)|Określa, czy dana lokalizacja jest dostępna w bieżącym harmonogramie.|
|[RegisterShutdownEvent —](#registershutdownevent)|Powoduje, że dojście zdarzenia systemu Windows przeszedł do `_ShutdownEvent` parametru, gdy harmonogram skojarzony z bieżącym kontekstem zostanie zamknięty i zniszczy sam siebie. W momencie zasygnalizowania zdarzenia wszystkie prace, które zostały zaplanowane do harmonogramu, zostały ukończone. W tej metodzie można zarejestrować wiele zdarzeń zamknięcia.|
|[ScheduleTask —](#scheduletask)|Przeciążone. Planuje zadanie lekkiej wagi w ramach harmonogramu skojarzonego z kontekstem wywołującym. Uproszczone zadanie zostanie umieszczone w grupie harmonogramu określonej przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w określonej lokalizacji.|

## <a name="remarks"></a>Uwagi

Jeśli nie ma żadnego harmonogramu (zobacz [Scheduler](scheduler-class.md)) skojarzonego z kontekstem wywołującym, wiele metod w klasie `CurrentScheduler` spowoduje zamocowanie domyślnego harmonogramu procesu. Może to również oznaczać, że podczas takiego wywołania jest tworzony harmonogram domyślny procesu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CurrentScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="create"></a>Create

Tworzy nowy harmonogram, którego zachowanie jest opisane przez parametr `_Policy` i dołącza go do kontekstu wywołującego. Nowo utworzony harmonogram stanie się bieżącym harmonogramem dla kontekstu wywołującego.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zasady harmonogramu opisujące zachowanie nowo utworzonego harmonogramu.

### <a name="remarks"></a>Uwagi

Dołączenie harmonogramu do kontekstu wywołującego niejawnie umieszcza liczbę odwołań w harmonogramie.

Po utworzeniu harmonogramu przy użyciu metody `Create` należy wywołać metodę [CurrentScheduler::D etach](#detach) w pewnym momencie w przyszłości, aby można było wyłączyć harmonogram.

Jeśli ta metoda jest wywoływana z kontekstu, który jest już dołączony do innego harmonogramu, istniejący harmonogram zostanie zapamiętany jako poprzedni harmonogram, a nowo utworzony harmonogram będzie bieżącym harmonogramem. Gdy wywołasz metodę `CurrentScheduler::Detach` w późniejszym czasie, poprzedni harmonogram zostanie przywrócony jako bieżący harmonogram.

Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>CreateScheduleGroup —

Tworzy nową grupę harmonogramu w ramach harmonogramu skojarzonego z kontekstem wywołującym. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w nowo utworzonej grupie harmonogramu zostaną rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odwołanie do lokalizacji, w której będą wykonywane zadania w grupie harmonogramu.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonej grupy harmonogramów. Ten obiekt `ScheduleGroup` ma umieszczaną początkową liczbę odwołań.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

Należy wywołać metodę [Release](schedulegroup-class.md#release) w grupie harmonogramu, gdy planujesz do niej prace. Harmonogram będzie niszczył grupę harmonogramu, gdy cała praca w kolejce do niej została zakończona.

Należy pamiętać, że jeśli ten harmonogram został jawnie utworzony, należy zwolnić wszystkie odwołania do grup zaplanowanych w ramach tego harmonogramu przed zwolnieniem odwołania do harmonogramu przez odłączenie bieżącego kontekstu od niego.

## <a name="detach"></a>Ekran

Odłącza bieżący harmonogram od kontekstu wywołującego i przywraca poprzednio dołączony harmonogram jako bieżący harmonogram, jeśli taki istnieje. Po powrocie tej metody kontekst wywołujący jest następnie zarządzany przez harmonogram, który został wcześniej dołączony do kontekstu przy użyciu metody `CurrentScheduler::Create` lub `Scheduler::Attach`.

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>Uwagi

Metoda `Detach` niejawnie usuwa liczbę odwołań z harmonogramu.

Jeśli nie ma żadnego harmonogramu dołączonego do kontekstu wywołującego, wywołanie tej metody spowoduje wyjątek [scheduler_not_attached](scheduler-not-attached-class.md) .

Wywołanie tej metody z kontekstu, który jest wewnętrzny i zarządzany przez harmonogram lub kontekst, który został dołączony przy użyciu metody innej niż [Scheduler:: Attach](scheduler-class.md#attach) lub [CurrentScheduler:: Create](#create) , spowoduje zgłoszenie wyjątku [improper_scheduler_detach](improper-scheduler-detach-class.md) .

## <a name="get"></a>Pobierz

Zwraca wskaźnik do harmonogramu skojarzonego z kontekstem wywołującym, nazywany również bieżącym harmonogramem.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do harmonogramu skojarzony z kontekstem wywoływania (bieżący harmonogram).

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym. Żadne dodatkowe odwołanie nie jest umieszczane w obiekcie `Scheduler` zwróconym przez tę metodę.

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors —

Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu skojarzonego z kontekstem wywoływania.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli harmonogram jest skojarzony z kontekstem wywołującym, bieżąca liczba procesorów wirtualnych dla tego harmonogramu; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Ta metoda nie będzie skutkować załącznikiem harmonogramu, jeśli kontekst wywołujący nie jest już skojarzony z harmonogramem.

Wartość zwracana z tej metody jest chwilową próbką liczby procesorów wirtualnych dla harmonogramu skojarzonego z kontekstem wywołującym. Ta wartość może być nieaktualna w momencie zwrócenia.

## <a name="getpolicy"></a>GetPolicy —

Zwraca kopię zasad, za pomocą której został utworzony bieżący harmonogram.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Wartość zwrócona

Kopia zasad, za pomocą których utworzono bieżący harmonogram.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

## <a name="id"></a>#

Zwraca unikatowy identyfikator dla bieżącego harmonogramu.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli harmonogram jest skojarzony z kontekstem wywołującym, unikatowym identyfikatorem tego harmonogramu; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Ta metoda nie będzie skutkować załącznikiem harmonogramu, jeśli kontekst wywołujący nie jest już skojarzony z harmonogramem.

## <a name="isavailablelocation"></a>IsAvailableLocation —

Określa, czy dana lokalizacja jest dostępna w bieżącym harmonogramie.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odwołanie do lokalizacji, w której ma zostać wyszukiwany bieżący harmonogram.

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy lokalizacja określona przez argument `_Placement` jest dostępna w bieżącym harmonogramie.

### <a name="remarks"></a>Uwagi

Ta metoda nie będzie skutkować załącznikiem harmonogramu, jeśli kontekst wywołujący nie jest już skojarzony z harmonogramem.

Zwróć uwagę, że wartość zwracana to chwilowe próbkowanie, czy dana lokalizacja jest dostępna. W obecności wielu harmonogramów dynamiczne zarządzanie zasobami może dodawać lub odrzucać zasoby od harmonogramów w dowolnym momencie. W takim przypadku dana lokalizacja może zmienić dostępność.

## <a name="registershutdownevent"></a>RegisterShutdownEvent —

Powoduje, że dojście zdarzenia systemu Windows przeszedł do `_ShutdownEvent` parametru, gdy harmonogram skojarzony z bieżącym kontekstem zostanie zamknięty i zniszczy sam siebie. W momencie zasygnalizowania zdarzenia wszystkie prace, które zostały zaplanowane do harmonogramu, zostały ukończone. W tej metodzie można zarejestrować wiele zdarzeń zamknięcia.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Parametry

*_ShutdownEvent*<br/>
Dojście do obiektu zdarzenia systemu Windows, które zostanie zasygnalizowane przez środowisko uruchomieniowe, gdy harmonogram skojarzony z bieżącym kontekstem zostanie zamknięty i zniszczy siebie.

### <a name="remarks"></a>Uwagi

Jeśli nie ma żadnego harmonogramu dołączonego do kontekstu wywołującego, wywołanie tej metody spowoduje wyjątek [scheduler_not_attached](scheduler-not-attached-class.md) .

## <a name="scheduletask"></a>ScheduleTask —

Planuje zadanie lekkiej wagi w ramach harmonogramu skojarzonego z kontekstem wywołującym. Uproszczone zadanie zostanie umieszczone w grupie harmonogramu określonej przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w określonej lokalizacji.

```cpp
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
Wskaźnik do funkcji, która ma zostać wykonana, aby wykonać treść zadania o lekkim średnim poziomie.

*_Data*<br/>
Wskaźnik void do danych, które zostaną przesłane jako parametr do treści zadania.

*_Placement*<br/>
Odwołanie do lokalizacji, w której zostanie obciążone zadanie lekkiej wagi.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje utworzenie i/lub dołączenie domyślnego harmonogramu procesu do kontekstu wywołującego, jeśli aktualnie nie istnieje żaden harmonogram skojarzony z kontekstem wywołującym.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
