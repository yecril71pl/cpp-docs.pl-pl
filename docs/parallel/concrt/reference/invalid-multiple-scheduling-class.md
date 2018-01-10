---
title: "invalid_multiple_scheduling — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs: C++
helpviewer_keywords: invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa021ec655162cb75837ac1475e5cb9094f79fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling — Klasa
Ta klasa opisuje wyjątek wywoływany, gdy `task_handle` obiekt jest zaplanowane wiele razy przy użyciu `run` metody `task_group` lub `structured_task_group` obiektu bez wywołania pośredniczące `wait` lub `run_and_wait` metody.  
  
## <a name="syntax"></a>Składnia  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_multiple_scheduling —](#ctor)|Przeciążone. Konstruuje `invalid_multiple_scheduling` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>invalid_multiple_scheduling — 

 Konstruuje `invalid_multiple_scheduling` obiektu.  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [task_handle — klasa](task-handle-class.md)   
 [task_group — klasa](task-group-class.md)   
 [Uruchom](task-group-class.md)   
 [oczekiwania](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group, klasa](structured-task-group-class.md)
