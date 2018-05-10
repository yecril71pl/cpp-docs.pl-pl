---
title: bad_target — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be10e5e4105dd16a68ad2854538d6181e90bfbe9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="badtarget-class"></a>bad_target — Klasa
Ta klasa opisuje wyjątek wywoływany, gdy blok komunikatów jest wskaźnik do obiektu docelowego, która jest nieprawidłowa dla wykonywanej operacji.  
  
## <a name="syntax"></a>Składnia  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[bad_target](#ctor)|Przeciążone. Konstruuje `bad_target` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Powodów takich, jak docelowy próby wykorzystania komunikat, który jest zarezerwowana do innej docelowej lub zwalniania zastrzeżenia, który nie ma zwykle zgłoszenia tego wyjątku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> bad_target — 

 Konstruuje `bad_target` obiektu.  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md)



