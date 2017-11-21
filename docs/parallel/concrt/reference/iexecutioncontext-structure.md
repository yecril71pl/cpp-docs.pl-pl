---
title: "Iexecutioncontext — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs: C++
helpviewer_keywords: IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af687c482ee3565d7b350672b83291194a2edf44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext — Struktura
Interfejs do kontekstu wykonywania, który można uruchomić na danym procesorów wirtualnych i wspólnie można przełączyć kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IExecutionContext::Dispatch](#dispatch)|Metoda wywoływana, gdy serwer proxy wątku rozpoczyna wykonanie określonego kontekstu wykonywania. Powinno to być procedury głównego procesu roboczego z harmonogramu.|  
|[IExecutionContext::GetId](#getid)|Zwraca unikatowy identyfikator kontekstu wykonywania.|  
|[IExecutionContext::GetProxy](#getproxy)|Zwraca interfejs do serwera proxy w wątku, który jest wykonywany w tym kontekście.|  
|[IExecutionContext::GetScheduler](#getscheduler)|Zwraca interfejs do harmonogramu należy tego kontekstu wykonywania.|  
|[IExecutionContext::SetProxy](#setproxy)|Kojarzy proxy wątku z tego kontekstu wykonywania. Proxy wątek skojarzony wywołuje prawo to metoda, przed rozpoczęciem wykonywania kontekstu `Dispatch` metody.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wdrażania Niestandardowy harmonogram, który interfejsy za pomocą Menedżera zasobów współbieżność środowiska wykonawczego, musisz zaimplementować `IExecutionContext` interfejsu. Utworzone przez Menedżera zasobów wątki wykonywania pracy w imieniu użytkownika harmonogramu, wykonując `IExecutionContext::Dispatch` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IExecutionContext`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dispatch"></a>IExecutionContext::Dispatch — metoda  
 Metoda wywoływana, gdy serwer proxy wątku rozpoczyna wykonanie określonego kontekstu wykonywania. Powinno to być procedury głównego procesu roboczego z harmonogramu.  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pDispatchState`  
 Wskaźnik do stanu, w którym wysyłany jest ten kontekst wykonywania. Aby uzyskać więcej informacji na stan wysyłania, zobacz [dispatchstate —](dispatchstate-structure.md).  
  
##  <a name="getid"></a>IExecutionContext::GetId — metoda  
 Zwraca unikatowy identyfikator kontekstu wykonywania.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy liczby całkowitej.  
  
### <a name="remarks"></a>Uwagi  
 Należy użyć metody `GetExecutionContextId` uzyskać unikatowy identyfikator dla obiekt, który implementuje `IExecutionContext` interfejsu, przed użyciem interfejsu jako parametr metody dostarczone przez Menedżera zasobów. Powinna zwrócić element tego samego identyfikatora po `GetId` funkcja jest wywoływana.  
  
 Identyfikator pochodzi z innego źródła może spowodować niezdefiniowane zachowanie.  
  
##  <a name="getproxy"></a>IExecutionContext::GetProxy — metoda  
 Zwraca interfejs do serwera proxy w wątku, który jest wykonywany w tym kontekście.  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IThreadProxy` Interfejsu. Jeśli nie zainicjowano kontekstu wykonywania wątku proxy wywołaniem `SetProxy`, funkcja musi zwracać `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Wywoła Resource Manager `SetProxy` metody dla kontekstu wykonywania z `IThreadProxy` interfejsu jako parametru, przed wprowadzeniem `Dispatch` metoda w kontekście. Oczekiwano do przechowywania tego argumentu i przywrócić go na wywołania `GetProxy()`.  
  
##  <a name="getscheduler"></a>IExecutionContext::GetScheduler — metoda  
 Zwraca interfejs do harmonogramu należy tego kontekstu wykonywania.  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IScheduler` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Należy zainicjować kontekstu wykonywania z prawidłowym `IScheduler` interfejsu przed użyciem go jako parametru do metody dostarczone przez Menedżera zasobów.  
  
##  <a name="setproxy"></a>IExecutionContext::SetProxy — metoda  
 Kojarzy proxy wątku z tego kontekstu wykonywania. Proxy wątek skojarzony wywołuje prawo to metoda, przed rozpoczęciem wykonywania kontekstu `Dispatch` metody.  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pThreadProxy`  
 Interfejs do serwera proxy w wątku, który ma wprowadź `Dispatch` metody dla tego kontekstu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Oczekiwano można zapisać parametru `pThreadProxy` i przywrócić go na wywołanie `GetProxy` metody. Menedżer zasobów gwarantuje proxy wątek skojarzony z kontekstu wykonywania nie spowoduje zmiany podczas wykonywania jest serwer proxy wątku `Dispatch` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Struktura IScheduler](ischeduler-structure.md)   
 [Ithreadproxy — struktura](ithreadproxy-structure.md)
