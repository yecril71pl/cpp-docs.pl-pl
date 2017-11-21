---
title: "invalid_scheduler_policy_value — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: concrt/concurrency::invalid_scheduler_policy_value
dev_langs: C++
helpviewer_keywords: invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc8d6a06d578169cb60bc757c1719b7028e12b06
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value — Klasa
Ta klasa opisuje wyjątek po klucz zasad `SchedulerPolicy` obiektu ma ustawioną nieprawidłową wartością dla tego klucza.  
  
## <a name="syntax"></a>Składnia  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_scheduler_policy_value —] (invalid-scheduler-policy-thread-specification-class.md#ctor|Przeciążone. Konstruuje `invalid_scheduler_policy_value` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
    
##  <a name="ctor"></a>invalid_scheduler_policy_value — 

 Konstruuje `invalid_scheduler_policy_value` obiektu.  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  

## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Schedulerpolicy — klasa](schedulerpolicy-class.md)
