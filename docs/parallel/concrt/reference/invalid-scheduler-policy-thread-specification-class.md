---
title: "invalid_scheduler_policy_thread_specification — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: concrt/concurrency::invalid_scheduler_policy_thread_specification
dev_langs: C++
helpviewer_keywords: invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82c53e760d09ecdcc39f50b30d68a6c0b5290c4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification — Klasa
Ta klasa opisuje wyjątek podczas próby ustawić limitów współbieżności `SchedulerPolicy` obiektu tak, aby wartość `MinConcurrency` klucza jest mniejsza niż wartość `MaxConcurrency` klucza.  
  
## <a name="syntax"></a>Składnia  
  
```
class invalid_scheduler_policy_thread_specification : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_scheduler_policy_thread_specification —] (nieprawidłowa — harmonogram — zasady — wartość class.md #ctor|Przeciążone. Konstruuje `invalid_scheduler_policy_value` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
##  <a name="ctor"></a>invalid_scheduler_policy_thread_specification — 

 Konstruuje `invalid_scheduler_policy_value` obiektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  

## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [SchedulerPolicy, klasa](schedulerpolicy-class.md)
