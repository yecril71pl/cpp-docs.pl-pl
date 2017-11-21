---
title: "scheduler_resource_allocation_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
dev_langs: C++
helpviewer_keywords: scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 334712def2fbd458b648b02cbfab05e202cc0e1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error — Klasa
Ta klasa opisuje wyjątek z powodu błędu można uzyskać zasobu krytycznego współbieżność środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class scheduler_resource_allocation_error : public std::exception;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[scheduler_resource_allocation_error —](#ctor)|Przeciążone. Konstruuje `scheduler_resource_allocation_error` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_error_code](#get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle zgłoszenia tego wyjątku, gdy wywołanie systemu operacyjnego ze współbieżności środowiska wykonawczego nie powiodło się. Kod błędu, który zazwyczaj będzie zwracany po wywołaniu metody Win32 `GetLastError` jest konwertowana na wartość typu `HRESULT` i może być pobierane przy użyciu `get_error_code` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="get_error_code"></a>get_error_code 

 Zwraca kod błędu, który spowodował wyjątek.  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HRESULT` Wartość błąd, który spowodował wyjątek.  
  
##  <a name="ctor"></a>scheduler_resource_allocation_error — 

 Konstruuje `scheduler_resource_allocation_error` obiektu.  
  
```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
 `_Hresult`  
 `HRESULT` Wartość błąd, który spowodował wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
