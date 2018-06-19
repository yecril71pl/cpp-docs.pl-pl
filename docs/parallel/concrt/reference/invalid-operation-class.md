---
title: invalid_operation — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa6d1152bb1f9a9c5671d1f7f0cdf0e426c02575
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696100"
---
# <a name="invalidoperation-class"></a>invalid_operation — Klasa
Ta klasa opisuje Wystąpił wyjątek zgłoszony, gdy ta operacja jest wykonywana, których nie opisano dokładniej przez inny typ wyjątków zgłaszanych przez współbieżności środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class invalid_operation : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_operation —](#ctor)|Przeciążone. Konstruuje `invalid_operation` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Różne metody, które generują ten wyjątek zostanie zazwyczaj dokumentu w jakich okolicznościach one zgłosi go.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_operation`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> invalid_operation — 

 Konstruuje `invalid_operation` obiektu.  
  
```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
