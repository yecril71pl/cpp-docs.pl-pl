---
title: invalid_scheduler_policy_value — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae46d9f9de26e80a97d4ea2e9a692caec3445c75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068159"
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value — Klasa
Ta klasa opisuje wyjątek generowany, gdy klucz zasad `SchedulerPolicy` obiekt jest ustawiony na nieprawidłową wartość dla tego klucza.  
  
## <a name="syntax"></a>Składnia  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|Przeciążone. Konstruuje `invalid_scheduler_policy_value` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value 

 Konstruuje `invalid_scheduler_policy_value` obiektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_Message*<br/>
Opisowy komunikat dotyczący błędu.  
  

## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [SchedulerPolicy, klasa](schedulerpolicy-class.md)
