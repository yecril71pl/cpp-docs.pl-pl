---
title: out_of_memory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab3285e0b37b8af93803a1a2752e25b6d91ab2f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695298"
---
# <a name="outofmemory-class"></a>out_of_memory — Klasa
Wyjątek zgłaszany, gdy metoda kończy się niepowodzeniem z powodu braku pamięci systemu lub urządzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[out_of_memory Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `out_of_memory` klasy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  
## <a name="ctor"></a> out_of_memory — 

 Inicjuje nowe wystąpienie klasy.  
  
### <a name="syntax"></a>Składnia  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Opis błędu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe wystąpienie klasy `out_of_memory` klasy.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
