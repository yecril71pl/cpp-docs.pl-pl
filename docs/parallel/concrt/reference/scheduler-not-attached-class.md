---
title: "scheduler_not_attached — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
dev_langs:
- C++
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2671479d51c703dc4c0d0ab01b8036a130497ac6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="schedulernotattached-class"></a>scheduler_not_attached — Klasa
Ta klasa opisuje wyjątek, jeśli operacja została wykonana, co wymaga harmonogramu jest dołączony do bieżącego kontekstu i jedna nie jest.  
  
## <a name="syntax"></a>Składnia  
  
```
class scheduler_not_attached : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_not_attached](#ctor)|Przeciążone. Konstruuje `scheduler_not_attached` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `scheduler_not_attached`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> scheduler_not_attached 

 Konstruuje `scheduler_not_attached` obiektu.  
  
```
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Scheduler, klasa](scheduler-class.md)
