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
ms.openlocfilehash: c63676e7bdf5ce1547b4feae16c7899ace545ad2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203367"
---
# <a name="error_condition-class"></a>error_condition — Klasa

Reprezentuje kody błędów zdefiniowane przez użytkownika.

## <a name="syntax"></a>Składnia

```cpp
class error_condition;
```

## <a name="remarks"></a>Uwagi

Obiekt typu `error_condition` przechowuje wartość kodu błędu i wskaźnik do obiektu, który reprezentuje [kategorię](../standard-library/error-category-class.md) kodów błędów używanych do raportowanych błędów zdefiniowanych przez użytkownika.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[error_condition](#error_condition)|Konstruuje obiekt typu `error_condition` .|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ reprezentujący przechowywaną wartość kodu błędu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[przypisać](#assign)|Przypisuje wartość kodu błędu i kategorię do warunku błędu.|
|[kategorii](#category)|Zwraca kategorię błędu.|
|[Wyczyść](#clear)|Czyści wartość kodu błędu i kategorię.|
|[Komunikat](#message)|Zwraca nazwę kodu błędu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator = =](#op_eq_eq)|Testuje równość między `error_condition` obiektami.|
|[operator! =](#op_neq)|Testuje pod kątem nierówności między `error_condition` obiektami.|
|[<operatora](#op_lt)|Testuje, czy `error_condition` obiekt jest mniejszy niż `error_code` obiekt przeszedł do porównania.|
|[operator =](#op_eq)|Przypisuje nowej wartości wyliczenia do `error_condition` obiektu.|
|[wartość logiczna operatora](#op_bool)|Rzutuje zmienną typu `error_condition` .|

### <a name="assign"></a><a name="assign"></a>ponownie

Przypisuje wartość kodu błędu i kategorię do warunku błędu.

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

### <a name="category"></a><a name="category"></a>kategorii

Zwraca kategorię błędu.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do przechowywanej kategorii błędów

#### <a name="remarks"></a>Uwagi

### <a name="clear"></a><a name="clear"></a>Wyczyść

Czyści wartość kodu błędu i kategorię.

```cpp
clear();
```

#### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje zero wartości kodu błędu i wskaźnik do obiektu [generic_category](../standard-library/system-error-functions.md#generic_category) .

### <a name="error_condition"></a><a name="error_condition"></a>error_condition

Konstruuje obiekt typu `error_condition` .

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość kodu błędu, która ma być przechowywana w `error_condition` .

*_Cat*\
Kategoria błędów do przechowywania w `error_condition` .

*_Errcode*\
Wartość wyliczenia, która ma być przechowywana w `error_condition` .

#### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje zero wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category).

Drugi Konstruktor przechowuje *Val* jako wartość kodu błędu i wskaźnik do [error_category](../standard-library/error-category-class.md).

Trzeci Konstruktor przechowuje `(value_type)_Errcode` jako wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a><a name="message"></a>Komunikat

Zwraca nazwę kodu błędu.

```cpp
string message() const;
```

#### <a name="return-value"></a>Wartość zwracana

`string`Reprezentujący nazwę kodu błędu.

#### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwraca `category().message(value())` .

### <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje równość między `error_condition` obiektami.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Ojbect do przetestowania pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty są równe; **`false`** Jeśli obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() == right.category() && value == right.value()` .

### <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje pod kątem nierówności między `error_condition` obiektami.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt, który ma być testowany pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_condition` obiekt nie jest równy `error_condition` obiektowi przekazanym w *prawej*; w przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `!(*this == right)` .

### <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy `error_condition` obiekt jest mniejszy niż `error_code` obiekt przeszedł do porównania.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
`error_condition`Obiekt, który ma zostać porównany.

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `error_condition` obiekt jest mniejszy niż `error_condition` obiekt przeszedł do porównania; W przeciwnym razie **`false`** .

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `category() < right.category() || category() == right.category() && value < right.value()` .

### <a name="operator"></a><a name="op_eq"></a>operator =

Przypisuje nowej wartości wyliczenia do `error_condition` obiektu.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>Parametry

*_Errcode*\
Wartość wyliczenia, która ma zostać przypisana do `error_condition` obiektu.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do `error_condition` obiektu, do którego jest przypisana nowa wartość wyliczenia przez funkcję członkowską.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego przechowuje `(value_type)error` jako wartość kodu błędu i wskaźnik do [generic_category](../standard-library/system-error-functions.md#generic_category). Zwraca wartość **`*this`** .

### <a name="operator-bool"></a><a name="op_bool"></a>wartość logiczna operatora

Rzutuje zmienną typu `error_condition` .

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna `error_condition` obiektu.

#### <a name="remarks"></a>Uwagi

Operator zwraca wartość, która **`true`** jest możliwa do konwersji tylko wtedy, gdy [wartość](#value) nie jest równa zero. Typ zwracany jest konwertowany tylko na **`bool`** , nie do `void *` lub inne znane typy skalarne.

### <a name="value"></a><a name="value"></a>wartościami

Zwraca przechowywaną wartość kodu błędu.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość przechowywanego kodu błędu typu [value_type](#value_type).

#### <a name="remarks"></a>Uwagi

### <a name="value_type"></a><a name="value_type"></a>value_type

Typ reprezentujący przechowywaną wartość kodu błędu.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Definicja typu jest synonimem dla **`int`** .
