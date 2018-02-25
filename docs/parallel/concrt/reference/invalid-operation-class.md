---
title: "invalid_operation — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97a62460dca6ab79672075e50f34ce8923239d1a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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
  
##  <a name="ctor">invalid_operation —</a> 

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
