---
title: "Message — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
dev_langs: C++
helpviewer_keywords: message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55d1744d67156bcfcf6f76c757fc97ab0d4fd380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="message-class"></a>message — Klasa
Koperty wiadomości podstawowe zawierającego ładunek danych są przekazywane między bloki komunikatów.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ładunku w komunikacie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`type`|Alias typu `T`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[komunikat](#ctor)|Przeciążone. Konstruuje `message` obiektu.|  
|[~ message — destruktor](#dtor)|Niszczy `message` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[add_ref](#add_ref)|Dodaje do liczebności referencyjnej dla `message` obiektu. Używany dla bloków komunikatów, wymagające zliczanie ustalenie okresy istnienia komunikatu.|  
|[msg_id](#msg_id)|Zwraca identyfikator `message` obiektu.|  
|[remove_ref](#remove_ref)|Odejmuje z licznika odwołań do `message` obiektu. Używany dla bloków komunikatów, wymagające zliczanie ustalenie okresy istnienia komunikatu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ładunek](#payload)|Ładunek `message` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `message`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  
  
 **Namespace:** współbieżności  
  
##  <a name="add_ref"></a>add_ref 

 Dodaje do liczebności referencyjnej dla `message` obiektu. Używany dla bloków komunikatów, wymagające zliczanie ustalenie okresy istnienia komunikatu.  
  
```
long add_ref();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa wartość liczebności referencyjnej.  
  
##  <a name="ctor"></a>Komunikat 

 Konstruuje `message` obiektu.  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_P`  
 Obciążenie tego komunikatu.  
  
 `_Id`  
 Unikatowy identyfikator tej wiadomości.  
  
 `_Msg`  
 Odwołanie lub wskaźnik do `message` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor, który pobiera wskaźnik do `message` obiekt jako argument zgłasza [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_Msg` jest `NULL`.  
  
##  <a name="dtor"></a>~ wiadomości 

 Niszczy `message` obiektu.  
  
```
virtual ~message();
```  
  
##  <a name="msg_id"></a>msg_id 

 Zwraca identyfikator `message` obiektu.  
  
```
runtime_object_identity msg_id() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `runtime_object_identity` z `message` obiektu.  
  
##  <a name="payload"></a>ładunek 

 Ładunek `message` obiektu.  
  
```
T const payload;
```  
  
##  <a name="remove_ref"></a>remove_ref 

 Odejmuje z licznika odwołań do `message` obiektu. Używany dla bloków komunikatów, wymagające zliczanie ustalenie okresy istnienia komunikatu.  
  
```
long remove_ref();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa wartość liczebności referencyjnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
