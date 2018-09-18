---
title: Iexecutioncontext — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3f33cf98adc011d872a7d71246e6b94afaf4cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059787"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext — Struktura
Interfejs do kontekstu wykonywania, który można uruchomić przy użyciu danego procesora wirtualnego i być wspólne przełączania kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IExecutionContext::Dispatch](#dispatch)|Metoda, która jest wywoływana, gdy wątek serwera proxy, który rozpoczyna się wykonywanie kontekstu wykonania określonego. Powinna to być procedury głównego procesu roboczego dla harmonogramu.|  
|[IExecutionContext::GetId](#getid)|Zwraca unikatowy identyfikator dla kontekstu wykonywania.|  
|[IExecutionContext::GetProxy](#getproxy)|Zwraca interfejs do serwera proxy wątku, który jest wykonywany w tym kontekście.|  
|[IExecutionContext::GetScheduler](#getscheduler)|Zwraca interfejs umożliwiający do harmonogramu należy tego kontekstu wykonywania.|  
|[IExecutionContext::SetProxy](#setproxy)|Kojarzy wątek serwera proxy przy użyciu tego kontekstu wykonywania. Serwer proxy wątku skojarzonego wywołuje to prawo metoda przed jej rozpoczęciem, wykonania z kontekstu `Dispatch` metody.|  
  
## <a name="remarks"></a>Uwagi  
 Przed zaimplementowaniem Niestandardowy harmonogram, który interfejsy za pomocą Menedżera zasobów Runtime współbieżności, należy zaimplementować `IExecutionContext` interfejsu. Utworzone przez Menedżera zasobów wątki wykonywania pracy imieniu harmonogramu, wykonując `IExecutionContext::Dispatch` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IExecutionContext`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dispatch"></a>  Iexecutioncontext::Dispatch — metoda  
 Metoda, która jest wywoływana, gdy wątek serwera proxy, który rozpoczyna się wykonywanie kontekstu wykonania określonego. Powinna to być procedury głównego procesu roboczego dla harmonogramu.  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pDispatchState*<br/>
Wskaźnik do stanu, w którym wywoływane jest ten kontekst wykonywania. Aby uzyskać więcej informacji na temat stanu wysyłania, zobacz [dispatchstate —](dispatchstate-structure.md).  
  
##  <a name="getid"></a>  Iexecutioncontext::getid — metoda  
 Zwraca unikatowy identyfikator dla kontekstu wykonywania.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy liczby całkowitej.  
  
### <a name="remarks"></a>Uwagi  
 Należy użyć metody `GetExecutionContextId` uzyskać unikatowy identyfikator obiektu, który implementuje `IExecutionContext` interfejsu, zanim użyjesz interfejsu jako parametr do metody dostarczone przez Menedżera zasobów. Powinna zwrócić element tego samego identyfikatora po `GetId` wywołaniu funkcji.  
  
 Identyfikator pochodzi z innego źródła może spowodować niezdefiniowane zachowanie.  
  
##  <a name="getproxy"></a>  Iexecutioncontext::getproxy — metoda  
 Zwraca interfejs do serwera proxy wątku, który jest wykonywany w tym kontekście.  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IThreadProxy` Interfejsu. Jeśli serwer proxy wątku kontekstu wykonania nie została zainicjowana przy użyciu wywołania do `SetProxy`, funkcja musi zwracać `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Wywoła usługi Resource Manager `SetProxy` metodę w kontekście wykonywania za pomocą `IThreadProxy` interfejsu jako parametru, przed rozpoczęciem `Dispatch` metody w kontekście. Mają być przechowywanie tego argumentu i zwrot wywołania `GetProxy()`.  
  
##  <a name="getscheduler"></a>  Iexecutioncontext::getscheduler — metoda  
 Zwraca interfejs umożliwiający do harmonogramu należy tego kontekstu wykonywania.  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IScheduler` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Należy zainicjować kontekstu wykonywania przy użyciu prawidłowego `IScheduler` interfejsu, zanim użyjesz go jako parametr do metody dostarczone przez Menedżera zasobów.  
  
##  <a name="setproxy"></a>  Iexecutioncontext::setproxy — metoda  
 Kojarzy wątek serwera proxy przy użyciu tego kontekstu wykonywania. Serwer proxy wątku skojarzonego wywołuje to prawo metoda przed jej rozpoczęciem, wykonania z kontekstu `Dispatch` metody.  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*pThreadProxy*<br/>
Interfejs do serwera proxy wątku, który ma wprowadź `Dispatch` metody w tym kontekście wykonania.  
  
### <a name="remarks"></a>Uwagi  
 Oczekuje można zapisać parametru `pThreadProxy` i zwrócić go w wywołaniu `GetProxy` metody. Menedżer zasobów gwarantuje proxy wątku skojarzonego z kontekstem wykonywania nie ulegnie zmianie podczas wykonywania proxy wątku `Dispatch` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IScheduler, struktura](ischeduler-structure.md)   
 [IThreadProxy, struktura](ithreadproxy-structure.md)
