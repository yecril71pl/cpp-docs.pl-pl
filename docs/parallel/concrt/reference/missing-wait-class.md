---
title: "missing_wait — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66feb4d39d08b4a9ae9b3a6099c32d2d15f1a5f1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="missingwait-class"></a>missing_wait — Klasa
Ta klasa opisuje wyjątek wywoływany, gdy nadal zaplanowane zadania `task_group` lub `structured_task_group` obiektów w czasie tego obiektu wykonuje destruktora. Ten wyjątek nigdy nie zostanie wygenerowany, jeśli osiągnięto destruktor ze względu na stosie rozwinięcia wyniku Wystąpił wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[missing_wait](#ctor)|Przeciążone. Konstruuje `missing_wait` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Brak przepływu wyjątek jest odpowiedzialny za wywoływanie albo `wait` lub `run_and_wait` metody `task_group` lub `structured_task_group` obiektu przed zezwoleniem na destruct tego obiektu. Środowisko uruchomieniowe zgłasza tego wyjątku, ponieważ oznacza to, że pamiętasz wywołać `wait` lub `run_and_wait` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> missing_wait — 

 Konstruuje `missing_wait` obiektu.  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [task_group — klasa](task-group-class.md)   
 [oczekiwania](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group, klasa](structured-task-group-class.md)
