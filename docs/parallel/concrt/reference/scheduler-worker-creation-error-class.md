---
title: "scheduler_worker_creation_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs: C++
helpviewer_keywords: scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a628d0ce3d85a2bdcae9c7d25550cbd36386e67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error — Klasa
Ta klasa opisuje wyjątek z powodu błędu tworzenia kontekstu wykonywania procesu roboczego współbieżność środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_worker_creation_error —](#ctor)|Przeciążone. Konstruuje `scheduler_worker_creation_error` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zgłoszenia tego wyjątku, gdy wywołanie systemu operacyjnego do tworzenia kontekstów wykonywania z wewnątrz współbieżności środowiska wykonawczego nie powiodło się. Kontekst wykonywania są wątków, które wykonywać zadania współbieżność środowiska wykonawczego. Kod błędu, który zazwyczaj będzie zwracany po wywołaniu metody Win32 `GetLastError` jest konwertowana na wartość typu `HRESULT` i może być pobierane przy użyciu metody klasy podstawowej `get_error_code`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 [scheduler_resource_allocation_error —](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>scheduler_worker_creation_error — 

 Konstruuje `scheduler_worker_creation_error` obiektu.  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
 `_Hresult`  
 `HRESULT` Wartość błąd, który spowodował wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
