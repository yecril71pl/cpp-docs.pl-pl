---
title: "&lt;forward_list —&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
dev_langs: C++
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: "11"
manager: ghogen
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: c00c7d1e506e60a0a8612601835ef4a91b98ea99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list —&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora jest taki sam jak obiekt do przodu liście po prawej stronie.  
  
```
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu overloads `operator==` do porównywania dwóch obiektów klasy szablonu `forward_list`. Funkcja zwraca `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.  
  
##  <a name="op_neq"></a>operator! =  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora nie jest taki sam jak obiekt do przodu liście po prawej stronie.  
  
```
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** list nie są równe; **false** listy są równe.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu zwraca `!(left == right)`.  
  
##  <a name="op_lt"></a>operator&lt;  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora jest mniejsza niż obiekt do przodu liście po prawej stronie.  
  
```
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli na liście z lewej strony operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu overloads `operator<` do porównywania dwóch obiektów klasy szablonu `forward_list`. Funkcja zwraca `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora jest mniejsza niż lub równe obiekt do przodu liście po prawej stronie.  
  
```
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli na liście z lewej strony operatora jest mniejsza niż lub równa liście po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu zwraca `!(right < left)`.  
  
##  <a name="op_gt"></a>operator&gt;  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora jest większy niż obiekt do przodu liście po prawej stronie.  
  
```
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli na liście z lewej strony operatora jest większa niż liście po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja szablonu zwraca `right < left`.  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Testy, jeśli obiekt do przodu listy po lewej stronie operatora jest większa niż lub równa obiekt do przodu liście po prawej stronie.  
  
```
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt typu `forward_list`.|  
|`right`|Obiekt typu `forward_list`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli lista do przodu po lewej stronie operatora jest większa niż lub równa listy do przodu po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `!(left < right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [< forward_list — >](../standard-library/forward-list.md)



