---
title: "&lt;system_error —&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs: C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: ed01a5abeb54f5071968555b563849e2cd4ac1af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error —&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&lt;](#op_lt)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, jeśli obiekt po lewej stronie operatora jest taki sam jak obiekt po prawej stronie.  
  
```
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt pod kątem równości.|  
|`right`|Obiekt pod kątem równości.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca `left.category() == right.category() && left.value() == right.value()`.  
  
##  <a name="op_neq"></a>operator! =  
 Testy, jeśli obiekt po lewej stronie operatora nie jest taki sam jak obiekt po prawej stronie.  
  
```
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt pod kątem nierówności.|  
|`right`|Obiekt pod kątem nierówności.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli przekazano obiekt `left` nie jest równa przekazano obiekt `right`; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca `!(left == right)`.  
  
##  <a name="op_lt"></a>operator&lt;  
 Sprawdza, czy obiekt jest mniejszy niż obiekt przekazany do porównania.  
  
```
template <class _Enum>  
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>  
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>  
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>  
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`left`|Obiekt do porównania.|  
|`right`|Obiekt do porównania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli przekazano obiekt `left` jest mniejsza niż przekazano obiekt `right`; W przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja sprawdza kolejność błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [< system_error — >](../standard-library/system-error.md)



