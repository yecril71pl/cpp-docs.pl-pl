---
title: "Iexecutionresource — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb4ad0b6f9038d78ae94b5ab1dcb148ebd628edc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Zwraca liczbę aktywowanego procesorów wirtualnych katalogów głównych i subskrybowane zewnętrznych wątków aktualnie skojarzony z podstawowej wątku sprzętu, którą reprezentuje ten zasób wykonywania.|  
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Zwraca unikatowy identyfikator wątku sprzętu, który reprezentuje tego zasobu wykonywania.|  
|[IExecutionResource::GetNodeId](#getnodeid)|Zwraca unikatowy identyfikator węzła procesora, należącego do tego zasobu wykonywania.|  
|[IExecutionResource::Remove](#remove)|Zwraca ten zasób wykonywania Menedżera zasobów.|  
  
## <a name="remarks"></a>Uwagi  
 Zasoby wykonanie może być autonomiczny lub skojarzone z procesorów wirtualnych katalogów głównych. Zasób wykonywania autonomiczny jest tworzony podczas wątku w aplikacji tworzy subskrypcję wątku. Metody [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) i [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) tworzyć subskrypcje wątku i zwracać `IExecutionResource` reprezentujący — interfejs Subskrypcja. Tworzenie subskrypcji wątku jest sposób informuje Menedżera zasobów, która będzie częścią danego wątku, w pracach do kolejki harmonogramu, wraz z katalogi główne procesorów wirtualnych, które Resource Manager przypisuje do harmonogramu. Menedżer zasobów informacje są używane w celu uniknięcia subskrybowanie nadmiernej ilości sprzętu wątków gdzie można.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IExecutionResource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="currentsubscriptionlevel"></a>  IExecutionResource::CurrentSubscriptionLevel — metoda  
 Zwraca liczbę aktywowanego procesorów wirtualnych katalogów głównych i subskrybowane zewnętrznych wątków aktualnie skojarzony z podstawowej wątku sprzętu, którą reprezentuje ten zasób wykonywania.  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący poziom subskrypcji.  
  
### <a name="remarks"></a>Uwagi  
 Poziom subskrypcji informuje, jak wiele uruchomionych wątków są skojarzone z wątkiem sprzętu. W tym tylko wątków, jakiej Menedżera zasobów jest znane w formie subskrybowanego wątków i katalogów głównych procesorów wirtualnych, które są aktywnie wykonywanych proxy wątku.  
  
 Wywołanie metody [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), lub metody [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) z parametrem `doSubscribeCurrentThread` ustawiona na wartość `true`zwiększa o jeden poziom subskrypcji wątku sprzętu. Zwracają także `IExecutionResource` interfejs reprezentujący subskrypcji. Do odpowiedniego wywołania [IExecutionResource::Remove](#remove) zmniejsza poziomu subskrypcji wątku sprzętu przez jeden.  
  
 Działanie aktywacji głównego procesora wirtualnego przy użyciu metody [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate) zwiększa o jeden poziom subskrypcji wątku sprzętu. Metody [IVirtualProcessorRoot::Deactivate](ivirtualprocessorroot-structure.md#deactivate), lub [IExecutionResource::Remove](#remove) zmniejszyć poziom subskrypcji przez jedną, gdy została wywołana w katalogu głównym aktywowanego procesora wirtualnego.  
  
 Menedżer zasobów używa poziomu informacji o subskrypcji jako jedną z metod, w którym do określenia, kiedy przenoszenie zasobów między transfery danych.  
  
##  <a name="getexecutionresourceid"></a>  IExecutionResource::GetExecutionResourceId — metoda  
 Zwraca unikatowy identyfikator wątku sprzętu, który reprezentuje tego zasobu wykonywania.  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator wątku sprzętu bazowy tego zasobu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Każdy wątek sprzętu przypisuje unikatowy identyfikator ze współbieżności środowiska wykonawczego. W przypadku wielu zasobów wykonanie skojarzonego sprzętu wątku, wszystkie mają ten sam identyfikator zasobu wykonywania.  
  
##  <a name="getnodeid"></a>  IExecutionResource::GetNodeId — metoda  
 Zwraca unikatowy identyfikator węzła procesora, należącego do tego zasobu wykonywania.  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator węzła procesora.  
  
### <a name="remarks"></a>Uwagi  
 Współbieżność środowiska wykonawczego reprezentuje wątków sprzętu w systemie w grupach węzłów procesora. Węzły są zazwyczaj uzyskiwane z topologii sprzętu systemu. Na przykład wszystkie procesory w określonych gniazda lub określonego węzła NUMA może należeć do tego samego węzła procesora. Menedżer zasobów przypisuje unikatowych identyfikatorów dla tych węzłów, począwszy od `0` włącznie `nodeCount - 1`, gdzie `nodeCount` reprezentuje łączna liczba węzłów procesora w systemie.  
  
 Liczba węzłów, można je uzyskać z funkcji [getprocessornodecount —](concurrency-namespace-functions.md).  
  
##  <a name="remove"></a>  IExecutionResource::Remove — Metoda  
 Zwraca ten zasób wykonywania Menedżera zasobów.  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pScheduler`  
 Interfejs do zgłoszenia żądania, aby usunąć ten zasób wykonywania harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zwrócić autonomicznego realizacji zasobów, a także wykonanie zasoby skojarzone z procesorów wirtualnych katalogów głównych Menedżera zasobów.  
  
 Jeśli jest zasobem autonomicznego realizacji otrzymanej od jednej z metod [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) lub [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), wywoływania Metoda `Remove` zakończy subskrypcji wątku, który zasób został utworzony w celu reprezentowania. Są wymagane, aby zakończyć wszystkie subskrypcje wątku przed zamknięciem proxy harmonogramu i należy wywołać metodę `Remove` z wątek, który utworzył subskrypcji.  
  
 Procesorów wirtualnych katalogów głównych, zbyt, może być zwracany Menedżera zasobów za pomocą `Remove` metody, ponieważ interfejs `IVirtualProcessorRoot` dziedziczy `IExecutionResource` interfejsu. Konieczne może być zwracany procesora wirtualnego katalogu głównego, albo w odpowiedzi na wywołanie [IScheduler::RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) metody, lub po zakończeniu oversubscribed procesora wirtualnego katalogu głównego, pochodzi z [ ISchedulerProxy::CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber) metody. Dla katalogów głównych procesora wirtualnego, nie ma żadnych ograniczeń w wątku, który można wywołać `Remove` metody.  
  
 `invalid_argument` wygenerowany, jeśli parametr `pScheduler` ma ustawioną wartość `NULL`.  
  
 `invalid_operation` wygenerowany, jeśli parametr `pScheduler` różni się od harmonogramu, że ten zasób wykonanie został utworzony na lub z zasobem autonomicznego realizacji, jeśli bieżący wątek jest inny niż wątek, który utworzył subskrypcji wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)
