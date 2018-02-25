---
title: "invalid_oversubscribe_operation — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 584cda20a30ea413afebc9fda00191e32dec9635
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation — Klasa
Ta klasa opisuje wyjątek wywoływany, gdy `Context::Oversubscribe` metoda jest wywoływana z `_BeginOversubscription` ustawiona `false` bez uprzedniego wywołania `Context::Oversubscribe` metody z `_BeginOversubscription` ustawiono parametr `true`.  
  
## <a name="syntax"></a>Składnia  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_oversubscribe_operation](#ctor)|Przeciążone. Konstruuje `invalid_oversubscribe_operation` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> invalid_oversubscribe_operation — 

 Konstruuje `invalid_oversubscribe_operation` obiektu.  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
