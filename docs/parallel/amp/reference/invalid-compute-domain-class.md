---
title: invalid_compute_domain — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
dev_langs:
- C++
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 588f12e04f3a2833da6d67c07ab41929d916a4b5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705214"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain — Klasa
Wyjątek zgłaszany, gdy środowisko uruchomieniowe nie może uruchomić jądra przy użyciu określonych w domenie obliczeniowej [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) wywołania.  

  
## <a name="syntax"></a>Składnia  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[invalid_compute_domain Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `invalid_compute_domain` klasy.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  

## <a name="ctor"></a> invalid_compute_domain — 

Inicjuje nowe wystąpienie klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit invalid_compute_domain(  
    const char * _Message ) throw();  
  
invalid_compute_domain() throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Opis błędu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wystąpienie `invalid_compute_domain` — klasa  
    
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
