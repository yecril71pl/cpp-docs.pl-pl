---
title: "Ischedulerproxy — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs: C++
helpviewer_keywords: ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b151e68c9cce0113c46f0eaffff8e19ed4d5c896
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy — Struktura
Interfejs, za pomocą którego planiści komunikować się z Menedżerem zasobów współbieżność środowiska wykonawczego do negocjowania alokacji zasobów.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|Kojarzy kontekstu wykonywania z wątku serwera proxy, jeśli nie jest już skojarzony z jednym.|  
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Tworzy nowy element główny procesorów wirtualnych w wątku sprzętu skojarzony z istniejącym zasobem wykonywania.|  
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Żądania wstępnego przyznawania procesorów wirtualnych katalogów głównych. Każdy procesora wirtualnego katalogu głównego reprezentuje możliwość wykonania jeden wątek, który może wykonywać pracy dla harmonogramu.|  
|[ISchedulerProxy::Shutdown](#shutdown)|Powiadamia menedżera zasobów, że harmonogram jest zamykana. Spowoduje to Menedżera zasobów, aby natychmiast odzyskać wszystkie zasoby przyznane do harmonogramu.|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Rejestruje bieżący wątek w usłudze Resource Manager skojarzeniem go z tego harmonogramu.|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Usuwa skojarzenia z kontekstu wykonywania określonej przez serwer proxy wątku `pContext` parametrów i zwraca go do puli wolnych wątków fabryki serwera proxy. Tę metodę można wywoływać tylko w kontekście wykonywania, który został powiązany za pomocą [ISchedulerProxy::BindContext](#bindcontext) — metoda i jeszcze nie został uruchomiony za pośrednictwem trwa `pContext` parametr [IThreadProxy::SwitchTo ](ithreadproxy-structure.md#switchto) wywołania metody.|  
  
## <a name="remarks"></a>Uwagi  
 Przekazuje Resource Manager `ISchedulerProxy` interfejsu każdego udogodnień, które rejestruje za pomocą [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="bindcontext"></a>ISchedulerProxy::BindContext — metoda  
 Kojarzy kontekstu wykonywania z wątku serwera proxy, jeśli nie jest już skojarzony z jednym.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Interfejs do kontekstu wykonywania do skojarzenia z serwerem proxy wątku.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) metody powiązać proxy wątku kontekstu wykonywania na żądanie. Istnieją, jednak okoliczności, w którym należy powiązać kontekstu z wyprzedzeniem, aby upewnić się, że `SwitchTo` metody zmienia kontekst już powiązane. Dotyczy to na UMS, kontekst harmonogramu, ponieważ nie można wywołać metody przydzielania pamięci i powiązanie proxy wątku może obejmować alokacji pamięci, jeśli serwer proxy wątku nie jest jeszcze dostępna w wolnej puli wątków fabryki serwera proxy.  
  
 `invalid_argument`wygenerowany, jeśli parametr `pContext` ma wartość `NULL`.  
  
##  <a name="createoversubscriber"></a>ISchedulerProxy::CreateOversubscriber — metoda  
 Tworzy nowy element główny procesorów wirtualnych w wątku sprzętu skojarzony z istniejącym zasobem wykonywania.  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pExecutionResource`  
 `IExecutionResource` Interfejs, który reprezentuje wątku sprzętu ma być oversubscribe.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IVirtualProcessorRoot` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, gdy chce oversubscribe wątku konkretnego sprzętu przez ograniczony czas z harmonogramu. Po wykonaniu głównego procesora wirtualnego, należy przywrócić go Menedżera zasobów przez wywołanie metody [Usuń](iexecutionresource-structure.md#remove) metoda `IVirtualProcessorRoot` interfejsu.  
  
 Możesz nawet oversubscribe istniejący katalog główny procesora wirtualnego, ponieważ `IVirtualProcessorRoot` dziedziczy interfejs `IExecutionResource` interfejsu.  
  
##  <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy::RequestInitialVirtualProcessors — metoda  
 Żądania wstępnego przyznawania procesorów wirtualnych katalogów głównych. Każdy procesora wirtualnego katalogu głównego reprezentuje możliwość wykonania jeden wątek, który może wykonywać pracy dla harmonogramu.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `doSubscribeCurrentThread`  
 Określa, czy subskrypcja bieżącego wątku i uwzględnić go podczas alokacji zasobów.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IExecutionResource` Interfejsu dla bieżącego wątku, jeśli parametr `doSubscribeCurrentThread` ma wartość `true`. Jeśli wartość jest `false`, metoda zwraca `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Przed harmonogramu wykonuje pracę, go należy użyć tej metody do żądania procesorów wirtualnych katalogów głównych z Menedżera zasobów. Menedżer zasobów będą uzyskiwać dostęp do zasad harmonogramu przy użyciu [IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) i użyj wartości kluczy zasad `MinConcurrency`, `MaxConcurrency` i `TargetOversubscriptionFactor` ustalenie, jak wiele wątków sprzętu do przypisania do Harmonogram początkowo i liczbę procesorów wirtualnych katalogów głównych można utworzyć dla każdego wątku sprzętu. Aby uzyskać więcej informacji na jak zasad harmonogramu są używane do określania harmonogramu początkowej alokacji, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
 Menedżer zasobów przyznaje zasobów do harmonogramu, wywołując metodę [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) z listy procesorów wirtualnych katalogów głównych. Metoda jest wywoływana jako wywołanie zwrotne do harmonogramu zanim ta metoda zwraca wartość.  
  
 Jeśli harmonogram żądane subskrypcji dla bieżącego wątku przez ustawienie dla parametru `doSubscribeCurrentThread` do `true`, metoda zwraca `IExecutionResource` interfejsu. Subskrypcja musi być zakończona w późniejszym czasie przy użyciu [IExecutionResource::Remove](iexecutionresource-structure.md#remove) metody.  
  
 Podczas określania, które wątków sprzętu są wybrane, Resource Manager podejmie próbę Optymalizuj dla procesora koligacji węzła. Jeśli subskrypcja jest wymagany dla bieżącego wątku, to wskazanie, że bieżący wątek nie chce uczestniczyć w pracy przypisane do tego harmonogramu. W takim przypadku przydzielone procesory wirtualne katalogi główne znajdują się w węźle procesora, które bieżący wątek jest wykonywany, jeśli to możliwe.  
  
 Czynność subskrypcji wątku zwiększa poziom subskrypcji źródłowej wątku sprzętu o jeden. Poziom subskrypcji jest ograniczone przez jedną, gdy subskrypcja jest zakończony. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>ISchedulerProxy::Shutdown — metoda  
 Powiadamia menedżera zasobów, że harmonogram jest zamykana. Spowoduje to Menedżera zasobów, aby natychmiast odzyskać wszystkie zasoby przyznane do harmonogramu.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie `IExecutionContext` interfejsy harmonogramu otrzymane w wyniku subskrypcji zewnętrznych wątku przy użyciu metod `ISchedulerProxy::RequestInitialVirtualProcessors` lub `ISchedulerProxy::SubscribeCurrentThread` musi zostać zwrócona do Menedżera zasobów przy użyciu `IExecutionResource::Remove` przed harmonogramu zostaje wyłączony.  
  
 Gdyby użytkownika harmonogramu dowolnej dezaktywowane procesorów wirtualnych katalogów głównych, należy je włączyć za pomocą [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)i mieć proxy wątku wykonywanie na nich pozostaw `Dispatch` metody wykonywania konteksty są one wysyłki przed wywołuje `Shutdown` na serwer proxy harmonogramu.  
  
 Nie jest niezbędna dla harmonogramu do indywidualnie zwrócenia wszystkich głównych procesorów wirtualnych Menedżera zasobów udzielone za pośrednictwem wywołania `Remove` metody ponieważ wszystkich procesorów wirtualnych katalogów głównych zostanie zwrócony przy zamykaniu do Menedżera zasobów.  
  
##  <a name="subscribecurrentthread"></a>ISchedulerProxy::SubscribeCurrentThread — metoda  
 Rejestruje bieżący wątek w usłudze Resource Manager skojarzeniem go z tego harmonogramu.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IExecutionResource` Relacje reprezentujący bieżący wątek w czasie wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, jeśli chcesz, aby Menedżer zasobów do konta dla bieżącego wątku podczas przydzielania zasobów z harmonogramu i inne transfery danych. Jest szczególnie przydatne w przypadku planów wątku brać udziału w pracy w kolejce do Twojej harmonogramu, wraz z katalogi główne procesorów wirtualnych, które planista odbiera z Menedżera zasobów. Menedżer zasobów używa informacji, aby uniknąć niepotrzebnych nadsubskrypcji wątków sprzętu w systemie.  
  
 Zasób wykonywania odebranych za pośrednictwem tej metody ma zostać zwrócony do Menedżera zasobów przy użyciu [IExecutionResource::Remove](iexecutionresource-structure.md#remove) metody. Wątek, który wywołuje `Remove` metoda musi być tym samym wątku, który wcześniej nazywane `SubscribeCurrentThread` metody.  
  
 Czynność subskrypcji wątku zwiększa poziom subskrypcji źródłowej wątku sprzętu o jeden. Poziom subskrypcji jest ograniczone przez jedną, gdy subskrypcja jest zakończony. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>ISchedulerProxy::UnbindContext — metoda  
 Usuwa skojarzenia z kontekstu wykonywania określonej przez serwer proxy wątku `pContext` parametrów i zwraca go do puli wolnych wątków fabryki serwera proxy. Tę metodę można wywoływać tylko w kontekście wykonywania, który został powiązany za pomocą [ISchedulerProxy::BindContext](#bindcontext) — metoda i jeszcze nie został uruchomiony za pośrednictwem trwa `pContext` parametr [IThreadProxy::SwitchTo ](ithreadproxy-structure.md#switchto) wywołania metody.  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pContext`  
 Kontekst wykonywania, aby usunąć skojarzenie z jego agent proxy wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Struktura IScheduler](ischeduler-structure.md)   
 [Ithreadproxy — struktura](ithreadproxy-structure.md)   
 [Ivirtualprocessorroot — struktura](ivirtualprocessorroot-structure.md)   
 [IResourceManager, struktura](iresourcemanager-structure.md)
