---
title: error_condition — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202add45c335adea086087aed9ce3374e56a7e39
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847871"
---
# <a name="errorcondition-class"></a>error_condition — Klasa

Reprezentuje kody błędów zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```cpp
class error_condition;
```

## <a name="remarks"></a>Uwagi

Obiekt typu `error_condition` przechowuje wartość kodu błędu i wskaźnika do obiektu, który reprezentuje [kategorii](../standard-library/error-category-class.md) używany do kodów błędów zgłoszonych błędów zdefiniowanych przez użytkownika.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[error_condition —](#error_condition)|Tworzy obiekt typu `error_condition`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ reprezentujący wartość kodu błędu przechowywane.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Przypisz](#assign)|Przypisuje wartość kodu błędu i kategorii warunek błędu.|
|[category](#category)|Zwraca błąd kategorii.|
|[Wyczyść](#clear)|Czyści wartość kodu błędu i kategorii.|
|[komunikat](#message)|Zwraca nazwę kod błędu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](#op_eq_eq)|Testy równości między `error_condition` obiektów.|
|[operator!=](#op_neq)|Testy pod kątem nierówności między `error_condition` obiektów.|
|[Operator <](#op_lt)|Sprawdza, czy `error_condition` obiekt jest mniejsza niż `error_code` przekazano obiekt do porównania.|
|[operator=](#op_eq)|Przypisuje nową wartość wyliczenia do `error_condition` obiektu.|
|[bool — operator](#op_bool)|Rzutuje zmiennej typu `error_condition`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error — >

**Namespace:** Standard

## <a name="assign"></a>  error_condition::ASSIGN

Przypisuje wartość kodu błędu i kategorii warunek błędu.

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`val`|Wartość kodu błędu mają być przechowywane w `error_code`.|
|`_Cat`|Kategoria błędu mają być przechowywane w `error_code`.|

### <a name="remarks"></a>Uwagi

Magazyny funkcji Członkowskich `val` jako wartość kodu błędu i wskaźnika do `_Cat`.

## <a name="category"></a>  error_condition::category

Zwraca błąd kategorii.

```cpp
const error_category& category() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do kategorii przechowywanych błąd

### <a name="remarks"></a>Uwagi

## <a name="clear"></a>  error_condition::Clear

Czyści wartość kodu błędu i kategorii.

```cpp
clear();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje błąd kodu wartość zerową i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category) obiektu.

## <a name="error_condition"></a>  error_condition::error_condition

Tworzy obiekt typu `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`val`|Wartość kodu błędu mają być przechowywane w `error_condition`.|
|`_Cat`|Kategoria błędu mają być przechowywane w `error_condition`.|
|`_Errcode`|Wartość wyliczenia mają być przechowywane w `error_condition`.|

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje błąd kodu wartość zerową i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category).

Drugi Konstruktor magazynów `val` jako wartość kodu błędu i wskaźnika do [error_category —](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).

Trzeci magazynów konstruktora `(value_type)_Errcode` jako wartość kodu błędu i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category).

## <a name="message"></a>  error_condition::Message

Zwraca nazwę kod błędu.

```cpp
string message() const;
```

### <a name="return-value"></a>Wartość zwracana

A `string` reprezentujący nazwę kod błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca `category().message(value())`.

## <a name="op_eq_eq"></a>  error_condition::operator ==

Testy równości między `error_condition` obiektów.

```cpp
bool operator==(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|Ojbect pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski operatora `category() == right.category() && value == right.value()`.

## <a name="op_neq"></a>  error_condition::operator! =

Testy pod kątem nierówności między `error_condition` obiektów.

```cpp
bool operator!=(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|Obiekt pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_condition` obiektu nie jest równa `error_condition` przekazano obiekt `right`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski operatora `!(*this == right)`.

## <a name="op_lt"></a>  error_condition::operator&lt;

Sprawdza, czy `error_condition` obiekt jest mniejsza niż `error_code` przekazano obiekt do porównania.

```cpp
bool operator<(const error_condition& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|`error_condition` Obiekt do porównania.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_condition` obiekt jest mniejsza niż `error_condition` obiekt przekazany do porównania; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski operatora `category() < right.category() || category() == right.category() && value < right.value()`.

## <a name="op_eq"></a>  error_condition::operator =

Przypisuje nową wartość wyliczenia do `error_condition` obiektu.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
 operator=(Enum _Errcode);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Errcode`|Wartość wyliczenia do przypisania do `error_condition` obiektu.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `error_condition` obiekt, który jest ona obecnie przypisywana nowa wartość wyliczenia przez funkcję elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Element członkowski operatora magazynów `(value_type)error` jako wartość kodu błędu i wskaźnika do [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca `*this`.

## <a name="op_bool"></a>  error_condition::operator bool

Rzutuje zmiennej typu `error_condition`.

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna `error_condition` obiektu.

### <a name="remarks"></a>Uwagi

Zwraca wartość możliwe do przekonwertowania na `true` tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest tylko do przekonwertowania `bool`, aby nie były `void *` lub innych znanych typów skalarnych.

## <a name="value"></a>  error_condition::Value

Zwraca wartość kodu błędu przechowywane.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość kodu błędu przechowywanych typu [value_type](#value_type).

### <a name="remarks"></a>Uwagi

## <a name="value_type"></a>  error_condition::value_type

Typ reprezentujący wartość kodu błędu przechowywane.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Uwagi

Definicja typu jest synonimem `int`.

## <a name="see-also"></a>Zobacz także

[error_category, klasa](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
