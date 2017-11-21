---
title: "invalid_oversubscribe_operation — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs: C++
helpviewer_keywords: invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb8bb8d7031cda89dd74637638062f4cdce692b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[invalid_oversubscribe_operation —](#ctor)|Przeciążone. Konstruuje `invalid_oversubscribe_operation` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>invalid_oversubscribe_operation — 

 Konstruuje `invalid_oversubscribe_operation` obiektu.  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
