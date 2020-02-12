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
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142009"
---
# <a name="scheduler-class"></a>Klasa harmonogramu

Reprezentuje streszczenie dla środowisko uruchomieniowe współbieżności Scheduler.

## <a name="syntax"></a>Składnia

```cpp
class Scheduler;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Scheduler](#ctor)|Obiekt klasy `Scheduler` można utworzyć tylko przy użyciu metod fabrycznych lub niejawnie.|
|[~ Scheduler — destruktor](#dtor)|Obiekt klasy `Scheduler` jest niejawnie niszczony, gdy wszystkie odwołania zewnętrzne przestaną istnieć.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Attach](#attach)|Dołącza harmonogram do kontekstu wywołującego. Po powrocie tej metody kontekst wywołujący jest zarządzany przez harmonogram, a harmonogram stał się bieżącym harmonogramem.|
|[Tworzenie](#create)|Tworzy nowy harmonogram, którego zachowanie jest opisane przez `_Policy` parametru, umieszcza odwołanie początkowe w harmonogramie i zwraca do niego wskaźnik.|
|[CreateScheduleGroup —](#createschedulegroup)|Przeciążone. Tworzy nową grupę harmonogramów w ramach harmonogramu. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w nowo utworzonej grupie harmonogramu zostaną rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.|
|[GetNumberOfVirtualProcessors —](#getnumberofvirtualprocessors)|Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.|
|[GetPolicy —](#getpolicy)|Zwraca kopię zasad, za pomocą której został utworzony harmonogram.|
|[Identyfikator](#id)|Zwraca unikatowy identyfikator dla harmonogramu.|
|[IsAvailableLocation —](#isavailablelocation)|Określa, czy dana lokalizacja jest dostępna w harmonogramie.|
|[Dokumentacja](#reference)|Zwiększa liczbę odwołań harmonogramu.|
|[RegisterShutdownEvent —](#registershutdownevent)|Powoduje, że dojście zdarzenia systemu Windows przeszedł do `_Event` parametru, aby zasygnalizować, gdy harmonogram zostanie zamknięty i zniszczy siebie. W momencie zasygnalizowania zdarzenia wszystkie prace, które zostały zaplanowane do harmonogramu, zostały ukończone. W tej metodzie można zarejestrować wiele zdarzeń zamknięcia.|
|[Wersja](#release)|Zmniejsza liczbę odwołań do harmonogramu.|
|[ResetDefaultSchedulerPolicy —](#resetdefaultschedulerpolicy)|Resetuje domyślne zasady harmonogramu do ustawień domyślnych środowiska uruchomieniowego. Przy następnym utworzeniu domyślnego harmonogramu zostaną użyte domyślne ustawienia zasad środowiska uruchomieniowego.|
|[ScheduleTask —](#scheduletask)|Przeciążone. Planuje zadanie lekkiej wagi w ramach harmonogramu. Uproszczone zadanie zostanie umieszczone w grupie harmonogramu określonej przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w określonej lokalizacji.|
|[SetDefaultSchedulerPolicy —](#setdefaultschedulerpolicy)|Zezwala na użycie zasad zdefiniowanych przez użytkownika do tworzenia domyślnego harmonogramu. Tę metodę można wywołać tylko wtedy, gdy w ramach procesu nie istnieje domyślny harmonogram. Po ustawieniu zasad domyślnych, będzie obowiązywać do następnego prawidłowego wywołania do `SetDefaultSchedulerPolicy` lub metody [ResetDefaultSchedulerPolicy —](#resetdefaultschedulerpolicy) .|

## <a name="remarks"></a>Uwagi

Harmonogram środowisko uruchomieniowe współbieżności używa kontekstów wykonywania, które mapują do kontekstów wykonywania systemu operacyjnego, takich jak wątek, aby wykonać pracę umieszczoną w kolejce przez aplikację. W dowolnym momencie poziom współbieżności harmonogramu jest równy liczbie procesorów wirtualnych przyznanych przez Menedżer zasobów. Procesor wirtualny jest abstrakcją dla zasobu przetwarzania i jest mapowany na wątek sprzętowy w systemie bazowym. Tylko jeden kontekst harmonogramu można wykonać na wirtualnym procesorze w danym momencie.

Środowisko uruchomieniowe współbieżności utworzy domyślny harmonogram dla procesu, aby wykonać pracę równoległą. Ponadto można tworzyć własne wystąpienia usługi Scheduler i manipulować nimi przy użyciu tej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Scheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="attach"></a>Klej

Dołącza harmonogram do kontekstu wywołującego. Po powrocie tej metody kontekst wywołujący jest zarządzany przez harmonogram, a harmonogram stał się bieżącym harmonogramem.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>Uwagi

Dołączenie harmonogramu powoduje niejawnie umieszczenie odwołania w harmonogramie.

W pewnym momencie w przyszłości należy wywołać metodę [CurrentScheduler::D etach](currentscheduler-class.md#detach) , aby można było wyłączyć harmonogram.

Jeśli ta metoda jest wywoływana z kontekstu, który jest już dołączony do innego harmonogramu, istniejący harmonogram zostanie zapamiętany jako poprzedni harmonogram, a nowo utworzony harmonogram będzie bieżącym harmonogramem. Gdy wywołasz metodę `CurrentScheduler::Detach` w późniejszym czasie, poprzedni harmonogram zostanie przywrócony jako bieżący harmonogram.

Ta metoda zgłosi wyjątek [improper_scheduler_attach](improper-scheduler-attach-class.md) , jeśli ten harmonogram jest bieżącym harmonogramem wywołującego kontekstu.

## <a name="create"></a>Create

Tworzy nowy harmonogram, którego zachowanie jest opisane przez `_Policy` parametru, umieszcza odwołanie początkowe w harmonogramie i zwraca do niego wskaźnik.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zasady harmonogramu opisujące zachowanie nowo utworzonego harmonogramu.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonego harmonogramu. Ten obiekt `Scheduler` ma umieszczaną początkową liczbę odwołań.

### <a name="remarks"></a>Uwagi

Po utworzeniu harmonogramu przy użyciu metody `Create` należy wywołać metodę `Release` w pewnym momencie w przyszłości, aby usunąć początkową liczbę odwołań i zezwolić na zamknięcie harmonogramu.

Harmonogram utworzony za pomocą tej metody nie jest dołączony do kontekstu wywołującego. Można go dołączyć do kontekstu przy użyciu metody [Attach](#attach) .

Ta metoda może zgłosić różne wyjątki, w tym [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) i [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>CreateScheduleGroup —

Tworzy nową grupę harmonogramów w ramach harmonogramu. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadania w nowo utworzonej grupie harmonogramu zostaną rozdzielone na wykonanie w lokalizacji określonej przez ten parametr.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odwołanie do lokalizacji, w której zadania w ramach grupy harmonogramu będą rozliczać do wykonywania w.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonej grupy harmonogramów. Ten obiekt `ScheduleGroup` ma umieszczaną początkową liczbę odwołań.

### <a name="remarks"></a>Uwagi

Należy wywołać metodę [Release](schedulegroup-class.md#release) w grupie harmonogramu, gdy planujesz do niej prace. Harmonogram będzie niszczył grupę harmonogramu, gdy cała praca w kolejce do niej została zakończona.

Należy pamiętać, że jeśli ten harmonogram został utworzony jawnie, przed zwolnieniem odwołań do harmonogramu należy zwolnić wszystkie odwołania do grup zaplanowanych w ramach tej usługi.

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors —

Zwraca bieżącą liczbę procesorów wirtualnych dla harmonogramu.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Bieżąca liczba procesorów wirtualnych dla harmonogramu.

## <a name="getpolicy"></a>GetPolicy —

Zwraca kopię zasad, za pomocą której został utworzony harmonogram.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Kopia zasad, za pomocą których harmonogram został utworzony.

## <a name="id"></a>#

Zwraca unikatowy identyfikator dla harmonogramu.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator dla harmonogramu.

## <a name="isavailablelocation"></a>IsAvailableLocation —

Określa, czy dana lokalizacja jest dostępna w harmonogramie.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parametry

*_Placement*<br/>
Odwołanie do lokalizacji, w której ma być wysyłana Kwerenda dotycząca usługi Scheduler.

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy lokalizacja określona przez argument `_Placement` jest dostępna w harmonogramie.

### <a name="remarks"></a>Uwagi

Zwróć uwagę, że wartość zwracana to chwilowe próbkowanie, czy dana lokalizacja jest dostępna. W obecności wielu harmonogramów dynamiczne zarządzanie zasobami może dodawać lub odrzucać zasoby od harmonogramów w dowolnym momencie. W takim przypadku dana lokalizacja może zmienić dostępność.

## <a name="reference"></a>Odwoła

Zwiększa liczbę odwołań harmonogramu.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Wartość zwrócona

Nowo zwiększona liczba odwołań.

### <a name="remarks"></a>Uwagi

Jest to zwykle używane do zarządzania okresem istnienia harmonogramu dla kompozycji. Gdy liczba odwołań dla harmonogramu jest równa zero, harmonogram zostanie zamknięty i zostanie destruktorem po ukończeniu wszystkich zadań w harmonogramie.

Metoda zgłosi wyjątek [improper_scheduler_reference](improper-scheduler-reference-class.md) , jeśli liczba odwołań przed wywołaniem metody `Reference` była zerem i wywołanie zostało wykonane z kontekstu, który nie należy do harmonogramu.

## <a name="registershutdownevent"></a>RegisterShutdownEvent —

Powoduje, że dojście zdarzenia systemu Windows przeszedł do `_Event` parametru, aby zasygnalizować, gdy harmonogram zostanie zamknięty i zniszczy siebie. W momencie zasygnalizowania zdarzenia wszystkie prace, które zostały zaplanowane do harmonogramu, zostały ukończone. W tej metodzie można zarejestrować wiele zdarzeń zamknięcia.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parametry

*_Event*<br/>
Dojście do obiektu zdarzenia systemu Windows, które zostanie zasygnalizowane przez środowisko uruchomieniowe, gdy harmonogram zostanie zamknięty i zniszczy siebie.

## <a name="release"></a>Usuwanie

Zmniejsza liczbę odwołań do harmonogramu.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowo zmniejszona liczba odwołań.

### <a name="remarks"></a>Uwagi

Jest to zwykle używane do zarządzania okresem istnienia harmonogramu dla kompozycji. Gdy liczba odwołań dla harmonogramu jest równa zero, harmonogram zostanie zamknięty i zostanie destruktorem po ukończeniu wszystkich zadań w harmonogramie.

## <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy —

Resetuje domyślne zasady harmonogramu do ustawień domyślnych środowiska uruchomieniowego. Przy następnym utworzeniu domyślnego harmonogramu zostaną użyte domyślne ustawienia zasad środowiska uruchomieniowego.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, gdy w ramach procesu istnieje harmonogram domyślny. Nie będzie to miało wpływu na zasady istniejącego harmonogramu domyślnego. Jeśli jednak domyślny harmonogram został zamknięty i zostanie utworzony nowy element domyślny w późniejszym momencie, nowy harmonogram użyje domyślnych ustawień zasad środowiska uruchomieniowego.

## <a name="ctor"></a>Pracę

Obiekt klasy `Scheduler` można utworzyć tylko przy użyciu metod fabrycznych lub niejawnie.

```cpp
Scheduler();
```

### <a name="remarks"></a>Uwagi

Domyślny harmonogram procesu jest tworzony niejawnie w przypadku korzystania z wielu funkcji środowiska uruchomieniowego, które wymagają dołączenia harmonogramu do kontekstu wywołującego. Metody w klasie `CurrentScheduler` i funkcje warstw PPL i Agents zwykle wykonują niejawny załącznik.

Harmonogram można również utworzyć jawnie za pomocą metody `CurrentScheduler::Create` lub metody `Scheduler::Create`.

## <a name="dtor"></a>~ Scheduler

Obiekt klasy `Scheduler` jest niejawnie niszczony, gdy wszystkie odwołania zewnętrzne przestaną istnieć.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a>ScheduleTask —

Planuje zadanie lekkiej wagi w ramach harmonogramu. Uproszczone zadanie zostanie umieszczone w grupie harmonogramu określonej przez środowisko uruchomieniowe. Wersja, która przyjmuje parametr `_Placement` powoduje, że zadanie zostanie rozdzielone na wykonanie w określonej lokalizacji.

```cpp
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
Wskaźnik do funkcji, która ma zostać wykonana, aby wykonać treść zadania o lekkim średnim poziomie.

*_Data*<br/>
Wskaźnik void do danych, które zostaną przesłane jako parametr do treści zadania.

*_Placement*<br/>
Odwołanie do lokalizacji, w której zostanie obciążone zadanie lekkiej wagi.

## <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy —

Zezwala na użycie zasad zdefiniowanych przez użytkownika do tworzenia domyślnego harmonogramu. Tę metodę można wywołać tylko wtedy, gdy w ramach procesu nie istnieje domyślny harmonogram. Po ustawieniu zasad domyślnych, będzie obowiązywać do następnego prawidłowego wywołania do `SetDefaultSchedulerPolicy` lub metody [ResetDefaultSchedulerPolicy —](#resetdefaultschedulerpolicy) .

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parametry

*_Policy*<br/>
Zasady, które mają być ustawione jako domyślne zasady harmonogramu.

### <a name="remarks"></a>Uwagi

Jeśli `SetDefaultSchedulerPolicy` Metoda jest wywoływana, gdy domyślny harmonogram już istnieje w ramach procesu, środowisko uruchomieniowe zgłosi wyjątek [default_scheduler_exists](default-scheduler-exists-class.md) .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
