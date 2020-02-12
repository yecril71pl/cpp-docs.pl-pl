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
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141273"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource — Struktura

Abstrakcja wątku sprzętowego.

## <a name="syntax"></a>Składnia

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IExecutionResource:: CurrentSubscriptionLevel —](#currentsubscriptionlevel)|Zwraca liczbę aktywowanych katalogów głównych procesora wirtualnego i subskrybowanych wątków zewnętrznych aktualnie skojarzonych z wątkiem sprzętowym, który reprezentuje ten zasób.|
|[IExecutionResource:: GetExecutionResourceId —](#getexecutionresourceid)|Zwraca unikatowy identyfikator wątku sprzętowego reprezentowanego przez ten zasób wykonania.|
|[IExecutionResource:: GetNodeId —](#getnodeid)|Zwraca unikatowy identyfikator węzła procesora, do którego należy ten zasób wykonania.|
|[IExecutionResource:: Remove](#remove)|Zwraca ten zasób wykonania do Menedżer zasobów.|

## <a name="remarks"></a>Uwagi

Zasoby wykonywania mogą być autonomiczne lub skojarzone z głównymi procesorami wirtualnymi. Zasób samodzielnego wykonywania jest tworzony, gdy wątek w aplikacji tworzy subskrypcję wątku. Metody [ISchedulerProxy:: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) i [ISchedulerProxy:: RequestInitialVirtualProcessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors) tworzą subskrypcje wątków i zwracają interfejs `IExecutionResource` reprezentujący subskrypcję. Tworzenie subskrypcji wątku jest sposobem na poinformowanie Menedżer zasobów, że dany wątek będzie uczestniczyć w kolejce pracy do harmonogramu, wraz z katalogami głównymi procesora wirtualnego Menedżer zasobów przypisywanych do harmonogramu. Menedżer zasobów używa tych informacji, aby uniknąć zasubskrybowania wątków sprzętowych, gdzie to możliwe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="currentsubscriptionlevel"></a>IExecutionResource:: CurrentSubscriptionLevel —, Metoda

Zwraca liczbę aktywowanych katalogów głównych procesora wirtualnego i subskrybowanych wątków zewnętrznych aktualnie skojarzonych z wątkiem sprzętowym, który reprezentuje ten zasób.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Bieżący poziom subskrypcji.

### <a name="remarks"></a>Uwagi

Poziom subskrypcji informuje o liczbie uruchomionych wątków skojarzonych z wątkiem sprzętowym. Obejmuje to tylko wątki, dla których Menedżer zasobów jest świadome w postaci wątków subskrybowanych, oraz katalogów głównych procesorów wirtualnych, które aktywnie korzystają z serwerów proxy wątków.

Wywołanie metody [ISchedulerProxy:: SubscribeCurrentThread —](ischedulerproxy-structure.md#subscribecurrentthread)lub metody [ISchedulerProxy:: RequestInitialVirtualProcessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors) z parametrem `doSubscribeCurrentThread` ustawionym na wartość **true** powoduje zwiększenie poziomu subskrypcji wątku sprzętowego o jeden. Zwracają również interfejs `IExecutionResource` reprezentujący subskrypcję. Odpowiednie wywołanie [IExecutionResource:: Remove](#remove) zmniejsza poziom subskrypcji wątku sprzętowego o jeden.

Czynność aktywowania głównego wirtualnego procesora przy użyciu metody [IVirtualProcessorRoot:: Activate](ivirtualprocessorroot-structure.md#activate) zwiększa poziom subskrypcji wątku sprzętowego o jeden. Metody [IVirtualProcessorRoot::D eactivate](ivirtualprocessorroot-structure.md#deactivate)lub [IExecutionResource:: Remove](#remove) zmniejszają poziom subskrypcji o jeden po wywołaniu dla aktywowanego wirtualnego procesora.

Menedżer zasobów używa informacji o poziomie subskrypcji jako jednego ze sposobów określania czasu przenoszenia zasobów między harmonogramami.

## <a name="getexecutionresourceid"></a>IExecutionResource:: GetExecutionResourceId —, Metoda

Zwraca unikatowy identyfikator wątku sprzętowego reprezentowanego przez ten zasób wykonania.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator wątku sprzętowego odpowiadającego temu zasobowi wykonania.

### <a name="remarks"></a>Uwagi

Każdy wątek sprzętowy ma przypisany unikatowy identyfikator przez środowisko uruchomieniowe współbieżności. Jeśli do wątku sprzętowego są skojarzone wiele zasobów wykonawczych, wszystkie będą miały ten sam identyfikator zasobu wykonania.

## <a name="getnodeid"></a>IExecutionResource:: GetNodeId —, Metoda

Zwraca unikatowy identyfikator węzła procesora, do którego należy ten zasób wykonania.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator węzła procesora.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe współbieżności reprezentuje wątki sprzętowe w systemie w grupach węzłów procesora. Węzły są zwykle wyprowadzane z topologii sprzętowej systemu. Na przykład wszystkie procesory w określonym gnieździe lub określony węzeł NUMA mogą należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowe identyfikatory do tych węzłów, rozpoczynając od `0` do i łącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje łączną liczbę węzłów procesora w systemie.

Liczbę węzłów można uzyskać z funkcji [GetProcessorNodeCount —](concurrency-namespace-functions.md).

## <a name="remove"></a>IExecutionResource:: Remove — Metoda

Zwraca ten zasób wykonania do Menedżer zasobów.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Interfejs do harmonogramu wykonujący żądanie usunięcia tego zasobu wykonania.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zwrócić autonomiczne zasoby wykonawcze, a także zasoby wykonywania skojarzone z głównymi procesorami wirtualnymi do Menedżer zasobów.

Jeśli jest to autonomiczny zasób wykonywania otrzymany z jednej z metod [ISchedulerProxy:: SubscribeCurrentThread —](ischedulerproxy-structure.md#subscribecurrentthread) lub [ISchedulerProxy:: RequestInitialVirtualProcessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors), wywołanie metody `Remove` spowoduje zakończenie subskrypcji wątku, która reprezentuje zasób. Przed zamknięciem serwera proxy usługi Scheduler należy zakończyć wszystkie subskrypcje wątków i należy wywołać `Remove` z wątku, który utworzył subskrypcję.

Również elementy główne procesora wirtualnego można zwrócić do Menedżer zasobów, wywołując metodę `Remove`, ponieważ interfejs `IVirtualProcessorRoot` dziedziczy z interfejsu `IExecutionResource`. Może być konieczne zwrócenie katalogu głównego wirtualnego procesora w odpowiedzi na wywołanie metody [IScheduler:: RemoveVirtualProcessors —](ischeduler-structure.md#removevirtualprocessors) lub po zakończeniu z zasubskrybowanym korzeniem wirtualnego procesora, który uzyskano z metody [ISchedulerProxy:: CreateOversubscriber —](ischedulerproxy-structure.md#createoversubscriber) . W przypadku katalogów głównych procesorów wirtualnych nie ma żadnych ograniczeń dotyczących tego, które wątki mogą wywołać metodę `Remove`.

`invalid_argument` jest generowany, jeśli `pScheduler` parametru jest ustawiona na `NULL`.

`invalid_operation` jest generowany, jeśli parametr `pScheduler` różni się od harmonogramu, dla którego ten zasób wykonywania został utworzony dla lub przy użyciu autonomicznego zasobu wykonywania, jeśli bieżący wątek jest inny niż wątek, który utworzył subskrypcję wątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
