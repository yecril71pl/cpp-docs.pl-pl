---
title: scheduler_worker_creation_error — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error
- CONCRT/concurrency::scheduler_worker_creation_error::scheduler_worker_creation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c81b62cee3a8c26b0d4ace61b8104f6eaee9db6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114387"
---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error — Klasa
Ta klasa opisuje wyjątek generowany z powodu błędu tworzenia kontekstu wykonywania procesu roboczego w środowisku uruchomieniowym współbieżności.  
  
## <a name="syntax"></a>Składnia  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_worker_creation_error](#ctor)|Przeciążone. Konstruuje `scheduler_worker_creation_error` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten wyjątek zazwyczaj jest zgłaszany, gdy wywołanie do systemu operacyjnego w celu tworzenia kontekstów wykonanie z w środowisku uruchomieniowym współbieżności: nie powiodło się. Kontekstami wykonywania są wątki, które są wykonywane zadania w środowisku uruchomieniowym współbieżności. Kod błędu, który normalnie zostałyby zwrócone w wyniku wywołania metody Win32 `GetLastError` jest konwertowana na wartość typu `HRESULT` i mogą być pobierane przy użyciu metody klasy bazowej `get_error_code`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> scheduler_worker_creation_error — 

 Konstruuje `scheduler_worker_creation_error` obiektu.  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
*_Message*<br/>
Opisowy komunikat dotyczący błędu.  
  
*_Hresult*<br/>
`HRESULT` Wartości błędu, który spowodował wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
