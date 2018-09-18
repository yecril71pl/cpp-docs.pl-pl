---
title: uninitialized_object — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 821f3c25d195a2c92ac04fdf5f9e5a59b493c257
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113841"
---
# <a name="uninitializedobject-class"></a>uninitialized_object — Klasa
Wyjątek, który jest zgłaszany, gdy używany jest obiekt niezainicjowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
class uninitialized_object : public runtime_exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[uninitialized_object — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `uninitialized_object` klasy.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  
## <a name="uninitialized_object__ctor"></a> unsupported_feature 

Tworzy nowe wystąpienie nieobsługiwanego wyjątku unsupported_feature.  
  
### <a name="syntax"></a>Składnia  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>Parametry  
*_Message*<br/>
Opis błędu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `unsupported_feature` Obiektu. 

## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
