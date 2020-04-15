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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368162"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy — Struktura

Interfejs, za pomocą którego harmonogramy komunikują się z Menedżerem zasobów środowiska wykonawczego współbieżności w celu negocjowania alokacji zasobów.

## <a name="syntax"></a>Składnia

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie jest już skojarzony z jednym.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Tworzy nowy katalog główny procesora wirtualnego w wątku sprzętowym skojarzonym z istniejącym zasobem wykonawczym.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy katalog główny procesora wirtualnego reprezentuje możliwość wykonania jednego wątku, który może wykonywać pracę dla harmonogramu.|
|[ISchedulerProxy::Zamknięcie](#shutdown)|Powiadamia Menedżera zasobów, że harmonogram jest zamykany. Spowoduje to, że Menedżer zasobów natychmiast odzyskać wszystkie zasoby przyznane harmonogramowi.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Rejestruje bieżący wątek z Menedżerem zasobów, kojarząc go z tym harmonogramem.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Odłącza serwer proxy wątku od kontekstu wykonywania `pContext` określonego przez parametr i zwraca go do wolnej puli fabryki proxy wątku. Ta metoda może być wywoływana tylko w kontekście wykonywania, który został powiązany za pośrednictwem [metody ISchedulerProxy::BindContext](#bindcontext) i nie została jeszcze uruchomiona za pomocą `pContext` parametru wywołania metody [IThreadProxy::SwitchTo.](ithreadproxy-structure.md#switchto)|

## <a name="remarks"></a>Uwagi

Menedżer zasobów przekazuje `ISchedulerProxy` interfejs do każdego harmonogramu, który rejestruje się z nim przy użyciu [metody IResourceManager::RegisterScheduler.](iresourcemanager-structure.md#registerscheduler)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISchedulerProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy::BindContext Metoda

Kojarzy kontekst wykonywania z serwerem proxy wątku, jeśli nie jest już skojarzony z jednym.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Interfejs do kontekstu wykonywania do skojarzenia z serwerem proxy wątku.

### <a name="remarks"></a>Uwagi

Zwykle [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) metoda wiąże proxy wątku do kontekstu wykonywania na żądanie. Istnieją jednak okoliczności, w których konieczne jest powiązanie kontekstu `SwitchTo` z wyprzedzeniem, aby upewnić się, że metoda przełącza się do już powiązanego kontekstu. Ma to miejsce w kontekście planowania usługi UMS, ponieważ nie można wywołać metod, które przydzielają pamięć i powiązania serwera proxy wątku może obejmować alokację pamięci, jeśli serwer proxy wątku nie jest łatwo dostępny w wolnej puli fabryki serwera proxy wątku.

`invalid_argument`jest generowany, `pContext` jeśli parametr `NULL`ma wartość .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>Metoda ISchedulerProxy::CreateOversubscriber

Tworzy nowy katalog główny procesora wirtualnego w wątku sprzętowym skojarzonym z istniejącym zasobem wykonawczym.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Parametry

*pWykoniczenieŹródło*<br/>
Interfejs `IExecutionResource` reprezentujący wątek sprzętowy, który ma subskrybować.

### <a name="return-value"></a>Wartość zwracana

Interfejs. `IVirtualProcessorRoot`

### <a name="remarks"></a>Uwagi

Tej metody należy użyć, gdy harmonogram chce oversubscribe określonego wątku sprzętowego przez ograniczony czas. Po zakończeniu pracy z katalogiem głównym procesora wirtualnego należy [Remove](iexecutionresource-structure.md#remove) zwrócić go `IVirtualProcessorRoot` do Menedżera zasobów, wywołując Remove metody w interfejsie.

Można nawet oversubscribe istniejącego katalogu głównego `IVirtualProcessorRoot` procesora wirtualnego, ponieważ interfejs dziedziczy z `IExecutionResource` interfejsu.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy::RequestInitialVirtualProcessors Metoda

Żąda początkowej alokacji katalogów głównych procesora wirtualnego. Każdy katalog główny procesora wirtualnego reprezentuje możliwość wykonania jednego wątku, który może wykonywać pracę dla harmonogramu.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Parametry

*doSubscribeCurrentThread*<br/>
Czy subskrybować bieżący wątek i uwzględnić go podczas alokacji zasobów.

### <a name="return-value"></a>Wartość zwracana

Interfejs `IExecutionResource` dla bieżącego wątku, `doSubscribeCurrentThread` jeśli parametr ma wartość **true**. Jeśli wartość jest **false**, metoda zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Zanim harmonogram wykona jakąkolwiek pracę, należy użyć tej metody, aby zażądać katalogów głównych procesora wirtualnego z Menedżera zasobów. Menedżer zasobów będzie uzyskiwał dostęp do zasad harmonogramu przy użyciu [funkcji IScheduler::GetPolicy](ischeduler-structure.md#getpolicy) i używał wartości dla `MinConcurrency`kluczy zasad oraz `MaxConcurrency` `TargetOversubscriptionFactor` określał, ile wątków sprzętowych należy początkowo przypisać do harmonogramu i ile katalogów głównych procesora wirtualnego utworzyć dla każdego wątku sprzętowego. Aby uzyskać więcej informacji na temat sposobu, w jaki zasady harmonogramu są używane do określania początkowej alokacji harmonogramu, zobacz [PolicyElementKey](concurrency-namespace-enums.md).

Menedżer zasobów udziela zasobów harmonogramowi, wywołując metodę [IScheduler::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) z listą katalogów głównych procesorów wirtualnych. Metoda jest wywoływana jako wywołanie zwrotne do harmonogramu, zanim ta metoda zwraca.

Jeśli harmonogram zażądał subskrypcji dla bieżącego wątku, ustawiając parametr `doSubscribeCurrentThread` na **true,** metoda zwraca `IExecutionResource` interfejs. Subskrypcja musi zostać zakończona w późniejszym momencie przy użyciu [IExecutionResource::Remove](iexecutionresource-structure.md#remove) metody.

Podczas określania, które wątki sprzętowe są zaznaczone, Menedżer zasobów podejmie próbę optymalizacji pod kątem koligacji węzła procesora. Jeśli subskrypcja jest wymagana dla bieżącego wątku, jest wskazanie, że bieżący wątek zamierza uczestniczyć w pracy przypisanej do tego harmonogramu. W takim przypadku przydzielone katalogi główne procesorów wirtualnych znajdują się w węźle procesora, na który wykonuje bieżący wątek, jeśli to możliwe.

Czynność subskrybowania wątku zwiększa poziom subskrypcji wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden po zakończeniu subskrypcji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy::Metoda zamykania

Powiadamia Menedżera zasobów, że harmonogram jest zamykany. Spowoduje to, że Menedżer zasobów natychmiast odzyskać wszystkie zasoby przyznane harmonogramowi.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Uwagi

Wszystkie `IExecutionContext` interfejsy harmonogramu odebrane w wyniku subskrybowania `ISchedulerProxy::RequestInitialVirtualProcessors` wątku zewnętrznego przy użyciu metod lub `ISchedulerProxy::SubscribeCurrentThread` muszą być zwrócone do Menedżera zasobów przy użyciu `IExecutionResource::Remove` przed harmonogram zamyka się w dół.

Jeśli harmonogram miał żadnych dezaktywowanych katalogów głównych procesora wirtualnego, należy je aktywować przy użyciu [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate), i mają serwery proxy wątku wykonywania na nich pozostawić `Dispatch` metodę kontekstów wykonywania, które są wywoływane przed wywołaniem `Shutdown` na serwerze proxy harmonogramu.

Nie jest konieczne dla harmonogramu indywidualnie zwrócić wszystkie katalogi główne procesora wirtualnego Menedżera `Remove` zasobów przyznane mu za pośrednictwem wywołań do metody, ponieważ wszystkie katalogi główne procesorów wirtualnych zostaną zwrócone do Menedżera zasobów w momencie zamykania.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy::SubscribeCurrentThread Metoda

Rejestruje bieżący wątek z Menedżerem zasobów, kojarząc go z tym harmonogramem.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Interfacing `IExecutionResource` reprezentujący bieżący wątek w czasie wykonywania.

### <a name="remarks"></a>Uwagi

Tej metody należy użyć, jeśli Menedżer zasobów ma uwzględniać bieżący wątek podczas przydzielania zasobów do harmonogramu i innych harmonogramów. Jest to szczególnie przydatne, gdy wątek planuje uczestniczyć w pracy w kolejce do harmonogramu, wraz z katalogami korzeniowymi procesora wirtualnego, które harmonogram otrzymuje od Menedżera zasobów. Menedżer zasobów używa informacji, aby zapobiec niepotrzebnemu nadsubskrypcji wątków sprzętowych w systemie.

Zasób wykonywania odebrany za pośrednictwem tej metody powinien zostać zwrócony do Menedżera zasobów przy użyciu [metody IExecutionResource::Remove.](iexecutionresource-structure.md#remove) Wątek, `Remove` który wywołuje metodę musi być ten `SubscribeCurrentThread` sam wątek, który wcześniej nazywał metodę.

Czynność subskrybowania wątku zwiększa poziom subskrypcji wątku sprzętowego o jeden. Poziom subskrypcji jest zmniejszany o jeden po zakończeniu subskrypcji. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>Metoda ISchedulerProxy::UnbindContext

Odłącza serwer proxy wątku od kontekstu wykonywania `pContext` określonego przez parametr i zwraca go do wolnej puli fabryki proxy wątku. Ta metoda może być wywoływana tylko w kontekście wykonywania, który został powiązany za pośrednictwem [metody ISchedulerProxy::BindContext](#bindcontext) i nie została jeszcze uruchomiona za pomocą `pContext` parametru wywołania metody [IThreadProxy::SwitchTo.](ithreadproxy-structure.md#switchto)

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Parametry

*Pcontext*<br/>
Kontekst wykonywania do odłączenia od jego serwera proxy wątku.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IThreadProxy, struktura](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager — Struktura](iresourcemanager-structure.md)
