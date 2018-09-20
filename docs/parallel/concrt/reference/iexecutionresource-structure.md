---
title: Iexecutionresource — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs:
- C++
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 912cdb59a1841bbe3bbe3e71202a796a3e67a94e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390269"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource — Struktura

Abstrakcja wątku sprzętu.

## <a name="syntax"></a>Składnia

```
struct IExecutionResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Iexecutionresource::currentsubscriptionlevel —](#currentsubscriptionlevel)|Zwraca liczbę aktywowanego Procesor wirtualny elementy główne i subskrypcję zewnętrznych wątków obecnie skojarzony z podstawowym wątku sprzętu, którą reprezentuje ten zasób wykonywania.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Zwraca unikatowy identyfikator wątku sprzętu, który reprezentuje ten zasób wykonywania.|
|[IExecutionResource::GetNodeId](#getnodeid)|Zwraca unikatowy identyfikator dla węzła procesora, której należy ten zasób wykonywania.|
|[IExecutionResource::Remove](#remove)|Zwraca ten zasób wykonywania do usługi Resource Manager.|

## <a name="remarks"></a>Uwagi

Zasoby wykonanie może być autonomiczny lub skojarzone z głównych procesorów wirtualnych. Zasób wykonywania autonomiczny jest tworzone, gdy wątek w aplikacji tworzy subskrypcję wątku. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) i [ischedulerproxy::requestinitialvirtualprocessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors) tworzyć subskrypcje wątku, a następnie wróć `IExecutionResource` interfejs reprezentujący Subskrypcja. Utworzenie subskrypcji w wątku jest sposobem informuje Menedżera zasobów, który danego wątku będą uczestniczyć w pracy w kolejce do harmonogramu, wraz z głównych procesorów wirtualnych, które usługi Resource Manager przypisuje do harmonogramu. Resource Manager używa informacji w celu uniknięcia subskrybowanie nadmiernej ilości wątków sprzętu, gdzie jest to możliwe.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IExecutionResource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="currentsubscriptionlevel"></a>  Iexecutionresource::currentsubscriptionlevel — metoda

Zwraca liczbę aktywowanego Procesor wirtualny elementy główne i subskrypcję zewnętrznych wątków obecnie skojarzony z podstawowym wątku sprzętu, którą reprezentuje ten zasób wykonywania.

```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący poziom subskrypcji.

### <a name="remarks"></a>Uwagi

Poziom subskrypcji informuje, jak wiele wątków uruchomionych są skojarzone z wątków sprzętu. Obejmuje to tylko wątki, Menedżer zasobów jest znane w formie subskrybowanego wątków i korzeni procesora wirtualnego, wykonywanych aktywnie proxy wątku.

Wywołanie metody [ischedulerproxy::subscribecurrentthread —](ischedulerproxy-structure.md#subscribecurrentthread), lub metody [ischedulerproxy::requestinitialvirtualprocessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors) z parametrem `doSubscribeCurrentThread` ustawiona na wartość `true`zwiększa poziom subskrypcji wątku sprzętu za pomocą jednej. Zwracają także `IExecutionResource` interfejs reprezentujący subskrypcji. Do odpowiedniego wywołania [iexecutionresource::REMOVE —](#remove) zmniejsza o jeden poziom subskrypcji wątku sprzętu za pomocą jednej.

Działanie procesora wirtualnego katalogu głównego przy użyciu metody aktywacji [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) zwiększa poziom subskrypcji wątku sprzętu za pomocą jednej. Metody [ivirtualprocessorroot::Deactivate —](ivirtualprocessorroot-structure.md#deactivate), lub [iexecutionresource::REMOVE —](#remove) zmniejszyć poziom subskrypcji za pomocą jednej po wywołaniu na aktywowanego procesora wirtualnego katalogu głównego.

Menedżer zasobów używa informacji o poziomie subskrypcji jako jednym ze sposobów, w którym do określenia, kiedy przenoszenia zasobów między transfery danych.

##  <a name="getexecutionresourceid"></a>  Iexecutionresource::getexecutionresourceid — metoda

Zwraca unikatowy identyfikator wątku sprzętu, który reprezentuje ten zasób wykonywania.

```
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator wątku sprzętu bazowego zasobu wykonywania.

### <a name="remarks"></a>Uwagi

Każdy wątek sprzętu jest przypisany unikatowy identyfikator w czasie wykonywania współbieżności. W przypadku wielu zasobów wykonywania powiązanym sprzętem wątku one będą mieć taki sam identyfikator zasobu wykonywania.

##  <a name="getnodeid"></a>  Iexecutionresource::getnodeid — metoda

Zwraca unikatowy identyfikator dla węzła procesora, której należy ten zasób wykonywania.

```
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator dla węzła procesora.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe współbieżności reprezentuje wątków sprzętu w systemie w grupy węzłów procesora. Węzły są zazwyczaj uzyskiwane z topologii sprzętu systemu. Na przykład wszystkie procesory w określonych gniazdo lub określonego węzła NUMA może należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowych identyfikatorów do tych węzłów, począwszy od `0` włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje całkowita liczba węzłów procesora w systemie.

Liczba węzłów można uzyskać z funkcji [getprocessornodecount —](concurrency-namespace-functions.md).

##  <a name="remove"></a>  Iexecutionresource::Remove — Metoda

Zwraca ten zasób wykonywania do usługi Resource Manager.

```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Parametry

*pScheduler*<br/>
Interfejs harmonogramu, dzięki czemu wniosek o usunięcie tego zasobu wykonywania.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby zwrócić autonomiczny wykonywania zasobów, a także zasoby wykonywania skojarzone z głównych procesorów wirtualnych Menedżera zasobów.

Jeśli jest to zasób wykonywania autonomiczny otrzymany od jednej z metod [ischedulerproxy::subscribecurrentthread —](ischedulerproxy-structure.md#subscribecurrentthread) lub [ischedulerproxy::requestinitialvirtualprocessors —](ischedulerproxy-structure.md#requestinitialvirtualprocessors), wywoływania Metoda `Remove` zakończy się subskrypcji wątku, który został utworzony zasób, aby reprezentować. Są wymagane do zakończenia wszystkich subskrypcji wątku przed zamknięciem proxy harmonogram, a musi wywołać `Remove` z wątku, który utworzono subskrypcję.

Korzeni procesora wirtualnego, mogą być zwrócone do usługi Resource Manager za pomocą wywołania `Remove` metody, ponieważ interfejs `IVirtualProcessorRoot` dziedziczy `IExecutionResource` interfejsu. Konieczne może być zwracać procesora wirtualnego katalogu głównego, albo w odpowiedzi na wywołanie [ischeduler::removevirtualprocessors —](ischeduler-structure.md#removevirtualprocessors) metodę, lub po zakończeniu zażądałeś procesora wirtualnego katalogu głównego, które zostały uzyskane z [ Ischedulerproxy::createoversubscriber —](ischedulerproxy-structure.md#createoversubscriber) metody. Korzeni procesora wirtualnego, nie ma żadnych ograniczeń w wątku, który można wywołać `Remove` metody.

`invalid_argument` jest generowany, jeśli parametr `pScheduler` ustawiono `NULL`.

`invalid_operation` jest generowany, jeśli parametr `pScheduler` różni się od harmonogramu, ten zasób wykonywania został utworzony do lub z zasobem wykonywania autonomicznych, jeśli bieżący wątek jest inny niż wątek, który utworzono subskrypcję wątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
