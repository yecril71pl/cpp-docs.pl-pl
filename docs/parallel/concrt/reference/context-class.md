---
title: Context — Klasa
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 9074dad572a3a74a5b456e9790dc359ddf8b7c60
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293956"
---
# <a name="context-class"></a>Context — Klasa

Reprezentuje klasą abstrakcyjną dla kontekstu wykonywania.

## <a name="syntax"></a>Składnia

```
class Context;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[~ Context — destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Blok](#block)|Blokuje bieżący kontekst.|
|[CurrentContext](#currentcontext)|Zwraca wskaźnik do bieżącego kontekstu.|
|[GetId](#getid)|Zwraca identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do której należy dany kontekst.|
|[GetScheduleGroupId](#getschedulegroupid)|Zwraca identyfikator grupy harmonogramu, który aktualnie pracuje kontekst.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|Zwraca identyfikator wirtualnego procesora, który jest aktualnie wywoływany na.|
|[Identyfikator](#id)|Zwraca identyfikator bieżącego kontekstu, która jest unikatowa w obrębie harmonogramu, do którego należy bieżący kontekst.|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Zwraca wskazanie, czy kolekcja zadań, która jest aktualnie wykonywana i wbudowana w bieżącym kontekście jest w środku aktywnego anulowania (lub będzie wkrótce).|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Określa, czy kontekst jest synchronicznie zablokowany. Kontekst uznaje się synchronicznie zablokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokady.|
|[Oversubscribe](#oversubscribe)|Wprowadza dodatkowy procesor wirtualny do harmonogramu na czas trwania bloku kodu, gdy wywoływany w kontekście wykonywania na jednym z procesorów wirtualnych w tym harmonogramie.|
|[ScheduleGroupId](#schedulegroupid)|Zwraca identyfikator grupy harmonogramu, który pracuje bieżącego kontekstu.|
|[Unblock](#unblock)|Odblokowuje kontekst i powoduje, że usługa będzie możliwy do uruchomienia.|
|[VirtualProcessorId](#virtualprocessorid)|Zwraca identyfikator wirtualnego procesora, który jest wykonywany bieżący kontekst.|
|[Yield](#yield)|Przekazuje wykonywanie kodu, dzięki czemu można wykonać w innym kontekście. Jeśli żaden inny kontekst nie jest dostępny do podania, harmonogram może podać inny wątek systemu operacyjnego.|

## <a name="remarks"></a>Uwagi

Harmonogram współbieżność środowiska wykonawczego (zobacz [harmonogramu](scheduler-class.md)) używa kontekstów wykonanie do wykonanie pracy w kolejce do niego przez daną aplikację. Wątek Win32 jest przykładem kontekst wykonania w systemie operacyjnym Windows.

W dowolnym momencie poziom współbieżności harmonogramu jest równa liczbie procesorów wirtualnych przyznanych przez Menedżera zasobów. Procesor wirtualny jest klasą abstrakcyjną dla zasobów przetwarzania i mapuje do wątku sprzętu w systemie podstawowym. Tylko pojedynczy Kontekst harmonogramu można wykonać przy użyciu procesora wirtualnego w danym momencie.

Usługa scheduler jest współpraca z natury i wywoływany kontekst może spowodować jego procesorów wirtualnych do innego kontekstu w dowolnym momencie, jeśli zażyczy sobie wejść w stan oczekiwania. Gdy jego oczekiwania zostaną spełnione, nie można wznowić, do momentu rozpoczęcia przez harmonogram dostępne wirtualnego procesor jej wykonanie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Context`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="block"></a> Blok

Blokuje bieżący kontekst.

```
static void __cdecl Block();
```

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

Jeśli kontekst wywołania działa na procesorze wirtualnym, procesor wirtualny znajdzie innym kontekście możliwy do uruchomienia na wykonanie lub potencjalnie może utworzyć nową.

