---
title: "cancellation_token_source — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
dev_langs: C++
helpviewer_keywords: cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5335b36e9ac80399a965c3717fcc0f5c2bab1fa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source — Klasa
`cancellation_token_source` Klasa reprezentuje możliwości można anulować operacji anulowania.  
  
## <a name="syntax"></a>Składnia  
  
```
class cancellation_token_source;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancellation_token_source —](#ctor)|Przeciążone. Tworzy nową `cancellation_token_source`. Źródło może służyć do flagi anulowania można anulować operacji.|  
|[~ cancellation_token_source — destruktor](#dtor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Anuluj](#cancel)|Anuluje tokenu. Wszelkie `task_group`, `structured_task_group`, lub `task` korzysta z której token zostanie anulowane po to wywołanie i Zgłoś wyjątek na następny punkt przerwania.|  
|[create_linked_source](#create_linked_source)|Przeciążone. Tworzy `cancellation_token_source` której została anulowana po anulowaniu podany token.|  
|[get_token](#get_token)|Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token on sondowany anulowania lub podaj wywołania zwrotnego, jeśli występuje anulowania.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator! =](#operator_neq)||  
|[operator =](#operator_eq)||  
|[operator ==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `cancellation_token_source`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplcancellation_token.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a>~ cancellation_token_source — 

```
~cancellation_token_source();
```  
  
##  <a name="cancel"></a>Anuluj 

 Anuluje tokenu. Wszelkie `task_group`, `structured_task_group`, lub `task` korzysta z której token zostanie anulowane po to wywołanie i Zgłoś wyjątek na następny punkt przerwania.  
  
```
void cancel() const;
```  
  
##  <a name="ctor"></a>cancellation_token_source — 

 Tworzy nową `cancellation_token_source`. Źródło może służyć do flagi anulowania można anulować operacji.  
  
```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="create_linked_source"></a>create_linked_source 

 Tworzy `cancellation_token_source` której została anulowana po anulowaniu podany token.  
  
```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```  
  
### <a name="parameters"></a>Parametry  
 `_Iter`  
 `_Src`  
 Token anulowania, którego spowoduje anulowanie zwrócony źródła tokenu. Uwaga zwrócony źródła tokenu również mogą zostać anulowane niezależnie od źródła zawartych w tym parametrze.  
  
 `_Begin`  
 Standardowa biblioteka C++ iteratora odpowiadający początek zakresu tokenów do nasłuchiwania anulowania.  
  
 `_End`  
 Standardowa biblioteka C++ iteratora odpowiadający końcowa zakresu tokenów do nasłuchiwania anulowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `cancellation_token_source` którego zostało anulowane, jeśli token `_Src` parametru zostało anulowane.  
  
##  <a name="get_token"></a>get_token 

 Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token on sondowany anulowania lub podaj wywołania zwrotnego, jeśli występuje anulowania.  
  
```
cancellation_token get_token() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Token anulowania skojarzony z tym źródłem.  
  
##  <a name="operator_neq"></a>operator! = 

```
bool operator!= (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq"></a>operator = 

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq_eq"></a>operator == 

```
bool operator== (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
