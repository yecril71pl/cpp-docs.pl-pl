---
title: error_code — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
ms.openlocfilehash: f4d0bc2c2922374d27bba3c0693e50f7930dbe67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593287"
---
# <a name="errorcode-class"></a>error_code — Klasa

Reprezentuje błędy niskiego poziomu systemu, które są specyficzne dla implementacji.

## <a name="syntax"></a>Składnia

```cpp
class error_code;
```

## <a name="remarks"></a>Uwagi

Obiekt typu `error_code` klasa przechowuje wartość kodu błędu i wskaźnik do obiektu, który reprezentuje [kategorii](../standard-library/error-category-class.md) błędu kodów, które opisują zgłaszane błędy systemu niskiego poziomu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[error_code —](#error_code)|Tworzy obiekt typu `error_code`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje wartość kodu błędu przechowywanych.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Przypisuje wartość kodu błędu i kategorii kod błędu.|
|[category](#category)|Zwraca kategoria błędu.|
|[Usuń zaznaczenie](#clear)|Czyści wartość kodu błędu i kategorii.|
|[default_error_condition —](#default_error_condition)|Zwraca domyślny warunek błędu.|
|[komunikat](#message)|Zwraca nazwę kod błędu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator==](#op_eq_eq)|Testuje pod kątem równości pomiędzy `error_code` obiektów.|
|[operator!=](#op_neq)|Testuje pod kątem nierówności pomiędzy `error_code` obiektów.|
|[Operator <](#op_lt)|Sprawdza, czy `error_code` obiekt jest mniejszy od `error_code` obiekt przekazany do porównania.|
|[operator=](#op_eq)|Przypisuje nową wartość wyliczenia do `error_code` obiektu.|
|[bool — operator](#op_bool)|Rzutuje zmienną typu `error_code`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<system_error >

**Namespace:** standardowe

## <a name="assign"></a>  error_code::ASSIGN

Przypisuje wartość kodu błędu i kategorii kod błędu.

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Val*|Wartość kodu błędu, aby przechowywać w `error_code`.|
|*_Cat*|Kategoria błędu, aby przechowywać w `error_code`.|

### <a name="remarks"></a>Uwagi

Magazyny funkcja elementu członkowskiego *val* jako wartość kodu błędu i wskaźnik *_Cat*.

## <a name="category"></a>  error_code::category

Zwraca kategoria błędu.

```cpp
const error_category& category() const;
```

### <a name="remarks"></a>Uwagi

## <a name="clear"></a>  error_code::Clear

Czyści wartość kodu błędu i kategorii.

```cpp
clear();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego przechowuje błąd kodu wartość zero i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category) obiektu.

## <a name="default_error_condition"></a>  error_code::default_error_condition

Zwraca domyślny warunek błędu.

```cpp
error_condition default_error_condition() const;
```

### <a name="return-value"></a>Wartość zwracana

[Error_condition](../standard-library/error-condition-class.md) określony przez [default_error_condition —](../standard-library/error-category-class.md#default_error_condition).

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca `category().default_error_condition(value())`.

## <a name="error_code"></a>  error_code::error_code

Tworzy obiekt typu `error_code`.

```cpp
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
|*Val*|Wartość kodu błędu, aby przechowywać w `error_code`.|
|*_Cat*|Kategoria błędu, aby przechowywać w `error_code`.|
|*_Errcode*|Wartość wyliczenia do przechowywania w `error_code`.|

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje błąd kodu wartość zero i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category).

Drugi Konstruktor magazynów *val* jako wartość kodu błędu i wskaźnik [error_category](../standard-library/error-category-class.md).

Trzeci Konstruktor magazynów `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category).

## <a name="message"></a>  error_code::Message

Zwraca nazwę kod błędu.

```cpp
string message() const;
```

### <a name="return-value"></a>Wartość zwracana

A `string` reprezentujący nazwę kod błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwraca `category().message(value())`.

## <a name="op_eq_eq"></a>  error_code::operator ==

Testuje pod kątem równości pomiędzy `error_code` obiektów.

```cpp
bool operator==(const error_code& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Obiekt, który ma zostać przetestowana pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() == right.category() && value == right.value()`.

## <a name="op_neq"></a>  error_code::operator! =

Testuje pod kątem nierówności pomiędzy `error_code` obiektów.

```cpp
bool operator!=(const error_code& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Obiekt, który ma zostać przetestowana pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_code` obiektu nie jest równa `error_code` obiekt przekazany w *prawo*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `!(*this == right)`.

## <a name="op_lt"></a>  error_code::operator&lt;

Sprawdza, czy `error_code` obiekt jest mniejszy od `error_code` obiekt przekazany do porównania.

```cpp
bool operator<(const error_code& right) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Error_code — obiekt, który ma zostać porównane.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_code` obiekt jest mniejszy od `error_code` obiekt przekazany do porównania; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() < right.category() || category() == right.category() && value < right.value()`.

## <a name="op_eq"></a>  error_code::operator =

Przypisuje nową wartość wyliczenia do `error_code` obiektu.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Errcode*|Wartość wyliczenia do przypisania do `error_code` obiektu.|

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `error_code` obiektu, który jest przypisany nową wartość wyliczenia przy użyciu funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Magazyny operator członkowski `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca `*this`.

## <a name="op_bool"></a>  error_code::operator bool

Rzutuje zmienną typu `error_code`.

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość logiczna `error_code` obiektu.

### <a name="remarks"></a>Uwagi

Operator zwraca można przekonwertować wartości na **true** tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest konwertowany tylko **bool**, nie `void *` lub innych znanych typów skalarnych.

## <a name="value"></a>  error_code::Value

Zwraca wartość kodu błędu przechowywanych.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość kodu błędu przechowywanych typu [value_type](#value_type).

### <a name="remarks"></a>Uwagi

## <a name="value_type"></a>  error_code::value_type

Typ, który reprezentuje wartość kodu błędu przechowywanych.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Uwagi

Ta definicja typu jest synonimem dla **int**.

## <a name="see-also"></a>Zobacz także

[error_category, klasa](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
