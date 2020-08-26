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
ms.openlocfilehash: 5bbd67d2967a1a6d070ece54ea464a2a5a2deac9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844460"
---
# <a name="error_code-class"></a>error_code — Klasa

Reprezentuje błędy systemu niskiego poziomu, które są specyficzne dla implementacji.

## <a name="syntax"></a>Składnia

```cpp
class error_code;
```

## <a name="remarks"></a>Uwagi

Obiekt typu `error_code` Class przechowuje wartość kodu błędu i wskaźnik do obiektu, który reprezentuje [kategorię](../standard-library/error-category-class.md) kodów błędów, które opisują raportowane błędy systemu niskiego poziomu.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[error_code](#error_code)|Konstruuje obiekt typu `error_code` .|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[value_type](#value_type)|Typ reprezentujący przechowywaną wartość kodu błędu.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[przypisać](#assign)|Przypisuje wartość kodu błędu i kategorię do kodu błędu.|
|[kategorii](#category)|Zwraca kategorię błędu.|
|[Wyczyść](#clear)|Czyści wartość kodu błędu i kategorię.|
|[default_error_condition](#default_error_condition)|Zwraca domyślny warunek błędu.|
|[Komunikat](#message)|Zwraca nazwę kodu błędu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator = =](#op_eq_eq)|Testuje równość między `error_code` obiektami.|
|[operator! =](#op_neq)|Testuje pod kątem nierówności między `error_code` obiektami.|
|[<operatora ](#op_lt)|Testuje, czy `error_code` obiekt jest mniejszy niż `error_code` obiekt przeszedł do porównania.|
|[operator =](#op_eq)|Przypisuje nowej wartości wyliczenia do `error_code` obiektu.|
|[wartość logiczna operatora](#op_bool)|Rzutuje zmienną typu `error_code` .|

### <a name="assign"></a><a name="assign"></a> ponownie

Przypisuje wartość kodu błędu i kategorię do kodu błędu.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość kodu błędu, która ma być przechowywana w `error_code` .

*_Cat*\
Kategoria błędów do przechowywania w `error_code` .

#### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje wartości *Val* jako wartość kodu błędu i wskaźnik do *_Cat*.

### <a name="category"></a><a name="category"></a> kategorii

Zwraca kategorię błędu.

```cpp
const error_category& category() const;
```

#### <a name="remarks"></a>Uwagi

### <a name="clear"></a><a name="clear"></a> Wyczyść

Czyści wartość kodu błędu i kategorię.

```cpp
clear();
```

#### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje zero wartości kodu błędu i wskaźnik do obiektu [generic_category](../standard-library/system-error-functions.md#generic_category) .

### <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

Zwraca domyślny warunek błędu.

```cpp
error_condition default_error_condition() const;
```

#### <a name="return-value"></a>Wartość zwracana

[Error_condition](../standard-library/error-condition-class.md) określony przez [default_error_condition](../standard-library/error-category-class.md#default_error_condition).

#### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwraca `category().default_error_condition(value())` .

### <a name="error_code"></a><a name="error_code"></a> error_code

Konstruuje obiekt typu `error_code` .

```cpp
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość kodu błędu, która ma być przechowywana w `error_code` .

*_Cat*\
Kategoria błędów do przechowywania w `error_code` .

*_Errcode*\
Wartość wyliczenia, która ma być przechowywana w `error_code` .

#### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje zero wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category).

Drugi Konstruktor przechowuje *Val* jako wartość kodu błędu i wskaźnik do [error_category](../standard-library/error-category-class.md).

Trzeci Konstruktor przechowuje `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a><a name="message"></a> Komunikat

Zwraca nazwę kodu błędu.

```cpp
string message() const;
```

#### <a name="return-value"></a>Wartość zwracana

`string`Reprezentujący nazwę kodu błędu.

#### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwraca `category().message(value())` .

### <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje równość między `error_code` obiektami.

```cpp
bool operator==(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt, który ma być testowany pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty są równe; **`false`** Jeśli obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() == right.category() && value == right.value()` .

### <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje pod kątem nierówności między `error_code` obiektami.

```cpp
bool operator!=(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt, który ma być testowany pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_code` obiekt nie jest równy `error_code` obiektowi przekazanym w *prawej*; w przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `!(*this == right)` .

### <a name="operatorlt"></a><a name="op_lt"></a> zakład&lt;

Testuje, czy `error_code` obiekt jest mniejszy niż `error_code` obiekt przeszedł do porównania.

```cpp
bool operator<(const error_code& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt error_code, który ma zostać porównany.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_code` obiekt jest mniejszy niż `error_code` obiekt przeszedł do porównania; W przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() < right.category() || category() == right.category() && value < right.value()` .

### <a name="operator"></a><a name="op_eq"></a> operator =

Przypisuje nowej wartości wyliczenia do `error_code` obiektu.

```cpp
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value, error_code>::type&
    operator=(_Enum _Errcode);
```

#### <a name="parameters"></a>Parametry

*_Errcode*\
Wartość wyliczenia, która ma zostać przypisana do `error_code` obiektu.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do `error_code` obiektu, do którego jest przypisana nowa wartość wyliczenia przez funkcję członkowską.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego przechowuje `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca wartość **`*this`** .

### <a name="operator-bool"></a><a name="op_bool"></a> wartość logiczna operatora

Rzutuje zmienną typu `error_code` .

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna `error_code` obiektu.

#### <a name="remarks"></a>Uwagi

Operator zwraca wartość, która **`true`** jest możliwa do konwersji tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest konwertowany tylko na **`bool`** , nie do `void *` lub inne znane typy skalarne.

### <a name="value"></a><a name="value"></a> wartościami

Zwraca przechowywaną wartość kodu błędu.

```cpp
value_type value() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość przechowywanego kodu błędu typu [value_type](#value_type).

### <a name="value_type"></a><a name="value_type"></a> value_type

Typ reprezentujący przechowywaną wartość kodu błędu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Ta definicja typu jest synonimem dla **`int`** .
