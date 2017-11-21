---
title: "improper_scheduler_attach — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
dev_langs: C++
helpviewer_keywords: improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c33190f973ace4492597ddd1309297516c7415a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach — Klasa
Ta klasa opisuje wyjątek wywoływany, gdy `Attach` wywoływana jest metoda `Scheduler` obiektu, który jest już dołączony do bieżącego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```
class improper_scheduler_attach : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[improper_scheduler_attach —](#ctor)|Przeciążone. Konstruuje `improper_scheduler_attach` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `improper_scheduler_attach`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>improper_scheduler_attach — 

 Konstruuje `improper_scheduler_attach` obiektu.  
  
```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [Klasa harmonogramu](scheduler-class.md)
