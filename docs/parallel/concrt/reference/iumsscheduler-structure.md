---
title: Struktura IUMSScheduler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs:
- C++
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da35fe5ae8d00ee537674fd689fd7f27074b0355
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="iumsscheduler-structure"></a>Struktura IUMSScheduler
Interfejs abstrakcję harmonogram pracy, który chce współbieżność środowiska wykonawczego Resource Manager ręcznie, jego schedulable wątków (UMS) trybu użytkownika. Menedżer zasobów używa tego interfejsu do komunikowania się z planiści wątku UMS. `IUMSScheduler` Dziedziczy interfejs `IScheduler` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Przypisuje `IUMSCompletionList` interfejs do harmonogramu UMS wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli w przypadku implementowania niestandardowych harmonogramu, który komunikuje się z Menedżerem zasobów, i chcesz UMS wątków jest przekazywany z harmonogramu zamiast zwykłego wątków Win32, powinien zapewniać implementację elementu `IUMSScheduler` interfejsu. Ponadto należy ustawić wartość klucza zasad harmonogramu `SchedulerKind` jako `UmsThreadDefault`. Jeśli zasady określają wątku UMS `IScheduler` interfejs, który jest przekazywany jako parametr [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) metoda musi być `IUMSScheduler` interfejsu.  
  
 Menedżer zasobów jest w stanie ręcznie, musisz wątków UMS tylko w systemach operacyjnych, które funkcja UMS. 64-bitowe systemy operacyjne z wersją systemu Windows 7 i nowsze wersje obsługują UMS wątków. W przypadku utworzenia zasad harmonogramu z `SchedulerKind` klucza ustawioną wartość `UmsThreadDefault` i platforma podstawowa nie obsługuje UMS, wartość `SchedulerKind` klucza na te zasady zostaną zmienione na wartość `ThreadScheduler`. Należy zawsze przeczytać powrotem tej wartości zasad przed oczekuje UMS wątków.  
  
 `IUMSScheduler` Interfejs jest jeden element end dwukierunkowy kanał komunikacji między harmonogramu i Menedżera zasobów. Drugi punkt końcowy jest reprezentowana przez `IResourceManager` i `ISchedulerProxy` interfejsów implementowanych przez Menedżera zasobów.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="setcompletionlist"></a>  IUMSScheduler::SetCompletionList — metoda  
 Przypisuje `IUMSCompletionList` interfejs do harmonogramu UMS wątku.  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pCompletionList`  
 Interfejs listy uzupełniania dla harmonogramu. Brak jedną listę według harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Menedżer zasobów będzie wywołania tej metody na harmonogram, który określa, że chce wątków UMS po planista zażądał początkowej alokacji zasobów. Harmonogram można użyć `IUMSCompletionList` interfejsu, aby określić, kiedy serwery proxy wątku UMS ma odblokowany. Jest on prawidłowy tylko dostęp do tego interfejsu z serwera proxy wątku uruchomiona na głównym procesorów wirtualnych przypisanych do harmonogramu UMS.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Policyelementkey —](concurrency-namespace-enums.md)   
 [Struktura IScheduler](ischeduler-structure.md)   
 [Iumscompletionlist — struktura](iumscompletionlist-structure.md)   
 [IResourceManager, struktura](iresourcemanager-structure.md)
