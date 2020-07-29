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
ms.openlocfilehash: dcb6d175fa84e33f6a5af974eb76f1e1246bdc35
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226701"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy — Struktura

Interfejs, za pomocą którego program Schedules komunikuje się z Menedżer zasobów środowisko uruchomieniowe współbieżności w celu negocjowania alokacji zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISchedulerProxy:: BindContext —](#bindcontext)|Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie został jeszcze skojarzony z jednym.|
|[ISchedulerProxy:: CreateOversubscriber —](#createoversubscriber)|Tworzy nowy rdzeń wirtualnego procesora w wątku sprzętowym skojarzonym z istniejącym zasobem wykonania.|
|[ISchedulerProxy:: RequestInitialVirtualProcessors —](#requestinitialvirtualprocessors)|Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy główny wirtualny procesor reprezentuje możliwość wykonywania jednego wątku, który może wykonywać pracę w harmonogramie.|
|[ISchedulerProxy:: Shutdown](#shutdown)|Powiadamia Menedżer zasobów o zamknięciu harmonogramu. Spowoduje to, że Menedżer zasobów natychmiast Odbierz wszystkie zasoby przydzielone do harmonogramu.|
|[ISchedulerProxy:: SubscribeCurrentThread —](#subscribecurrentthread)|Rejestruje bieżący wątek w Menedżer zasobów, kojarząc go z tym harmonogramem.|
|[ISchedulerProxy:: UnbindContext —](#unbindcontext)|Odkojarzy serwer proxy wątku z kontekstu wykonywania określonego przez `pContext` parametr i zwraca go do puli wolnych dla fabryki proxy wątku. Tę metodę można wywołać tylko w kontekście wykonywania, który został powiązany przez metodę [ISchedulerProxy:: BindContext —](#bindcontext) i nie został jeszcze uruchomiony za pośrednictwem `pContext` parametru metody [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) .|

## <a name="remarks"></a>Uwagi

Menedżer zasobów to `ISchedulerProxy` interfejs do każdego harmonogramu, który rejestruje się za pomocą metody [IResourceManager:: RegisterScheduler —](iresourcemanager-structure.md#registerscheduler) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISchedulerProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy:: BindContext —, Metoda

Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie został jeszcze skojarzony z jednym.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Interfejs do kontekstu wykonywania, który ma zostać skojarzony z serwerem proxy wątku.

### <a name="remarks"></a>Uwagi

Zwykle Metoda [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) będzie powiązać serwer proxy wątku z kontekstem wykonywania na żądanie. Istnieją jednak sytuacje, w których konieczne jest powiązanie kontekstu z wyprzedzeniem, aby upewnić się, że `SwitchTo` Metoda przełącza się do już powiązanego kontekstu. Dzieje się tak w przypadku kontekstu planowania UMS, ponieważ nie może on wywołać metod przynoszących pamięć, a powiązanie serwera proxy wątków może wiązać się z alokacją pamięci, jeśli serwer proxy wątku nie jest łatwo dostępny w bezpłatnej puli fabryki proxy wątków.

`invalid_argument`jest zgłaszany, jeśli parametr `pContext` ma wartość `NULL` .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>ISchedulerProxy:: CreateOversubscriber —, Metoda

Tworzy nowy rdzeń wirtualnego procesora w wątku sprzętowym skojarzonym z istniejącym zasobem wykonania.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pExecutionResource*<br/>
`IExecutionResource`Interfejs reprezentujący wątek sprzętowy, który chcesz zasubskrybować.

### <a name="return-value"></a>Wartość zwracana

`IVirtualProcessorRoot`Interfejs.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli harmonogram chce zasubskrybować określony wątek sprzętowy przez ograniczoną ilość czasu. Po zakończeniu pracy z głównym procesorem wirtualnym należy zwrócić go do Menedżera zasobów, wywołując metodę [Remove](iexecutionresource-structure.md#remove) w `IVirtualProcessorRoot` interfejsie.

Można nawet zasubskrybować istniejący rdzeń wirtualnego procesora, ponieważ `IVirtualProcessorRoot` interfejs dziedziczy po `IExecutionResource` interfejsie.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy:: RequestInitialVirtualProcessors —, Metoda

Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy główny wirtualny procesor reprezentuje możliwość wykonywania jednego wątku, który może wykonywać pracę w harmonogramie.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Czy zasubskrybować bieżący wątek i konto podczas alokacji zasobów.

### <a name="return-value"></a>Wartość zwracana

`IExecutionResource`Interfejs dla bieżącego wątku, jeśli parametr `doSubscribeCurrentThread` ma wartość **`true`** . Jeśli wartość jest **`false`** , metoda zwraca wartość null.

### <a name="remarks"></a>Uwagi

Aby harmonogram wykonał jakąkolwiek pracę, należy użyć tej metody do żądania katalogów głównych procesora wirtualnego z Menedżer zasobów. Menedżer zasobów będzie uzyskiwać dostęp do zasad harmonogramu za pomocą [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy) i używania wartości dla kluczy zasad `MinConcurrency` `MaxConcurrency` oraz `TargetOversubscriptionFactor` do określenia liczby wątków sprzętowych, które mają być przypisane początkowo do harmonogramu, oraz liczby katalogów głównych procesorów wirtualnych, które mają zostać utworzone dla każdego wątku sprzętowego. Aby uzyskać więcej informacji na temat sposobu używania zasad harmonogramu do określenia początkowej alokacji harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

Menedżer zasobów przyznaje zasoby do harmonogramu, wywołując metodę [IScheduler:: AddVirtualProcessors —](ischeduler-structure.md#addvirtualprocessors) z listą katalogów głównych procesora wirtualnego. Metoda jest wywoływana jako wywołanie zwrotne do harmonogramu przed zwróceniem tej metody.

Jeśli harmonogram żąda subskrypcji bieżącego wątku przez ustawienie parametru `doSubscribeCurrentThread` na **`true`** , metoda zwraca `IExecutionResource` interfejs. Subskrypcję należy zakończyć w późniejszym czasie za pomocą metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) .

Podczas określania, które wątki sprzętowe są wybrane, Menedżer zasobów będzie próbować zoptymalizować dla koligacji węzła procesora. Jeśli zażądano subskrypcji bieżącego wątku, oznacza to, że bieżący wątek zamierza wziąć udział w pracy przypisanej do tego harmonogramu. W takim przypadku elementy główne przydzielonych procesorów wirtualnych znajdują się w węźle procesora, w którym jest wykonywany bieżący wątek, jeśli jest to możliwe.

Czynność subskrybowania wątku zwiększa poziom subskrypcji bazowego wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden, gdy subskrypcja zostanie przerwana. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy:: Shutdown — Metoda

Powiadamia Menedżer zasobów o zamknięciu harmonogramu. Spowoduje to, że Menedżer zasobów natychmiast Odbierz wszystkie zasoby przydzielone do harmonogramu.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Uwagi

Wszystkie `IExecutionContext` interfejsy odebrane przez harmonogram w wyniku subskrybowania wątku zewnętrznego przy użyciu metod `ISchedulerProxy::RequestInitialVirtualProcessors` lub `ISchedulerProxy::SubscribeCurrentThread` muszą zostać zwrócone do Menedżer zasobów przy użyciu `IExecutionResource::Remove` przed zamknięciem usługi Scheduler.

Jeśli w harmonogramie zostały zdezaktywowane katalogi główne procesora wirtualnego, należy je aktywować przy użyciu [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate)i mieć wykonywane przez nich serwery proxy wątków, pozostawiając `Dispatch` metodę kontekstów wykonywania, które są wysyłane przed wywołaniem `Shutdown` na serwerze proxy usługi Scheduler.

Nie jest konieczne, aby harmonogram zwracał pojedynczo wszystkie elementy główne wirtualnego procesora Menedżer zasobów przyznane do niego przez wywołania `Remove` metody, ponieważ wszystkie katalogi wirtualne procesorów wirtualnych zostaną zwrócone do Menedżer zasobów przy zamykaniu.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy:: SubscribeCurrentThread —, Metoda

Rejestruje bieżący wątek w Menedżer zasobów, kojarząc go z tym harmonogramem.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Połączenie, które `IExecutionResource` reprezentuje bieżący wątek w środowisku uruchomieniowym.

### <a name="remarks"></a>Uwagi

Użyj tej metody, jeśli chcesz, aby Menedżer zasobów do konta bieżącego wątku podczas alokowania zasobów do harmonogramu i innych harmonogramów. Jest on szczególnie przydatny, gdy wątek planuje uczestnictwo w pracy w kolejce do harmonogramu, wraz z głównymi procesorami wirtualnymi, które usługa Scheduler odbiera z Menedżer zasobów. Menedżer zasobów używa informacji, aby zapobiegać niepotrzebnym nadsubskrypcji wątków sprzętowych w systemie.

Zasób wykonywania otrzymany za pośrednictwem tej metody powinien zostać zwrócony do Menedżer zasobów przy użyciu metody [IExecutionResource:: Remove](iexecutionresource-structure.md#remove) . Wątek, który wywołuje `Remove` metodę, musi być tym samym wątkiem, który wcześniej wezwał `SubscribeCurrentThread` metodę.

Czynność subskrybowania wątku zwiększa poziom subskrypcji bazowego wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden, gdy subskrypcja zostanie przerwana. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>ISchedulerProxy:: UnbindContext —, Metoda

Odkojarzy serwer proxy wątku z kontekstu wykonywania określonego przez `pContext` parametr i zwraca go do puli wolnych dla fabryki proxy wątku. Tę metodę można wywołać tylko w kontekście wykonywania, który został powiązany przez metodę [ISchedulerProxy:: BindContext —](#bindcontext) i nie został jeszcze uruchomiony za pośrednictwem `pContext` parametru metody [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto) .

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*pContext*<br/>
Kontekst wykonywania do skojarzenia z jego serwerem proxy wątków.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Struktura IScheduler](ischeduler-structure.md)<br/>
[IThreadProxy — Struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot — Struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager — Struktura](iresourcemanager-structure.md)
