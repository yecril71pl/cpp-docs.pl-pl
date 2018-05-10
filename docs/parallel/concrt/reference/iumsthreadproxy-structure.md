---
title: Iumsthreadproxy — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbba2955adc14ef73a0ba9932756ace57c4136e6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy — Struktura
Abstrakcja dla wątku wykonywania. Jeśli Twoje harmonogramu przyznawane schedulable wątków (UMS) trybu użytkownika, należy ustawić wartość elementu zasad harmonogramu `SchedulerKind` do `UmsThreadDefault`i wdrożenie `IUMSScheduler` interfejsu. Wątki UMS są tylko w obsługiwanych systemach operacyjnych 64-bitowej wersji systemu Windows 7 lub nowszy.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Wywołuje się, aby krytyczne regionu. Po obszarze krytycznych, harmonogramu nie zostanie obserwować operacji asynchronicznych blokujące, które mają miejsce podczas regionu. Oznacza to, że harmonogram zostanie nie można ponownie wprowadzić hasło dla błędów stron, zawieszenia wątku, wywołania procedur asynchronicznych jądra (APCs) i tak dalej, wątku UMS.|  
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Wywołuje się, aby hyper krytyczne regionu. Po obszarze hyper krytycznych, harmonogramu nie zostanie obserwować żadnych operacji blokujące, które mają miejsce podczas regionu. Oznacza to, że nie będzie trzeba ponownie wprowadzić planista dotyczące blokowania wywołania funkcji, prób przejęcie blokady z bloków, błędów stron wątku zawieszenia wywołań procedur asynchronicznych jądra (APCs) i dlatego określonymi dla UMS wątku.|  
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Wywołuje się, aby można było zakończyć krytyczne regionu.|  
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Wywołuje się, aby zakończyć działanie funkcji hyper krytyczne regionu.|  
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Zwraca jakiego rodzaju krytyczne region proxy wątek znajduje się w. Ponieważ hyper krytyczne regiony są podzbiorem krytyczne regionach, jeśli wprowadzony kod krytyczne region, a następnie obszarem hyper krytyczne `InsideHyperCriticalRegion` zostaną zwrócone.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="entercriticalregion"></a>  IUMSThreadProxy::EnterCriticalRegion — metoda  
 Wywołuje się, aby krytyczne regionu. Po obszarze krytycznych, harmonogramu nie zostanie obserwować operacji asynchronicznych blokujące, które mają miejsce podczas regionu. Oznacza to, że harmonogram zostanie nie można ponownie wprowadzić hasło dla błędów stron, zawieszenia wątku, wywołania procedur asynchronicznych jądra (APCs) i tak dalej, wątku UMS.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa głębokość krytyczne regionu. Krytyczne regiony są współużytkowane.  
  
##  <a name="enterhypercriticalregion"></a>  IUMSThreadProxy::EnterHyperCriticalRegion — metoda  
 Wywołuje się, aby hyper krytyczne regionu. Po obszarze hyper krytycznych, harmonogramu nie zostanie obserwować żadnych operacji blokujące, które mają miejsce podczas regionu. Oznacza to, że nie będzie trzeba ponownie wprowadzić planista dotyczące blokowania wywołania funkcji, prób przejęcie blokady z bloków, błędów stron wątku zawieszenia wywołań procedur asynchronicznych jądra (APCs) i dlatego określonymi dla UMS wątku.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa głębokość hyper krytyczne regionu. Krytyczne Hyper regiony są współużytkowane.  
  
### <a name="remarks"></a>Uwagi  
 Planista musi być bardzo rozważnie korzystać z metod wywoływanych przez nią i co umożliwia zablokowanie uzyskuje tych regionów. Jeśli kod w regionie na blokuje na blokadę przechowywana przez coś się, że harmonogram jest odpowiedzialny za planowanie, może nastąpić zakleszczenia.  
  
##  <a name="exitcriticalregion"></a>  IUMSThreadProxy::ExitCriticalRegion — metoda  
 Wywołuje się, aby można było zakończyć krytyczne regionu.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa głębokość krytyczne regionu. Krytyczne regiony są współużytkowane.  
  
##  <a name="exithypercriticalregion"></a>  IUMSThreadProxy::ExitHyperCriticalRegion — metoda  
 Wywołuje się, aby zakończyć działanie funkcji hyper krytyczne regionu.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa głębokość hyper krytyczne regionu. Krytyczne Hyper regiony są współużytkowane.  
  
##  <a name="getcriticalregiontype"></a>  IUMSThreadProxy::GetCriticalRegionType — metoda  
 Zwraca jakiego rodzaju krytyczne region proxy wątek znajduje się w. Ponieważ hyper krytyczne regiony są podzbiorem krytyczne regionach, jeśli wprowadzony kod krytyczne region, a następnie obszarem hyper krytyczne `InsideHyperCriticalRegion` zostaną zwrócone.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ krytyczne regionu proxy wątek jest w ciągu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [IUMSScheduler, struktura](iumsscheduler-structure.md)
