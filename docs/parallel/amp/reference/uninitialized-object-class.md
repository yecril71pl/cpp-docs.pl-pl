---
title: "uninitialized_object — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs: C++
helpviewer_keywords: uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7c0e30cefa99a52d0dfbc0725c3274e52f2a76c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="uninitializedobject-class"></a>uninitialized_object — Klasa
Wyjątek zgłaszany, gdy jest używany niezainicjowanego obiektu.  
  
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
## <a name="uninitialized_object__ctor"></a>unsupported_feature — 

Tworzy nowe wystąpienie klasy unsupported_feature — wyjątek.  
  
### <a name="syntax"></a>Składnia  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Opis błędu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `unsupported_feature` Obiektu. 

## <a name="see-also"></a>Zobacz też  
 [Namespace współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
