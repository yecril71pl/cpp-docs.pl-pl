---
title: Operatory ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75c9ffb8c918cce70ad1e150dd80cb07ebdd7b34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-operators"></a>Operatory ATL
Ta sekcja zawiera tematy referencyjne dla operatorów globalnych ATL.  
  
|Operator|Opis|  
|--------------|-----------------|  
|[operator ==](#operator_eq_eq)|Porównuje dwa `CSid` obiektów lub `SID` struktury pod kątem równości.|  
|[operator! =](#operator_neq)|Porównuje dwa `CSid` obiektów lub `SID` struktury pod kątem nierówności.|  
|[Operator <](#operator_lt)|Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejsza niż `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).|  
|[operator >](#operator_gt)|Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większa niż `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).|  
|[Operator < =](#operator_lt__eq)|Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejsze niż lub równe `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).|  
|[operator > =](#operator_gt__eq)|Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest większa niż lub równa `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h.  
  
##  <a name="operator_eq_eq"></a>  operator ==  
 Porównuje `CSid` obiektów lub `SID` struktur (identyfikator zabezpieczeń) pod kątem równości.  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli obiekty są takie same, **false** nie są równe.  
  
##  <a name="operator_neq"></a>  operator! =  
 Porównuje `CSid` obiektów lub `SID` struktur (identyfikator zabezpieczeń) pod kątem nierówności.  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli obiekty nie są takie same, **false** czy są równe.  
  
##  <a name="operator_lt"></a>  Operator <  
 Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejsza niż `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli adres `lhs` obiekt jest mniejszy niż adres `rhs` obiektu **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane, aby zapewnić zgodność z klasy kolekcji standardowa biblioteka C++.  
  
##  <a name="operator_gt"></a>  operator >  
 Sprawdza, czy `CSid` obiektu lub `SID` struktury po lewej stronie operatora jest większa niż `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli adres `lhs` jest większy niż adres `rhs`, **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane, aby zapewnić zgodność z klasy kolekcji standardowa biblioteka C++.  
  
##  <a name="operator_lt__eq"></a>  Operator < =  
 Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest mniejsze niż lub równe `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli adres `lhs` jest mniejszy niż adres `rhs`, **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane, aby zapewnić zgodność z klasy kolekcji standardowa biblioteka C++.  
  
##  <a name="operator_gt__eq"></a>  operator > =  
 Sprawdza, czy `CSid` obiektu lub `SID` struktura po lewej stronie operatora jest większa niż lub równa `CSid` obiektu lub `SID` struktury po prawej stronie (na potrzeby zgodności standardowa biblioteka C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy `CSid` obiektu lub `SID` struktury do porównania.  
  
 `rhs`  
 Drugi `CSid` obiektu lub `SID` struktury do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli adres `lhs` jest większa niż lub równa adres `rhs`, **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator działa na adres `CSid` obiektu lub `SID` struktury i jest implementowane, aby zapewnić zgodność z klasy kolekcji standardowa biblioteka C++.



