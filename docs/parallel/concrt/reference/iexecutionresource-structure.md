---
title: IExecutionResource — Struktura
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377314"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource — Struktura

Abstrakcja wątku sprzętowego.

## <a name="syntax"></a>Składnia

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Zwraca liczbę aktywnych katalogów głównych procesora wirtualnego i subskrybowanych wątków zewnętrznych obecnie skojarzonych z podstawowym wątkiem sprzętowym, który reprezentuje ten zasób wykonywania.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Zwraca unikatowy identyfikator wątku sprzętowego, który reprezentuje ten zasób wykonywania.|
|[IExecutionResource::GetNodeId](#getnodeid)|Zwraca unikatowy identyfikator węzła procesora, do którego należy ten zasób wykonywania.|
|[IExecutionResource::Usuń](#remove)|Zwraca ten zasób wykonania do Menedżera zasobów.|

## <a name="remarks"></a>Uwagi

Zasoby wykonania mogą być autonomiczne lub skojarzone z katalogami korzeniowymi procesora wirtualnego. Zasób wykonywania autonomicznego jest tworzony, gdy wątek w aplikacji tworzy subskrypcję wątku. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) i [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) utworzyć subskrypcje `IExecutionResource` wątku i zwracać interfejs reprezentujący subskrypcję. Tworzenie subskrypcji wątku jest sposobem poinformowania Menedżera zasobów, że dany wątek będzie uczestniczyć w pracy w kolejce do harmonogramu, wraz z katalogu źródłowego procesora wirtualnego Menedżer zasobów przypisuje do harmonogramu. Menedżer zasobów używa informacji, aby uniknąć nadmiernej subskrypcji wątków sprzętowych, gdzie to możliwe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>IExecutionResource::CurrentSubscriptionLevel Metoda

Zwraca liczbę aktywnych katalogów głównych procesora wirtualnego i subskrybowanych wątków zewnętrznych obecnie skojarzonych z podstawowym wątkiem sprzętowym, który reprezentuje ten zasób wykonywania.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący poziom subskrypcji.

### <a name="remarks"></a>Uwagi

Poziom subskrypcji informuje, ile uruchomionych wątków jest skojarzonych z wątkiem sprzętowym. Obejmuje to tylko wątki, o których menedżer zasobów jest świadomy w postaci subskrybowanych wątków i katalogów głównych procesora wirtualnego, które aktywnie wykonują serwery proxy wątku.

Wywołanie metody [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)lub metody [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) z parametrem `doSubscribeCurrentThread` ustawionym na wartość **true** zwiększa poziom subskrypcji wątku sprzętowego o jeden. Zwracają również `IExecutionResource` interfejs reprezentujący subskrypcję. Odpowiednie [wywołanie IExecutionResource::Remove](#remove) zmniejsza poziom subskrypcji wątku sprzętowego o jeden.

Czynność aktywacji katalogu głównego procesora wirtualnego przy użyciu metody [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) zwiększa poziom subskrypcji wątku sprzętowego o jeden. Metody [IVirtualProcessorRoot::Deaktywować](ivirtualprocessorroot-structure.md#deactivate)lub [IExecutionResource::Usuń](#remove) dekrementację poziomu subskrypcji o jeden, gdy jest wywoływany w aktywowanym katalogu głównym procesora wirtualnego.

Menedżer zasobów używa informacji na poziomie subskrypcji jako jeden ze sposobów określania, kiedy mają być przesuwne zasoby między harmonogramami.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>IExecutionResource::Metoda GetExecutionResourceId

Zwraca unikatowy identyfikator wątku sprzętowego, który reprezentuje ten zasób wykonywania.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator wątku sprzętowego leżącego u podstaw tego zasobu wykonywania.

### <a name="remarks"></a>Uwagi

Każdy wątek sprzętowy jest przypisywany unikatowy identyfikator przez współbieżność środowiska uruchomieniowego. Jeśli wiele zasobów wykonywania są skojarzone wątku sprzętowego, wszystkie będą miały ten sam identyfikator zasobu wykonywania.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>IExecutionResource::Metoda GetNodeId

Zwraca unikatowy identyfikator węzła procesora, do którego należy ten zasób wykonywania.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator węzła procesora.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze współbieżności reprezentuje wątki sprzętowe w systemie w grupach węzłów procesora. Węzły są zwykle pochodną topologii sprzętowej systemu. Na przykład wszystkie procesory w określonym gnieździe lub określonym węźle NUMA mogą należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowe identyfikatory do `0` tych węzłów, zaczynając od maksymalnie do momentu włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje całkowitą liczbę węzłów procesora w systemie.

Liczbę węzłów można uzyskać z funkcji [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>IExecutionResource::Metoda usuwania

Zwraca ten zasób wykonania do Menedżera zasobów.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler ( pScheduler )*<br/>
Interfejs do harmonogramu, który żąda żądania usunięcia tego zasobu wykonywania.

### <a name="remarks"></a>Uwagi

Ta metoda służy do zwracania autonomicznych zasobów wykonywania, a także zasobów wykonywania skojarzonych z katalogami korzeniowymi procesora wirtualnego do Menedżera zasobów.

Jeśli jest to autonomiczny zasób wykonywania otrzymany z jednej z metod [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) lub [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), wywołanie metody `Remove` zakończy subskrypcję wątku, który zasób został utworzony do reprezentowania. Musisz zakończyć wszystkie subskrypcje wątku przed zamknięciem serwera proxy `Remove` harmonogramu i należy wywołać z wątku, który utworzył subskrypcję.

Katalogi główne procesora wirtualnego również mogą być `Remove` zwracane do `IVirtualProcessorRoot` Menedżera zasobów, `IExecutionResource` wywołując metodę, ponieważ interfejs dziedziczy z interfejsu. Może być konieczne zwrócenie katalogu głównego procesora wirtualnego albo w odpowiedzi na [wywołanie metody IScheduler::RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) lub po zakończeniu pracy z nadrzędnym katalogiem procesora wirtualnego z nadmierną subskrypcją uzyskaną z metody [ISchedulerProxy::CreateOversubscriber.](ischedulerproxy-structure.md#createoversubscriber) W przypadku katalogów głównych procesora wirtualnego `Remove` nie ma żadnych ograniczeń, na których wątek może wywołać metodę.

`invalid_argument`jest generowany, `pScheduler` jeśli parametr `NULL`jest ustawiony na .

`invalid_operation`jest generowany, `pScheduler` jeśli parametr różni się od harmonogramu, dla których utworzono ten zasób wykonywania lub, za pomocą autonomicznego zasobu wykonania, jeśli bieżący wątek różni się od wątku, który utworzył subskrypcję wątku.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
