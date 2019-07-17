---
title: error_condition — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: cbadf6a22871cc9a23d37c095a398490c8a4c72c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245797"
---
# <a name="errorcondition-class"></a>error_condition — Klasa

Reprezentuje kody błędów zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```cpp
class error_condition;
```

## <a name="remarks"></a>Uwagi

Obiekt typu `error_condition` przechowuje wartość kodu błędu i wskaźnik do obiektu, który reprezentuje [kategorii](../standard-library/error-category-class.md) umożliwiający objętych kodami błędów zgłoszonych błędów zdefiniowanych przez użytkownika.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[error_condition —](#error_condition)|Tworzy obiekt typu `error_condition`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje wartość kodu błędu przechowywanych.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[Przypisz](#assign)|Przypisuje wartość kodu błędu i kategorii warunek błędu.|
|[category](#category)|Zwraca kategoria błędu.|
|[Usuń zaznaczenie](#clear)|Czyści wartość kodu błędu i kategorii.|
|[komunikat](#message)|Zwraca nazwę kod błędu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator==](#op_eq_eq)|Testuje pod kątem równości pomiędzy `error_condition` obiektów.|
|[operator!=](#op_neq)|Testuje pod kątem nierówności pomiędzy `error_condition` obiektów.|
|[Operator <](#op_lt)|Sprawdza, czy `error_condition` obiekt jest mniejszy od `error_code` obiekt przekazany do porównania.|
|[operator=](#op_eq)|Przypisuje nową wartość wyliczenia do `error_condition` obiektu.|
|[bool — operator](#op_bool)|Rzutuje zmienną typu `error_condition`.|

### <a name="assign"></a> Przypisz

Przypisuje wartość kodu błędu i kategorii warunek błędu.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parametry

*Val*\
Wartość kodu błędu, aby przechowywać w `error_code`.

*_Cat*\
Kategoria błędu, aby przechowywać w `error_code`.

#### <a name="remarks"></a>Uwagi

Magazyny funkcja elementu członkowskiego *val* jako wartość kodu błędu i wskaźnik *_Cat*.

### <a name="category"></a> Kategoria

Zwraca kategoria błędu.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do kategorii błędów przechowywane

#### <a name="remarks"></a>Uwagi

### <a name="clear"></a> Usuń zaznaczenie

Czyści wartość kodu błędu i kategorii.

```cpp
clear();
```

#### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego przechowuje błąd kodu wartość zero i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category) obiektu.

### <a name="error_condition"></a> error_condition —

Tworzy obiekt typu `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametry

*Val*\
Wartość kodu błędu, aby przechowywać w `error_condition`.

*_Cat*\
Kategoria błędu, aby przechowywać w `error_condition`.

*_Errcode*\
Wartość wyliczenia do przechowywania w `error_condition`.

#### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje błąd kodu wartość zero i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category).

Drugi Konstruktor magazynów *val* jako wartość kodu błędu i wskaźnik [error_category](../standard-library/error-category-class.md).

Trzeci Konstruktor magazynów `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a> Komunikat

Zwraca nazwę kod błędu.

```cpp
string message() const;
```

#### <a name="return-value"></a>Wartość zwracana

A `string` reprezentujący nazwę kod błędu.

#### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca `category().message(value())`.

### <a name="op_eq_eq"></a> operator ==

Testuje pod kątem równości pomiędzy `error_condition` obiektów.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
Ojbect, który ma zostać przetestowana pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() == right.category() && value == right.value()`.

### <a name="op_neq"></a> operator! =

Testuje pod kątem nierówności pomiędzy `error_condition` obiektów.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
Obiekt, który ma zostać przetestowana pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_condition` obiektu nie jest równa `error_condition` obiekt przekazany w *prawo*; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `!(*this == right)`.

### <a name="op_lt"></a> Operator&lt;

Sprawdza, czy `error_condition` obiekt jest mniejszy od `error_code` obiekt przekazany do porównania.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
`error_condition` Obiekt do porównania.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_condition` obiekt jest mniejszy od `error_condition` obiekt przekazany do porównania; W przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="op_eq"></a> operator =

Przypisuje nową wartość wyliczenia do `error_condition` obiektu.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>Parametry

*_Errcode*\
Wartość wyliczenia do przypisania do `error_condition` obiektu.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do `error_condition` obiektu, który jest przypisany nową wartość wyliczenia przy użyciu funkcji elementu członkowskiego.

#### <a name="remarks"></a>Uwagi

Magazyny operator członkowski `(value_type)error` jako wartość kodu błędu i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca `*this`.

### <a name="op_bool"></a> bool — operator

Rzutuje zmienną typu `error_condition`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna `error_condition` obiektu.

#### <a name="remarks"></a>Uwagi

Operator zwraca można przekonwertować wartości na **true** tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest konwertowany tylko **bool**, nie `void *` lub innych znanych typów skalarnych.

### <a name="value"></a> Wartość

Zwraca wartość kodu błędu przechowywanych.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość kodu błędu przechowywanych typu [value_type](#value_type).

#### <a name="remarks"></a>Uwagi

### <a name="value_type"></a> value_type

Typ, który reprezentuje wartość kodu błędu przechowywanych.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Definicja typu jest synonimem dla **int**.
