---
title: "unsupported_feature — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
dev_langs: C++
helpviewer_keywords: unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2d9a85d0ca9b6ff952d6f7ae6420bedfabea5289
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unsupportedfeature-class"></a>unsupported_feature — Klasa
Wyjątek zgłaszany, gdy jest używany nieobsługiwanej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[unsupported_feature — Konstruktor](#ctor)|Tworzy nowe wystąpienie klasy `unsupported_feature` wyjątku.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## <a name="unsupported_feature__ctor"></a>unsupported_feature — 

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
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
