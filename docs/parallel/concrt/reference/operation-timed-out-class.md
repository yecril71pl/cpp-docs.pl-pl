---
title: operation_timed_out — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
dev_langs:
- C++
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af30dd9d7ff6ac64d6c0659520a6e7a15f2d0d93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116656"
---
# <a name="operationtimedout-class"></a>operation_timed_out — Klasa
Ta klasa opisuje wyjątek generowany, gdy upłynął limit czasu operacji.  
  
## <a name="syntax"></a>Składnia  
  
```
class operation_timed_out : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operation_timed_out](#ctor)|Przeciążone. Konstruuje `operation_timed_out` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `operation_timed_out`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> operation_timed_out — 

 Konstruuje `operation_timed_out` obiektu.  
  
```
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_Message*<br/>
Opisowy komunikat dotyczący błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
