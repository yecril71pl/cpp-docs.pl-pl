---
title: "message_processor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs: C++
helpviewer_keywords: message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f93763a3d29e19feaa110b336c4cc9bb832539d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="messageprocessor-class"></a>message_processor — Klasa
`message_processor` Klasa jest abstrakcyjna klasa podstawowa dla przetwarzania `message` obiektów. Nie ma żadnej gwarancji z kolejnością wiadomości.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ładunku w komunikaty obsługiwane przez to `message_processor` obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`type`|Alias typu `T`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[async_send](#async_send)|W przypadku przesłonięcia w klasie pochodnej, umieszcza wiadomości w bloku asynchronicznie.|  
|[sync_send](#sync_send)|W przypadku przesłonięcia w klasie pochodnej, umieszcza wiadomości w bloku synchronicznie.|  
|[oczekiwania](#wait)|W przypadku przesłonięcia w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|W przypadku przesłonięcia w klasie pochodnej, przetwarza przekazywania wiadomości w bloku. Wywoływana raz za każdym razem zostanie dodany nowy komunikat i można odnaleźć kolejki muszą być puste.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `message_processor`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="async_send"></a>async_send 

 W przypadku przesłonięcia w klasie pochodnej, umieszcza wiadomości w bloku asynchronicznie.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 A `message` obiektu do wysłania asynchronicznie.  
  
### <a name="remarks"></a>Uwagi  
 Procesor implementacje powinny przesłaniać tę metodę.  
  
##  <a name="process_incoming_message"></a>process_incoming_message 

 W przypadku przesłonięcia w klasie pochodnej, przetwarza przekazywania wiadomości w bloku. Wywoływana raz za każdym razem zostanie dodany nowy komunikat i można odnaleźć kolejki muszą być puste.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Komunikat bloku implementacje powinny przesłaniać tę metodę.  
  
##  <a name="sync_send"></a>sync_send 

 W przypadku przesłonięcia w klasie pochodnej, umieszcza wiadomości w bloku synchronicznie.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 A `message` obiektu do wysłania synchronicznie.  
  
### <a name="remarks"></a>Uwagi  
 Procesor implementacje powinny przesłaniać tę metodę.  
  
##  <a name="wait"></a>oczekiwania 

 W przypadku przesłonięcia w klasie pochodnej, czeka na zakończenie wszystkich operacji asynchronicznych.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Uwagi  
 Procesor implementacje powinny przesłaniać tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [ordered_message_processor — klasa](ordered-message-processor-class.md)
