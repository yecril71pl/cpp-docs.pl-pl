---
title: improper_lock — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
dev_langs:
- C++
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 903a24a6007eb8693584cfd4eed96bd12ef3cdda
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695603"
---
# <a name="improperlock-class"></a>improper_lock — Klasa
Ta klasa opisuje wyjątek, jeśli blokada jest nakładana nieprawidłowo.  
  
## <a name="syntax"></a>Składnia  
  
```
class improper_lock : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[improper_lock](#ctor)|Przeciążone. Konstruuje `improper_lock exception`.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas próby uzyskania blokady nie obsługującą rekursywnie na tym samym kontekście zazwyczaj zgłoszenia tego wyjątku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `improper_lock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> improper_lock — 

 Konstruuje `improper_lock exception`.  
  
```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [critical_section — klasa](critical-section-class.md)   
 [reader_writer_lock, klasa](reader-writer-lock-class.md)
