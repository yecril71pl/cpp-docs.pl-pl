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
ms.openlocfilehash: 3ed2eceb60c2efa78181faea58a256b0e35d489f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076614"
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

Dwa wstępnie zdefiniowane obiekty implementują `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) i [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ reprezentujący przechowywaną wartość kodu błędu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[default_error_condition](#default_error_condition)|Przechowuje wartość kodu błędu dla obiektu warunku błędu.|
|[samą](#equivalent)|Zwraca wartość określającą, czy obiekty błędów są równoważne.|
|[generic_category](#generic)||
|[komunikat](#message)|Zwraca nazwę określonego kodu błędu.|
|[Nazwij](#name)|Zwraca nazwę kategorii.|
|[system_category](#system)||

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_as)||
|[operator = =](#op_eq_eq)|Testuje równość między obiektami `error_category`.|
|[operator!=](#op_neq)|Testuje pod kątem nierówności między obiektami `error_category`.|
|[< operatora](#op_lt)|Testuje, czy obiekt [error_category](../standard-library/error-category-class.md) jest mniejszy niż obiekt `error_category` przeszedł do porównania.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

Przechowuje wartość kodu błędu dla obiektu warunku błędu.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

*_Errval*\
Wartość kodu błędu do zapisania w [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Uwagi

### <a name="equivalent"></a><a name="equivalent"></a>samą

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

**prawda** , jeśli Kategoria i wartość są równe; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca `*this == _Cond.category() && _Cond.value() == _Errval`.

Druga funkcja członkowska zwraca `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>Komunikat

Zwraca nazwę określonego kodu błędu.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parametry

*val*\
Wartość kodu błędu do opisania.

#### <a name="return-value"></a>Wartość zwracana

Zwraca opisową nazwę kodu błędu *Val* dla kategorii.

#### <a name="remarks"></a>Uwagi

### <a name="name"></a><a name="name"></a>Nazwij

Zwraca nazwę kategorii.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę kategorii jako ciąg bajtowy zakończony wartością null.

### <a name="operator"></a><a name="op_as"></a>operator =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje równość między obiektami `error_category`.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*prawa*\
Obiekt, który ma być testowany pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli obiekty są równe; **Fałsz** , jeśli obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Ten operator elementu członkowskiego zwraca `this == &right`.

### <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje pod kątem nierówności między obiektami `error_category`.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*prawa*\
Obiekt, który ma być testowany pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli obiekt `error_category` nie jest równy obiektowi `error_category` przekazaną w *prawej*; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `(!*this == right)`.

### <a name="operatorlt"></a><a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt [error_category](../standard-library/error-category-class.md) jest mniejszy niż obiekt `error_category` przeszedł do porównania.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*prawa*\
Obiekt `error_category`, który ma zostać porównany.

#### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli obiekt `error_category` jest mniejszy niż obiekt `error_category` przeszedł do porównania; W przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `this < &right`.

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Typ reprezentujący przechowywaną wartość kodu błędu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Ta definicja typu jest synonimem dla **int**.
