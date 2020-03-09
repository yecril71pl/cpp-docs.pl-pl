---
title: ISchedulerProxy — Struktura
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 776f70f9b93eb2e38151ceb5e84b4664420cf954
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854213"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy — Struktura

Interfejs, za pomocą którego program Schedules komunikuje się z Menedżer zasobów środowisko uruchomieniowe współbieżności w celu negocjowania alokacji zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ISchedulerProxy:: BindContext —](#bindcontext)|Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie został jeszcze skojarzony z jednym.|
|[ISchedulerProxy:: CreateOversubscriber —](#createoversubscriber)|Tworzy nowy rdzeń wirtualnego procesora w wątku sprzętowym skojarzonym z istniejącym zasobem wykonania.|
|[ISchedulerProxy:: RequestInitialVirtualProcessors —](#requestinitialvirtualprocessors)|Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy główny wirtualny procesor reprezentuje możliwość wykonywania jednego wątku, który może wykonywać pracę w harmonogramie.|
|[ISchedulerProxy:: Shutdown](#shutdown)|Powiadamia Menedżer zasobów o zamknięciu harmonogramu. Spowoduje to, że Menedżer zasobów natychmiast Odbierz wszystkie zasoby przydzielone do harmonogramu.|
|[ISchedulerProxy:: SubscribeCurrentThread —](#subscribecurrentthread)|Rejestruje bieżący wątek w Menedżer zasobów, kojarząc go z tym harmonogramem.|
|[ISchedulerProxy:: UnbindContext —](#unbindcontext)|Odkojarzy serwer proxy wątku z kontekstu wykonywania określonego przez parametr `pContext` i zwraca go do puli wolnych dla fabryki proxy wątku. Tę metodę można wywołać tylko w kontekście wykonywania, który został powiązany przez metodę [ISchedulerProxy:: BindContext —](#bindcontext) i nie został jeszcze uruchomiony za pośrednictwem `pContext` parametru wywołania metody [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) .|

## <a name="remarks"></a>Uwagi

Menedżer zasobów to interfejs `ISchedulerProxy` do każdego harmonogramu, który rejestruje się za pomocą metody [IResourceManager:: RegisterScheduler —](iresourcemanager-structure.md#registerscheduler) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISchedulerProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="bindcontext"></a>ISchedulerProxy:: BindContext —, Metoda

Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie został jeszcze skojarzony z jednym.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Interfejs do kontekstu wykonywania, który ma zostać skojarzony z serwerem proxy wątku.

### <a name="remarks"></a>Uwagi

Zwykle Metoda [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) będzie powiązać serwer proxy wątku z kontekstem wykonywania na żądanie. Istnieją jednak sytuacje, w których konieczne jest powiązanie kontekstu z wyprzedzeniem, aby upewnić się, że metoda `SwitchTo` przełączy się już z kontekstem. Dzieje się tak w przypadku kontekstu planowania UMS, ponieważ nie może on wywołać metod przynoszących pamięć, a powiązanie serwera proxy wątków może wiązać się z alokacją pamięci, jeśli serwer proxy wątku nie jest łatwo dostępny w bezpłatnej puli fabryki proxy wątków.

`invalid_argument` jest generowany, jeśli parametr `pContext` ma wartość `NULL`.

## <a name="createoversubscriber"></a>ISchedulerProxy:: CreateOversubscriber —, Metoda

Tworzy nowy rdzeń wirtualnego procesora w wątku sprzętowym skojarzonym z istniejącym zasobem wykonania.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pExecutionResource*<br/>
Interfejs `IExecutionResource` reprezentujący wątek sprzętowy, który chcesz zasubskrybować.

### <a name="return-value"></a>Wartość zwracana

Interfejs `IVirtualProcessorRoot`.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli harmonogram chce zasubskrybować określony wątek sprzętowy przez ograniczoną ilość czasu. Po zakończeniu pracy z głównym procesorem wirtualnym należy zwrócić go do Menedżera zasobów, wywołując metodę [Remove](iexecutionresource-structure.md#remove) w interfejsie `IVirtualProcessorRoot`.

Można nawet zasubskrybować istniejący rdzeń wirtualnego procesora, ponieważ interfejs `IVirtualProcessorRoot` dziedziczy po interfejsie `IExecutionResource`.

## <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: RequestInitialVirtualProcessors —, Metoda

Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy główny wirtualny procesor reprezentuje możliwość wykonywania jednego wątku, który może wykonywać pracę w harmonogramie.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Czy zasubskrybować bieżący wątek i konto podczas alokacji zasobów.

### <a name="return-value"></a>Wartość zwracana

Interfejs `IExecutionResource` bieżącego wątku, jeśli parametr `doSubscribeCurrentThread` ma wartość **true**. Jeśli wartość to **false**, metoda zwraca wartość null.

### <a name="remarks"></a>Uwagi

Aby harmonogram wykonał jakąkolwiek pracę, należy użyć tej metody do żądania katalogów głównych procesora wirtualnego z Menedżer zasobów. Menedżer zasobów będzie uzyskiwać dostęp do zasad harmonogramu za pomocą [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) i używania wartości kluczy zasad `MinConcurrency`, `MaxConcurrency` i `TargetOversubscriptionFactor`, aby określić, ile wątków sprzętowych ma być przypisywanych do harmonogramu początkowo i ile katalogów głównych procesorów wirtualnych do utworzenia dla każdego wątku sprzętowego. Aby uzyskać więcej informacji na temat sposobu używania zasad harmonogramu do określenia początkowej alokacji harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

Menedżer zasobów przyznaje zasoby do harmonogramu, wywołując metodę [IScheduler:: AddVirtualProcessors —](ischeduler-structure.md#addvirtualprocessors) z listą katalogów głównych procesora wirtualnego. Metoda jest wywoływana jako wywołanie zwrotne do harmonogramu przed zwróceniem tej metody.

Jeśli harmonogram zażądał subskrypcji bieżącego wątku przez ustawienie parametru `doSubscribeCurrentThread` na **true**, metoda zwraca interfejs `IExecutionResource`. Subskrypcję należy zakończyć w późniejszym czasie za pomocą metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) .

Podczas określania, które wątki sprzętowe są wybrane, Menedżer zasobów będzie próbować zoptymalizować dla koligacji węzła procesora. Jeśli zażądano subskrypcji bieżącego wątku, oznacza to, że bieżący wątek zamierza wziąć udział w pracy przypisanej do tego harmonogramu. W takim przypadku elementy główne przydzielonych procesorów wirtualnych znajdują się w węźle procesora, w którym jest wykonywany bieżący wątek, jeśli jest to możliwe.

Czynność subskrybowania wątku zwiększa poziom subskrypcji bazowego wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden, gdy subskrypcja zostanie przerwana. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="shutdown"></a>ISchedulerProxy:: Shutdown — Metoda

Powiadamia Menedżer zasobów o zamknięciu harmonogramu. Spowoduje to, że Menedżer zasobów natychmiast Odbierz wszystkie zasoby przydzielone do harmonogramu.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Uwagi

Wszystkie `IExecutionContext` interfejsy, które zostały odebrane przez harmonogram w wyniku subskrybowania wątku zewnętrznego przy użyciu metod `ISchedulerProxy::RequestInitialVirtualProcessors` lub `ISchedulerProxy::SubscribeCurrentThread` należy zwrócić do Menedżer zasobów przy użyciu `IExecutionResource::Remove`, zanim harmonogram zamknie się w dół.

Jeśli w harmonogramie zostały zdezaktywowane katalogi główne procesora wirtualnego, należy je aktywować przy użyciu [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)i mieć wykonywane przez niego serwery proxy wątków, pozostawiając `Dispatch`ą metodę kontekstów wykonywania, które są wysyłane przed wywołaniem `Shutdown` na serwerze proxy usługi Scheduler.

Nie jest konieczne, aby harmonogram zwracał pojedynczo wszystkie elementy główne wirtualnego procesora Menedżer zasobów przyznane do niego za pośrednictwem wywołań metody `Remove`, ponieważ wszystkie katalogi wirtualne procesorów wirtualnych zostaną zwrócone do Menedżer zasobów przy zamykaniu.

## <a name="subscribecurrentthread"></a>ISchedulerProxy:: SubscribeCurrentThread —, Metoda

Rejestruje bieżący wątek w Menedżer zasobów, kojarząc go z tym harmonogramem.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Wartość zwracana

`IExecutionResource`, który reprezentuje bieżący wątek w środowisku uruchomieniowym.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli chcesz, aby Menedżer zasobów do konta bieżącego wątku podczas alokowania zasobów do harmonogramu i innych harmonogramów. Jest on szczególnie przydatny, gdy wątek planuje uczestnictwo w pracy w kolejce do harmonogramu, wraz z głównymi procesorami wirtualnymi, które usługa Scheduler odbiera z Menedżer zasobów. Menedżer zasobów używa informacji, aby zapobiegać niepotrzebnym nadsubskrypcji wątków sprzętowych w systemie.

Zasób wykonywania otrzymany za pośrednictwem tej metody powinien zostać zwrócony do Menedżer zasobów przy użyciu metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) . Wątek, który wywołuje metodę `Remove`, musi być tym samym wątkiem, który wcześniej wezwał metodę `SubscribeCurrentThread`.

Czynność subskrybowania wątku zwiększa poziom subskrypcji bazowego wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden, gdy subskrypcja zostanie przerwana. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="unbindcontext"></a>ISchedulerProxy:: UnbindContext —, Metoda

Odkojarzy serwer proxy wątku z kontekstu wykonywania określonego przez parametr `pContext` i zwraca go do puli wolnych dla fabryki proxy wątku. Tę metodę można wywołać tylko w kontekście wykonywania, który został powiązany przez metodę [ISchedulerProxy:: BindContext —](#bindcontext) i nie został jeszcze uruchomiony za pośrednictwem `pContext` parametru wywołania metody [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) .

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst wykonywania do skojarzenia z jego serwerem proxy wątków.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, struktura](iresourcemanager-structure.md)