Po `Block` metoda została wywołana lub zostanie wywołana, Sparuj go z wywołaniem [odblokowanie](#unblock) metody z innego kontekstu wykonania w celu użycia go do ponownego uruchomienia. Należy pamiętać, że między punktem, w którym kod publikuje kontekst do innego wątku można było wywołać okresie krytycznym `Unblock` metody i punkt, gdzie wywołanie metody rzeczywiste `Block` wykonano. W tym okresie nie należy wywołać każdą metodę, która z kolei można blokować i odblokowywać swój własny powodów (np. uzyskiwania blokady). Wywołania `Block` i `Unblock` Przyczyna blokowania i odblokowywania "nie Śledź" metoda. Tylko jeden obiekt powinien mieć własności `Block` -  `Unblock` pary.

Ta metoda może zgłosić różnych wyjątków, łącznie z [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md).

##  <a name="dtor"></a> ~ Kontekstu

```
virtual ~Context();
```

##  <a name="currentcontext"></a> CurrentContext

Zwraca wskaźnik do bieżącego kontekstu.

```
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bieżącego kontekstu.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

##  <a name="getid"></a> GetId

Zwraca identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do której należy dany kontekst.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu, który jest unikatowy w obrębie harmonogramu, do której należy dany kontekst.

##  <a name="getschedulegroupid"></a> GetScheduleGroupId

Zwraca identyfikator grupy harmonogramu, który aktualnie pracuje kontekst.

```
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator grupy harmonogramu, w którym aktualnie pracuje kontekst.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania grupy harmonogramu, który kontekst. Jeśli ta metoda jest wywoływana w kontekście innej niż bieżący kontekst, wartość może być nieaktualne moment, są zwracane i nie można polegać. Zazwyczaj ta metoda jest używana do debugowania lub tylko do celów śledzenia.

##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId

Zwraca identyfikator wirtualnego procesora, który jest aktualnie wywoływany na.

```
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli jest aktualnie wywoływany przy użyciu procesora wirtualnego, identyfikator wirtualnego procesora, który jest aktualnie wywoływany. w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania procesora wirtualnego, który kontekst. Ta wartość może być nieaktualne moment, są zwracane i nie można polegać. Zazwyczaj ta metoda jest używana do debugowania lub tylko do celów śledzenia.

##  <a name="id"></a> Id

Zwraca identyfikator bieżącego kontekstu, która jest unikatowa w obrębie harmonogramu, do którego należy bieżący kontekst.

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator dla bieżącego kontekstu, która jest unikatowa w obrębie harmonogramu, do którego należy bieżący kontekst; w przeciwnym razie wartość `-1`.

##  <a name="iscurrenttaskcollectioncanceling"></a> Iscurrenttaskcollectioncanceling —

Zwraca wskazanie, czy kolekcja zadań, która jest aktualnie wykonywana i wbudowana w bieżącym kontekście jest w środku aktywnego anulowania (lub będzie wkrótce).

```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli harmonogram jest dołączony do wywoływania kontekstu i grupy zadań jest wykonywana i wbudowana zadania w tym kontekście, wskazanie, czy tej grupy zadań jest w środku aktywnego anulowania (lub będzie wkrótce) w przeciwnym razie wartość `false`.

##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked

Określa, czy kontekst jest synchronicznie zablokowany. Kontekst uznaje się synchronicznie zablokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokady.

```
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Czy kontekst jest synchronicznie zablokowany.

### <a name="remarks"></a>Uwagi

Kontekst uznaje się synchronicznie zablokowany, jeśli jawnie wykonał akcję, która doprowadziła do blokady. W harmonogramie wątku, może to wskazywać na bezpośrednie wywołanie `Context::Block` metoda lub obiekt synchronizacji, który został zbudowany przy użyciu `Context::Block` metody.

Wartość zwrócona przez tę metodę jest natychmiastowe przykładem tego, czy kontekst jest synchronicznie zablokowany. Ta wartość może być nieaktualne moment, są zwracane i można używać tylko w bardzo szczególnych okolicznościach.

##  <a name="operator_delete"></a> Usuwanie operatora

A `Context` obiekt jest niszczony wewnętrznie przez środowisko uruchomieniowe. Go nie można jawnie usunąć.

```
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parametry

*_PObject*<br/>
Wskaźnik do obiektu, który ma zostać usunięty.

##  <a name="oversubscribe"></a> Oversubscribe

Wprowadza dodatkowy procesor wirtualny do harmonogramu na czas trwania bloku kodu, gdy wywoływany w kontekście wykonywania na jednym z procesorów wirtualnych w tym harmonogramie.

```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parametry

*_BeginOversubscription*<br/>
Jeśli **true**, wskazanie, że procesor dodatkowe wirtualne powinny zostać dodane w czasie trwania nadsubskrypcji. Jeśli **false**, wskazanie, że nadsubskrypcja należy zakończyć i uprzednio dodanych procesora wirtualnego, które powinny zostać usunięte.

##  <a name="schedulegroupid"></a> ScheduleGroupId

Zwraca identyfikator grupy harmonogramu, który pracuje bieżącego kontekstu.

```
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli bieżący kontekst jest dołączony do harmonogramu i pracy na grupy harmonogramu, identyfikator harmonogramu grupa, bieżącego kontekstu pracuje; w przeciwnym razie wartość `-1`.

##  <a name="unblock"></a> Odblokowywanie

Odblokowuje kontekst i powoduje, że usługa będzie możliwy do uruchomienia.

```
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Uwagi

Doskonale dozwolone wywołania `Unblock` metoda przed odpowiedniego wywołania [bloku](#block) metody. Tak długo, jak wywołania `Block` i `Unblock` metody są prawidłowo skojarzone, środowisko wykonawcze obsługuje prawidłowo naturalnych wyścigu albo kolejności. `Unblock` Wywołania pochodzące przed `Block` wywołania po prostu neguje efekt `Block` wywołania.

Istnieje kilka wyjątków, które mogą być generowane przez tę metodę. Jeśli kontekst próbuje wywołać `Unblock` metody na siebie, [context_self_unblock —](context-self-unblock-class.md) zostanie zgłoszony wyjątek. Jeśli wywołania `Block` i `Unblock` nie są prawidłowo skojarzone (na przykład dwa wywołania `Unblock` są wykonywane w kontekście, który jest obecnie uruchomiona), [context_unblock_unbalanced —](context-unblock-unbalanced-class.md) zostanie zgłoszony wyjątek.

Należy pamiętać, że między punktem, w którym kod publikuje kontekst do innego wątku można było wywołać okresie krytycznym `Unblock` metody i punkt, gdzie wywołanie metody rzeczywiste `Block` wykonano. W tym okresie nie należy wywołać każdą metodę, która z kolei można blokować i odblokowywać swój własny powodów (np. uzyskiwania blokady). Wywołania `Block` i `Unblock` Przyczyna blokowania i odblokowywania "nie Śledź" metoda. Tylko jeden obiekt powinien mieć własności `Block` i `Unblock` pary.

##  <a name="virtualprocessorid"></a> VirtualProcessorId

Zwraca identyfikator wirtualnego procesora, który jest wykonywany bieżący kontekst.

```
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli bieżący kontekst jest dołączony do harmonogramu, identyfikator wirtualnego procesora, który jest wykonywany bieżący kontekst; w przeciwnym razie wartość `-1`.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez tę metodę jest natychmiastowe próbkowania procesora wirtualnego, który jest wykonywany bieżący kontekst. Ta wartość może być nieaktualne moment, są zwracane i nie można polegać. Zazwyczaj ta metoda jest używana do debugowania lub tylko do celów śledzenia.

##  <a name="yield"></a> YIELD

Przekazuje wykonywanie kodu, dzięki czemu można wykonać w innym kontekście. Jeśli żaden inny kontekst nie jest dostępny do podania, harmonogram może podać inny wątek systemu operacyjnego.

```
static void __cdecl Yield();
```

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

##  <a name="yieldexecution"></a> YieldExecution

Przekazuje wykonywanie kodu, dzięki czemu można wykonać w innym kontekście. Jeśli żaden inny kontekst nie jest dostępny do podania, harmonogram może podać inny wątek systemu operacyjnego.

```
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Uwagi

Ta metoda powoduje procesu domyślnego harmonogramu są tworzone i/lub dołączyć do wywoływania kontekstu, jeśli nie harmonogramu obecnie skojarzony kontekst wywołania.

Ta funkcja jest nowa w programie Visual Studio 2015 i jest taka sama jak [uzyskanie](#yield) funkcji, ale nie powoduje konfliktu z makr Yield w Windows.h.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Scheduler, klasa](scheduler-class.md)<br/>
[Task Scheduler](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
