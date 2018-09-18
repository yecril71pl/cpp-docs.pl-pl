---
title: Ischedulerproxy — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 189d4b4084958c2572a0a3165509acd3be6e8d23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028301"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy — Struktura
Interfejs, za pomocą którego lotów komunikować się z Menedżerem zasobów w środowisku uruchomieniowym współbieżności do negocjowania alokacji zasobów.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|Kojarzy kontekstu wykonania za pomocą serwera proxy wątku, jeśli nie jest już skojarzony z jednym.|  
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Tworzy nowego procesora wirtualnego katalogu głównego wątku sprzętu skojarzony z istniejącym zasobem wykonywania.|  
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Żądania wstępnego przyznawania korzeni procesora wirtualnego. Każdy procesora wirtualnego katalogu głównego reprezentuje zdolności do jej realizacji jeden wątek, który można wykonać pracę dla harmonogramu.|  
|[ISchedulerProxy::Shutdown](#shutdown)|Powiadamia menedżera zasobów, że harmonogram jest zamykana. Spowoduje to Menedżera zasobów, aby natychmiast odzyskać wszystkie zasoby przyznane do harmonogramu.|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Rejestruje bieżącego wątku za pomocą Menedżera zasobów, kojarząc ją za pomocą tego harmonogramu.|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Powoduje usunięcie z kontekstu wykonania określonego przez wątek serwera proxy `pContext` parametr i zwraca go do puli bezpłatnej fabryki serwera proxy wątku. Ta metoda lze volat pouze w kontekście wykonywania, który został powiązany za pośrednictwem [ischedulerproxy::bindcontext —](#bindcontext) metody i nie zostało jeszcze uruchomione za pośrednictwem trwa `pContext` parametru [ithreadproxy::switchto — ](ithreadproxy-structure.md#switchto) wywołania metody.|  
  
## <a name="remarks"></a>Uwagi  
 Resource Manager przekazuje `ISchedulerProxy` interfejs do każdej harmonogram, który rejestruje go za pomocą [iresourcemanager::registerscheduler —](iresourcemanager-structure.md#registerscheduler) metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="bindcontext"></a>  Ischedulerproxy::bindcontext — metoda  
 Kojarzy kontekstu wykonania za pomocą serwera proxy wątku, jeśli nie jest już skojarzony z jednym.  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pContext*<br/>
Interfejs do kontekstu wykonania do skojarzenia z serwerem proxy wątku.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle [ithreadproxy::switchto —](ithreadproxy-structure.md#switchto) metoda powiąże wątek serwera proxy do kontekstu wykonania na żądanie. Istnieją, jednak okoliczności, w którym należy go powiązać kontekstu z wyprzedzeniem, aby upewnić się, że `SwitchTo` metoda przełącza się do kontekstu już powiązane. Dotyczy to na UMS, kontekst harmonogramu, ponieważ nie można wywoływać metody, które przydzielają pamięć i powiązania serwera proxy wątku może obejmować alokacji pamięci, jeśli serwer proxy wątku nie jest jeszcze dostępna w wolnej puli fabryki serwera proxy wątku.  
  
 `invalid_argument` jest generowany, jeśli parametr `pContext` ma wartość `NULL`.  
  
##  <a name="createoversubscriber"></a>  Ischedulerproxy::createoversubscriber — metoda  
 Tworzy nowego procesora wirtualnego katalogu głównego wątku sprzętu skojarzony z istniejącym zasobem wykonywania.  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pExecutionResource*<br/>
`IExecutionResource` Interfejs, który reprezentuje wątek sprzętu, aby oversubscribe.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IVirtualProcessorRoot` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda harmonogramu chce oversubscribe wątku określonego sprzętu przez ograniczony czas. Po wykonaniu procesora wirtualnego katalogu głównego, powinna zwracać je do usługi resource manager przez wywołanie metody [Usuń](iexecutionresource-structure.md#remove) metody `IVirtualProcessorRoot` interfejsu.  
  
 Możesz nawet jest nadsubskrybowanie istniejącego katalogu głównego procesora wirtualnego, ponieważ `IVirtualProcessorRoot` interfejs dziedziczy z `IExecutionResource` interfejsu.  
  
##  <a name="requestinitialvirtualprocessors"></a>  Ischedulerproxy::requestinitialvirtualprocessors — metoda  
 Żądania wstępnego przyznawania korzeni procesora wirtualnego. Każdy procesora wirtualnego katalogu głównego reprezentuje zdolności do jej realizacji jeden wątek, który można wykonać pracę dla harmonogramu.  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*doSubscribeCurrentThread*<br/>
Określa, czy subskrypcja bieżący wątek i uwzględnić go podczas alokacji zasobów.  
  
### <a name="return-value"></a>Wartość zwracana  
 `IExecutionResource` Interfejsu dla bieżącego wątku, jeśli parametr `doSubscribeCurrentThread` ma wartość `true`. Jeśli wartość jest `false`, metoda zwraca `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Przed harmonogramu wykonuje żadnych działań, ta metoda powinna korzystać do żądania korzeni procesora wirtualnego, Menedżera zasobów. Menedżer zasobów będą miały dostęp zasadę harmonogramu przy użyciu [ischeduler::getpolicy —](ischeduler-structure.md#getpolicy) i użyj wartości kluczy zasad `MinConcurrency`, `MaxConcurrency` i `TargetOversubscriptionFactor` ustalenie, jak wiele wątków sprzętu, aby przypisać do Harmonogram początkowo i jak wiele głównych procesorów wirtualnych, aby utworzyć dla każdego wątku sprzętu. Aby uzyskać więcej informacji na temat używania zasad harmonogramu do ustalenia harmonogramu początkowego przydziału, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
 Menedżer zasobów przyznaje zasobów do harmonogramu przez wywołanie metody [ischeduler::addvirtualprocessors —](ischeduler-structure.md#addvirtualprocessors) listę głównych procesorów wirtualnych. Metoda jest wywoływana jako wywołanie zwrotne w ramach harmonogramu zadań, zanim ta metoda zwraca wartość.  
  
 Jeśli harmonogram żądane subskrypcji dla bieżącego wątku przez ustawienie dla parametru `doSubscribeCurrentThread` do `true`, metoda zwraca `IExecutionResource` interfejsu. Subskrypcja musi być zakończona w dowolnym momencie za pomocą [iexecutionresource::REMOVE —](iexecutionresource-structure.md#remove) metody.  
  
 Podczas określania, które wątków sprzętu są zaznaczone, Menedżer zasobów będzie podejmować próby Optymalizuj dla procesora koligacji węzłów. Jeśli subskrypcja jest wymagany dla bieżącego wątku, jest wskazanie, że bieżący wątek nie chce uczestniczyć w pracach przypisane do tego harmonogramu. W takim przypadku przydzielone procesory wirtualne katalogi główne znajdują się w węźle procesora, do którego bieżący wątek jest wykonywany, jeśli jest to możliwe.  
  
 Czynność subskrybowania wątku zwiększa się o jeden poziom subskrypcji w podstawowym wątku sprzętu. Poziom subskrypcji jest ograniczone przez jeden, gdy subskrypcja jest zakończony. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="shutdown"></a>  Ischedulerproxy::Shutdown — metoda  
 Powiadamia menedżera zasobów, że harmonogram jest zamykana. Spowoduje to Menedżera zasobów, aby natychmiast odzyskać wszystkie zasoby przyznane do harmonogramu.  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie `IExecutionContext` interfejsy harmonogramu otrzymane w wyniku subskrybowania zewnętrzny wątek przy użyciu metod `ISchedulerProxy::RequestInitialVirtualProcessors` lub `ISchedulerProxy::SubscribeCurrentThread` musi zostać zwrócone do usługi Resource Manager przy użyciu `IExecutionResource::Remove` przed harmonogramu kończy pracę.  
  
 Jeśli próba zawierała harmonogramu dowolnej dezaktywowane korzeni procesora wirtualnego, należy je włączyć za pomocą [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate)i mają proxy wątku wykonywania na nich pozostaw `Dispatch` metody wykonywania konteksty muszą być wysyłki przed wywołujesz `Shutdown` na serwer proxy usługi scheduler.  
  
 Nie jest konieczne usługi scheduler do indywidualnie zwrócenia wszystkich głównych procesorów wirtualnych Menedżera zasobów udzielone za pośrednictwem wywołania `Remove` metody, ponieważ wszystkie procesory wirtualne katalogi główne zostaną zwrócone do usługi Resource Manager podczas zamykania systemu.  
  
##  <a name="subscribecurrentthread"></a>  Ischedulerproxy::subscribecurrentthread — metoda  
 Rejestruje bieżącego wątku za pomocą Menedżera zasobów, kojarząc ją za pomocą tego harmonogramu.  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IExecutionResource` Komunikowanie się reprezentujący bieżącego wątku w środowisku uruchomieniowym.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, jeśli chcesz, aby konto dla bieżącego wątku podczas przydzielania zasobów do harmonogramu i inne transfery danych za pomocą Menedżera zasobów. Może to być szczególnie przydatne, gdy uczestniczy w pracach plany wątku w kolejce do harmonogramu, wraz z korzeni procesora wirtualnego, który harmonogram otrzymuje z usługi Resource Manager. Menedżer zasobów używa informacji, aby uniknąć niepotrzebnych nadsubskrypcję wątków sprzętu w systemie.  
  
 Zasób wykonywania odebraną za pomocą tej metody powinna zostać zwrócona do usługi Resource Manager przy użyciu [iexecutionresource::REMOVE —](iexecutionresource-structure.md#remove) metody. Wątek, który wywołuje `Remove` metoda musi być tym samym wątku, który wcześniej nazywane `SubscribeCurrentThread` metody.  
  
 Czynność subskrybowania wątku zwiększa się o jeden poziom subskrypcji w podstawowym wątku sprzętu. Poziom subskrypcji jest ograniczone przez jeden, gdy subskrypcja jest zakończony. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
##  <a name="unbindcontext"></a>  Ischedulerproxy::unbindcontext — metoda  
 Powoduje usunięcie z kontekstu wykonania określonego przez wątek serwera proxy `pContext` parametr i zwraca go do puli bezpłatnej fabryki serwera proxy wątku. Ta metoda lze volat pouze w kontekście wykonywania, który został powiązany za pośrednictwem [ischedulerproxy::bindcontext —](#bindcontext) metody i nie zostało jeszcze uruchomione za pośrednictwem trwa `pContext` parametru [ithreadproxy::switchto — ](ithreadproxy-structure.md#switchto) wywołania metody.  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pContext*<br/>
Kontekst wykonywania, aby usunąć skojarzenie z jego agent proxy wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IScheduler, struktura](ischeduler-structure.md)   
 [Ithreadproxy — struktura](ithreadproxy-structure.md)   
 [Ivirtualprocessorroot — struktura](ivirtualprocessorroot-structure.md)   
 [IResourceManager, struktura](iresourcemanager-structure.md)
