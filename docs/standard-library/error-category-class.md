---
title: "error_category — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
dev_langs:
- C++
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3befee5318756471e0eee6b975bdfb65f61c0391
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="errorcategory-class"></a>error_category — Klasa
Reprezentuje podstawę abstrakcyjna, wspólne dla obiektów opisujący kategorii kodów błędów.  
  
## <a name="syntax"></a>Składnia  
  
```
class error_category;
```  
  
## <a name="remarks"></a>Uwagi  
 Implementowanie dwa obiekty wstępnie zdefiniowanych `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) i [system_category](../standard-library/system-error-functions.md#system_category).  
  
### <a name="typedefs"></a>Definicje typów  
  
|||  
|-|-|  
|[value_type](#value_type)|Typ reprezentujący wartość kodu błędu przechowywane.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[default_error_condition](#default_error_condition)|Przechowuje wartość kodu błędu dla obiekt warunek błędu.|  
|[equivalent](#equivalent)|Zwraca wartość określającą, czy błąd obiekty są równoważne.|  
|[komunikat](#message)|Zwraca nazwę określonego kodu błędu.|  
|[Nazwa](#name)|Zwraca nazwę kategorii.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|Testy równości między `error_category` obiektów.|  
|[operator!=](#op_neq)|Testy pod kątem nierówności między `error_category` obiektów.|  
|[Operator <](#op_lt)|Sprawdza, czy [error_category —](../standard-library/error-category-class.md) obiekt jest mniejsza niż `error_category` przekazano obiekt do porównania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<system_error — >  
  
 **Namespace:** Standard  
  
##  <a name="default_error_condition"></a>  error_category::default_error_condition  
 Przechowuje wartość kodu błędu dla obiekt warunek błędu.  
  
```
virtual error_condition default_error_condition(int _Errval) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Errval`|Wartość kodu błędu mają być przechowywane w [error_condition —](../standard-library/error-condition-class.md).|  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `error_condition(_Errval, *this)`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="equivalent"></a>  error_category::Equivalent  
 Zwraca wartość określającą, czy błąd obiekty są równoważne.  
  
```
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Errval`|Kod błędu wartość do porównania.|  
|`_Cond`|[Error_condition —](../standard-library/error-condition-class.md) obiekt do porównania.|  
|`_Code`|[Error_code —](../standard-library/error-code-class.md) obiekt do porównania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli kategorii i wartości są równe; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej `*this == _Cond.category() && _Cond.value() == _Errval`.  
  
 Zwraca drugie funkcji członkowskiej `*this == _Code.category() && _Code.value() == _Errval`.  
  
##  <a name="message"></a>  error_category::Message  
 Zwraca nazwę określonego kodu błędu.  
  
```
virtual string message(error_code::value_type val) const = 0;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`val`|Wartość kodu błędu do opisu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę opisową kodu błędu `val` dla kategorii.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="name"></a>  error_category::Name  
 Zwraca nazwę kategorii.  
  
```
virtual const char *name() const = 0;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nazwę kategorii jako ciąg znaków zakończony znakiem null bajtów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="op_eq_eq"></a>  error_category::operator ==  
 Testy równości między `error_category` obiektów.  
  
```
bool operator==(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Obiekt pod kątem równości.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator członkowski zwraca `this == &right`.  
  
##  <a name="op_neq"></a>  error_category::operator! =  
 Testy pod kątem nierówności między `error_category` obiektów.  
  
```
bool operator!=(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Obiekt pod kątem nierówności.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `error_category` obiektu nie jest równa `error_category` przekazano obiekt `right`; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski operatora `(!*this == right)`.  
  
##  <a name="op_lt"></a>  error_category::operator&lt;  
 Sprawdza, czy [error_category —](../standard-library/error-category-class.md) obiekt jest mniejsza niż `error_category` przekazano obiekt do porównania.  
  
```
bool operator<(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|`error_category` Obiekt do porównania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `error_category` obiekt jest mniejsza niż `error_category` obiekt przekazany do porównania; W przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski operatora `this < &right`.  
  
##  <a name="value_type"></a>  error_category::value_type  
 Typ reprezentujący wartość kodu błędu przechowywane.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta definicja typu jest synonimem `int`.  
  
## <a name="see-also"></a>Zobacz też  
 [<system_error>](../standard-library/system-error.md)



