---
title: "cancellation_token_registration — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7c609c3a76e94029bd9004cf6322bae4f08d27b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration — Klasa
`cancellation_token_registration` Klasa reprezentuje wywołanie zwrotne powiadomienia `cancellation_token`. Gdy `register` metody na `cancellation_token` służy do odbierania powiadomień o po wystąpieniu anulowania `cancellation_token_registration` obiekt jest zwracany jako dojścia do wywołania zwrotnego, aby element wywołujący może zażądać wywołania zwrotnego nie jest już być wprowadzane za pośrednictwem stosowania `deregister` metody.  
  
## <a name="syntax"></a>Składnia  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[cancellation_token_registration](#ctor)||  
|[~cancellation_token_registration Destructor](#dtor)||  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplcancellation_token.h  
  
 **Namespace:** współbieżności  
  
##  <a name="dtor"></a> ~cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="ctor"></a> cancellation_token_registration — 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="operator_neq"></a> operator! = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq"></a> operator = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq_eq"></a> operator == 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
