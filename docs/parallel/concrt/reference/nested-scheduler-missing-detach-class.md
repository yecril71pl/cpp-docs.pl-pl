---
title: nested_scheduler_missing_detach — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26027693209bc5b4687686efeae5d190ed374607
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687364"
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
