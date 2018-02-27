---
title: "error_code — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9521790906c591c3b459cc5efd70fe0ba021ccf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="errorcode-class"></a>error_code — Klasa
Reprezentuje błędy systemu niskiego poziomu, które są specyficzne dla wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```
class error_code;
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt typu `error_code` klasy przechowuje wartość kodu błędu i wskaźnika do obiektu, który reprezentuje [kategorii](../standard-library/error-category-class.md) błędu kodów opisujących zgłaszane błędy niskiego poziomu systemu.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[error_code](#error_code)|Tworzy obiekt typu `error_code`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[value_type](#value_type)|Typ reprezentujący wartość kodu błędu przechowywane.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przypisz](#assign)|Przypisuje wartość kodu błędu i kategorii kod błędu.|  
|[category](#category)|Zwraca błąd kategorii.|  
|[Wyczyść](#clear)|Czyści wartość kodu błędu i kategorii.|  
|[default_error_condition](#default_error_condition)|Zwraca domyślny warunek błędu.|  
|[komunikat](#message)|Zwraca nazwę kod błędu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|Testy równości między `error_code` obiektów.|  
|[operator!=](#op_neq)|Testy pod kątem nierówności między `error_code` obiektów.|  
|[Operator <](#op_lt)|Sprawdza, czy `error_code` obiekt jest mniejsza niż `error_code` przekazano obiekt do porównania.|  
|[operator=](#op_eq)|Przypisuje nową wartość wyliczenia do `error_code` obiektu.|  
|[bool — operator](#op_bool)|Rzutuje zmiennej typu `error_code`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<system_error — >  
  
 **Namespace:** Standard  
  
##  <a name="assign"></a>  error_code::ASSIGN  
 Przypisuje wartość kodu błędu i kategorii kod błędu.  
  
```
void assign(value_type val, const error_category& _Cat);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`val`|Wartość kodu błędu mają być przechowywane w `error_code`.|  
|`_Cat`|Kategoria błędu mają być przechowywane w `error_code`.|  
  
### <a name="remarks"></a>Uwagi  
 Magazyny funkcji Członkowskich `val` jako wartość kodu błędu i wskaźnika do `_Cat`.  
  
##  <a name="category"></a>  error_code::category  
 Zwraca błąd kategorii.  
  
```
const error_category& category() const;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="clear"></a>  error_code::Clear  
 Czyści wartość kodu błędu i kategorii.  
  
```
clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska przechowuje błąd kodu wartość zerową i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category) obiektu.  
  
##  <a name="default_error_condition"></a>  error_code::default_error_condition  
 Zwraca domyślny warunek błędu.  
  
```
error_condition default_error_condition() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [Error_condition —](../standard-library/error-condition-class.md) określonego przez [default_error_condition —](../standard-library/error-category-class.md#default_error_condition).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwraca `category().default_error_condition(value())`.  
  
##  <a name="error_code"></a>  error_code::error_code  
 Tworzy obiekt typu `error_code`.  
  
```
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`val`|Wartość kodu błędu mają być przechowywane w `error_code`.|  
|`_Cat`|Kategoria błędu mają być przechowywane w `error_code`.|  
|`_Errcode`|Wartość wyliczenia mają być przechowywane w `error_code`.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor przechowuje błąd kodu wartość zerową i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
 Drugi Konstruktor magazynów `val` jako wartość kodu błędu i wskaźnika do [error_category —](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).  
  
 Trzeci magazynów konstruktora `(value_type)_Errcode` jako wartość kodu błędu i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="message"></a>  error_code::Message  
 Zwraca nazwę kod błędu.  
  
```
string message() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `string` reprezentujący nazwę kod błędu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwraca `category().message(value())`.  
  
##  <a name="op_eq_eq"></a>  error_code::operator ==  
 Testy równości między `error_code` obiektów.  
  
```
bool operator==(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Obiekt pod kątem równości.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski operatora `category() == right.category() && value == right.value()`.  
  
##  <a name="op_neq"></a>  error_code::operator! =  
 Testy pod kątem nierówności między `error_code` obiektów.  
  
```
bool operator!=(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Obiekt pod kątem nierówności.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `error_code` obiektu nie jest równa `error_code` przekazano obiekt `right`; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski operatora `!(*this == right)`.  
  
##  <a name="op_lt"></a>  error_code::operator&lt;  
 Sprawdza, czy [error_code —](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) obiekt jest mniejsza niż `error_code` przekazano obiekt do porównania.  
  
```
bool operator<(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Error_code — obiekt do porównania.|  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli `error_code` obiekt jest mniejsza niż `error_code` obiekt przekazany do porównania; W przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski operatora `category() < right.category() || category() == right.category() && value < right.value()`.  
  
##  <a name="op_eq"></a>  error_code::operator =  
 Przypisuje nową wartość wyliczenia do [error_code —](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) obiektu.  
  
```
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type&
 operator=(_Enum _Errcode);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`_Errcode`|Wartość wyliczenia do przypisania do `error_code` obiektu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `error_code` obiekt, który jest ona obecnie przypisywana nowa wartość wyliczenia przez funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski operatora magazynów `(value_type)_Errcode` jako wartość kodu błędu i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca `*this`.  
  
##  <a name="op_bool"></a>  error_code::operator bool  
 Rzutuje zmiennej typu `error_code`.  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna `error_code` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość możliwe do przekonwertowania na `true` tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest tylko do przekonwertowania `bool`, aby nie były `void *` lub innych znanych typów skalarnych.  
  
##  <a name="value"></a>  error_code::Value  
 Zwraca wartość kodu błędu przechowywane.  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość kodu błędu przechowywanych typu [value_type](#value_type).  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="value_type"></a>  error_code::value_type  
 Typ reprezentujący wartość kodu błędu przechowywane.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta definicja typu jest synonimem `int`.  
  
## <a name="see-also"></a>Zobacz też  
 [error_category — klasa](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)



