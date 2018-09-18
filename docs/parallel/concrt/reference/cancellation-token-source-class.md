---
title: cancellation_token_source — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5bda0dd4b756ba9228fac8cc5b0de70b6d71f7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053651"
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source — Klasa
`cancellation_token_source` Klasa reprezentuje możliwości anulowania pewnej operacji.  
  
## <a name="syntax"></a>Składnia  
  
```
class cancellation_token_source;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancellation_token_source](#ctor)|Przeciążone. Tworzy nowy `cancellation_token_source`. Źródło może służyć do oflagowania anulowania pewnej operacji.|  
|[~cancellation_token_source Destructor](#dtor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancel](#cancel)|Anuluje token. Wszelkie `task_group`, `structured_task_group`, lub `task` które wykorzystują token będą anulowane po tym wywołaniu i zgłoszą wyjątek w następnym punkcie przerwania.|  
|[create_linked_source](#create_linked_source)|Przeciążone. Tworzy `cancellation_token_source` anulowany, gdy dostarczony token zostaje anulowany.|  
|[get_token](#get_token)|Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token może być sondowany w celu anulowania lub wygenerowania wywołania zwrotnego, wtedy, gdy następuje anulowanie.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `cancellation_token_source`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplcancellation_token.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~ cancellation_token_source — 

```
~cancellation_token_source();
```  
  
##  <a name="cancel"></a> Anuluj 

 Anuluje token. Wszelkie `task_group`, `structured_task_group`, lub `task` które wykorzystują token będą anulowane po tym wywołaniu i zgłoszą wyjątek w następnym punkcie przerwania.  
  
```
void cancel() const;
```  
  
##  <a name="ctor"></a> cancellation_token_source — 

 Tworzy nowy `cancellation_token_source`. Źródło może służyć do oflagowania anulowania pewnej operacji.  
  
```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Obiekt, aby skopiować lub przenieść.  
  
##  <a name="create_linked_source"></a> create_linked_source — 

 Tworzy `cancellation_token_source` anulowany, gdy dostarczony token zostaje anulowany.  
  
```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```  
  
### <a name="parameters"></a>Parametry  
*_Iter*<br/>
Typ iteratora.

*_Src*<br/>
Token, którego Anulowanie spowoduje anulowanie zwróconego źródła tokenu. Należy pamiętać, że zwracane źródłowego tokenu może być anulowane niezależnie od źródła zawartego w tym parametrze.  
  
*_Rozpocznij*<br/>
Standardowa biblioteka C++ iterator odpowiadający początkowi zakresu tokenów do nasłuchiwania anulowania.  
  
*_Zakończ*<br/>
Standardowa biblioteka C++ iterator odpowiadający końcowi zakresu tokenów do nasłuchiwania anulowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `cancellation_token_source` anulowany, gdy token dostarczony przez `_Src` zostaje anulowany.  
  
##  <a name="get_token"></a> get_token — 

 Zwraca token anulowania skojarzony z tym źródłem. Zwrócony token może być sondowany w celu anulowania lub wygenerowania wywołania zwrotnego, wtedy, gdy następuje anulowanie.  
  
```
cancellation_token get_token() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Token anulowania skojarzony z tym źródłem.  
  
##  <a name="operator_neq"></a> operator! = 

```
bool operator!= (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Argument operacji.
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq"></a> operator = 

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Argument operacji.

### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq_eq"></a> operator == 

```
bool operator== (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Argument operacji.
  
### <a name="return-value"></a>Wartość zwracana  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
