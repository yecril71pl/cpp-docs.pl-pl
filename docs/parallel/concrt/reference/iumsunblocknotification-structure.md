---
title: Iumsunblocknotification — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda4f6e2b0565d39fd604767f3a89bcdd9a6df2c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification — Struktura
Reprezentuje powiadomienie z Menedżera zasobów czy zablokowane i wyzwalane powrotu do harmonogramu wyznaczony planowania kontekstu serwera proxy wątek został odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, kiedy kontekstu wykonywania skojarzony proxy wątku zwrócone z `GetContext` zmiany harmonogramu metody.  
  
## <a name="syntax"></a>Składnia  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IUMSUnblockNotification::GetContext](#getcontext)|Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzonej z serwerem proxy wątku, który został odblokowany. Po powrocie z tej metody i zaplanowano podstawowej kontekstu wykonywania za pośrednictwem wywołania `IThreadProxy::SwitchTo` metody tego interfejsu nie jest już prawidłowy.|  
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|Zwraca następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h  
  
 **Namespace:** współbieżności  
  
##  <a name="getcontext"></a>  IUMSUnblockNotification::GetContext — metoda  
 Zwraca `IExecutionContext` interfejs dla kontekstu wykonywania skojarzonej z serwerem proxy wątku, który został odblokowany. Po powrocie z tej metody i zaplanowano podstawowej kontekstu wykonywania za pośrednictwem wywołania `IThreadProxy::SwitchTo` metody tego interfejsu nie jest już prawidłowy.  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IExecutionContext` Interfejs dla kontekstu wykonywania na serwerze proxy wątku, który został odblokowany.  
  
##  <a name="getnextunblocknotification"></a>  IUMSUnblockNotification::GetNextUnblockNotification — metoda  
 Zwraca następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Następne `IUMSUnblockNotification` interfejsu w łańcuchu zwrócona przez metodę `IUMSCompletionList::GetUnblockNotifications`.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Struktura IUMSScheduler](iumsscheduler-structure.md)   
 [IUMSCompletionList, struktura](iumscompletionlist-structure.md)
