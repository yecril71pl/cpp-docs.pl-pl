---
title: "nested_scheduler_missing_detach — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0fdcc96de9e691d71a2ceaf36c87f843e5b4276
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach — Klasa
Ta klasa opisuje wyjątek wykrycie współbieżności środowiska wykonawczego nie zwrócił do wywołania `CurrentScheduler::Detach` metody w kontekście dołączonego do drugiego za pomocą harmonogramu `Attach` metody `Scheduler` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[nested_scheduler_missing_detach](#ctor)|Przeciążone. Konstruuje `nested_scheduler_missing_detach` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten wyjątek jest zgłaszany tylko wtedy, gdy zagnieździć jeden harmonogram wewnątrz innego wywołując `Attach` metody `Scheduler` obiektu w kontekście, który jest już własnością lub dołączony do innego harmonogramu. Współbieżności środowiska wykonawczego zgłasza tego wyjątku tylko wtedy, gdy jako pomoc do lokalizowania problem może wykryć scenariusza. Nie wszystkie wystąpienia pominięcia do wywołania `CurrentScheduler::Detach` metody jest gwarantowana ma zostać zgłoszony wyjątek.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> nested_scheduler_missing_detach 

 Konstruuje `nested_scheduler_missing_detach` obiektu.  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Scheduler, klasa](scheduler-class.md)
