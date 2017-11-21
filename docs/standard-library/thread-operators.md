---
title: "&lt;Wątek&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
dev_langs: C++
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: ff0fa361845c7bf64dd15bfc4e23be7b92b6cc39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltthreadgt-operators"></a>&lt;Wątek&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|  
|[operator ==](#op_eq_eq)|  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Określa, czy co najmniej `thread::id` obiektu jest większa lub równa innej.  
  
```cpp  
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `!(Left < Right)`  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_gt"></a>operator&gt;  
 Określa, czy co najmniej `thread::id` obiekt jest większy niż innym.  
  
```cpp  
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `Right < Left`  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż lub równy do innego.  
  
```cpp  
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `!(Right < Left)`  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_lt"></a>operator&lt;  
 Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż innym.  
  
```cpp  
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `Left` poprzedza `Right` w kolejności całkowita; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Definiuje operator całkowita kolejności na wszystkich `thread::id` obiektów. Te obiekty może służyć jako klucze w kontenerach asocjacyjnej.  
  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_neq"></a>operator! =  
 Porównuje dwa `thread::id` obiekty pod kątem nierówności.  
  
```cpp  
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `!(Left == Right)`  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_eq_eq"></a>operator ==  
 Porównuje dwa `thread::id` obiekty pod kątem równości.  
  
```cpp  
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```  
  
### <a name="parameters"></a>Parametry  
 `Left`  
 Po lewej stronie `thread::id` obiektu.  
  
 `Right`  
 Prawo `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli dwa obiekty reprezentują tego samego wątku wykonywania lub jeśli żaden obiekt reprezentuje wątku do wykonania; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji nie generują żadnych wyjątków.  
  
##  <a name="op_lt_lt"></a>operator&lt;&lt;  
 Wstawia tekst reprezentację `thread::id` obiektu do strumienia.  
  
```cpp  
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```  
  
### <a name="parameters"></a>Parametry  
 `Ostr`  
 A [basic_ostream —](../standard-library/basic-ostream-class.md) obiektu.  
  
 `Id`  
 A `thread::id` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `Ostr`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wstawia `Id` do `Ostr`.  
  
 Jeśli dwa `thread::id` obiektów porównanie, reprezentacje wstawionego tekstu te obiekty są takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Wątek >](../standard-library/thread.md)



