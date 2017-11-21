---
title: "cancellation_token — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs: C++
helpviewer_keywords: cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e4e656fa567342dde9ba990bff5b0d8081337385
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cancellationtoken-class"></a>cancellation_token — Klasa
`cancellation_token` Klasa reprezentuje możliwość określenia, czy zażądano operacji do anulowania. Skojarzono danego tokenu `task_group`, `structured_task_group`, lub `task` zapewnienie niejawne anulowania. Można go również sondowany anulowania lub wywołania zwrotnego zarejestrowany dla przypadku, gdy skojarzony `cancellation_token_source` zostało anulowane.  
  
## <a name="syntax"></a>Składnia  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancellation_token —](#ctor)||  
|[~ cancellation_token — destruktor](#dtor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[deregister_callback](#deregister_callback)|Usuwa wywołanie zwrotne zarejestrowane wcześniej za pośrednictwem `register` na podstawie metody `cancellation_token_registration` obiekt jest zwracany w chwili rejestracji.|  
|[is_cancelable](#is_cancelable)|Zwraca wskazaniem, czy ten token mogą zostać anulowane lub nie.|  
|[is_canceled](#is_canceled)|Zwraca `true` czy token został anulowany.|  
|[Brak](#none)|Zwraca token anulowania, który nigdy nie mogą podlegać anulowania.|  
|[register_callback](#register_callback)|Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token jest anulowane, nastąpi wywołania zwrotnego. Należy pamiętać, że jeśli token jest już anulowane w momencie, gdy ta metoda jest wywoływana, wywołania zwrotnego będą natychmiast.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator! =](#operator_neq)||  
|[operator =](#operator_eq)||  
|[operator ==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `cancellation_token`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplcancellation_token.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a>~ cancellation_token — 

```
~cancellation_token();
```  
  
##  <a name="ctor"></a>cancellation_token — 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="deregister_callback"></a>deregister_callback 

 Usuwa wywołanie zwrotne zarejestrowane wcześniej za pośrednictwem `register` na podstawie metody `cancellation_token_registration` obiekt jest zwracany w chwili rejestracji.  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Registration`  
 `cancellation_token_registration` Obiektu odpowiadającego wywołanie zwrotne, aby być wyrejestrowany. Ten token musi zostały wcześniej zwrócone w wyniku wywołania `register` metody.  
  
##  <a name="is_cancelable"></a>is_cancelable 

 Zwraca wskazaniem, czy ten token mogą zostać anulowane lub nie.  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskazanie, czy ten token mogą zostać anulowane lub nie.  
  
##  <a name="is_canceled"></a>is_canceled 

 Zwraca `true` czy token został anulowany.  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość `true` Jeśli token została anulowana, a w przeciwnym razie wartość `false`.  
  
##  <a name="none"></a>Brak 

 Zwraca token anulowania, który nigdy nie mogą podlegać anulowania.  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Token anulowania, którego nie można anulować.  
  
##  <a name="operator_neq"></a>operator! = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq"></a>operator = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq_eq"></a>operator == 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="register_callback"></a>register_callback 

 Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token jest anulowane, nastąpi wywołania zwrotnego. Należy pamiętać, że jeśli token jest już anulowane w momencie, gdy ta metoda jest wywoływana, wywołania zwrotnego będą natychmiast.  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcja, która zostanie wywołana Wstecz, gdy to `cancellation_token` zostało anulowane.  
  
 `_Func`  
 Obiekt funkcji, która zostanie wywołana Wstecz, gdy to `cancellation_token` zostało anulowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `cancellation_token_registration` obiektu, który może być wykorzystana w `deregister` metodę wyrejestrowania wcześniej zarejestrowane wywołanie zwrotne i uniemożliwić odniesienia. Metoda zgłosi [invalid_operation —](invalid-operation-class.md) wyjątek, jeśli jest to `cancellation_token` obiekt, który został utworzony przy użyciu [cancellation_token::none](#none) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
