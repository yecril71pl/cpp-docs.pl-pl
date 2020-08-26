---
title: error_category — Klasa
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 218596ff5b81e99f4787efe2582fdc2752533cec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840170"
---
# <a name="error_category-class"></a>error_category — Klasa

Reprezentuje abstrakcyjną, popularną bazę dla obiektów, która opisuje kategorię kodów błędów.

## <a name="syntax"></a>Składnia

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Uwagi

Dwa wstępnie zdefiniowane obiekty implementują `error_category` : [generic_category](../standard-library/system-error-functions.md#generic_category) i [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[value_type](#value_type)|Typ reprezentujący przechowywaną wartość kodu błędu.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[default_error_condition](#default_error_condition)|Przechowuje wartość kodu błędu dla obiektu warunku błędu.|
|[samą](#equivalent)|Zwraca wartość określającą, czy obiekty błędów są równoważne.|
|[generic_category](#generic)||
|[Komunikat](#message)|Zwraca nazwę określonego kodu błędu.|
|[Nazwij](#name)|Zwraca nazwę kategorii.|
|[system_category](#system)||

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[operator =](#op_as)|Operator przypisania.|
|[operator = =](#op_eq_eq)|Testuje równość między `error_category` obiektami.|
|[operator! =](#op_neq)|Testuje pod kątem nierówności między `error_category` obiektami.|
|[<operatora ](#op_lt)|Testuje, czy obiekt [error_category](../standard-library/error-category-class.md) jest mniejszy niż `error_category` obiekt przeszedł do porównania.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a> default_error_condition

Przechowuje wartość kodu błędu dla obiektu warunku błędu.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

`_Errval`\
Wartość kodu błędu do zapisania w [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Uwagi

### <a name="equivalent"></a><a name="equivalent"></a> samą

Zwraca wartość określającą, czy obiekty błędów są równoważne.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Parametry

*_Errval*\
Wartość kodu błędu do porównania.

*_Cond*\
Obiekt [error_condition](../standard-library/error-condition-class.md) do porównania.

*_Code*\
Obiekt [error_code](../standard-library/error-code-class.md) do porównania.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli Kategoria i wartość są równe; w przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca `*this == _Cond.category() && _Cond.value() == _Errval` .

Druga funkcja członkowska zwraca wartość `*this == _Code.category() && _Code.value() == _Errval` .

### <a name="generic_category"></a><a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a> Komunikat

Zwraca nazwę określonego kodu błędu.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość kodu błędu do opisania.

#### <a name="return-value"></a>Wartość zwracana

Zwraca opisową nazwę kodu błędu *Val* dla kategorii. Jeśli kod błędu nie zostanie rozpoznany, zwraca `"unknown error"` .

#### <a name="remarks"></a>Uwagi

### <a name="name"></a><a name="name"></a> Nazwij

Zwraca nazwę kategorii.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę kategorii jako ciąg bajtowy zakończony wartością null.

### <a name="operator"></a><a name="op_as"></a> operator =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje równość między `error_category` obiektami.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt, który ma być testowany pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty są równe; **`false`** Jeśli obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Ten operator elementu członkowskiego zwraca `this == &right` .

### <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje pod kątem nierówności między `error_category` obiektami.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt, który ma być testowany pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_category` obiekt nie jest równy `error_category` obiektowi przekazanym w *prawej*; w przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `(!*this == right)` .

### <a name="operatorlt"></a><a name="op_lt"></a> zakład&lt;

Testuje, czy obiekt [error_category](../standard-library/error-category-class.md) jest mniejszy niż `error_category` obiekt przeszedł do porównania.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
`error_category`Obiekt, który ma zostać porównany.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_category` obiekt jest mniejszy niż `error_category` obiekt przeszedł do porównania; W przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `this < &right` .

### <a name="system_category"></a><a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a> value_type

Typ reprezentujący przechowywaną wartość kodu błędu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Ta definicja typu jest synonimem dla **`int`** .
