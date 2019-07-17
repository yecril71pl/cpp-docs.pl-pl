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
ms.openlocfilehash: 308fa1a2309ddfda1a02fe6a687360185c1e7c6e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245851"
---
# <a name="errorcategory-class"></a>error_category — Klasa

Reprezentuje podstawę abstrakcyjne, wspólne dla obiektów opisująca kategorię kody błędów.

## <a name="syntax"></a>Składnia

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Uwagi

Implementowanie dwa wstępnie zdefiniowanych obiektów `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) i [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Typ, który reprezentuje wartość kodu błędu przechowywanych.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[default_error_condition](#default_error_condition)|Przechowuje wartość kodu błędu dla obiektu warunku błędu.|
|[equivalent](#equivalent)|Zwraca wartość określającą, czy błąd obiekty są równoważne.|
|[generic_category](#generic)||
|[komunikat](#message)|Zwraca nazwę określonego kodu błędu.|
|[name](#name)|Zwraca nazwę kategorii.|
|[system_category](#system)||

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)|Testuje pod kątem równości pomiędzy `error_category` obiektów.|
|[operator!=](#op_neq)|Testuje pod kątem nierówności pomiędzy `error_category` obiektów.|
|[Operator <](#op_lt)|Sprawdza, czy [error_category](../standard-library/error-category-class.md) obiekt jest mniejszy od `error_category` obiekt przekazany do porównania.|

## <a name="default_error_condition"></a> default_error_condition —

Przechowuje wartość kodu błędu dla obiektu warunku błędu.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parametry

*_Errval*\
Wartość kodu błędu, aby przechowywać w [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Wartość zwracana

Zwraca `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Uwagi

### <a name="equivalent"></a> równoważne

Zwraca wartość określającą, czy błąd obiekty są równoważne.

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
[Error_condition](../standard-library/error-condition-class.md) obiekt do porównania.

*_Fragmenty*\
[Error_code](../standard-library/error-code-class.md) obiekt do porównania.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kategorii i wartości są równe; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca `*this == _Cond.category() && _Cond.value() == _Errval`.

Druga funkcja elementu członkowskiego zwraca `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a> Komunikat

Zwraca nazwę określonego kodu błędu.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parametry

*Val*\
Wartość kodu błędu do opisu.

#### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę opisową kod błędu: *val* dla kategorii.

#### <a name="remarks"></a>Uwagi

### <a name="name"></a> Nazwa

Zwraca nazwę kategorii.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę kategorii jako ciąg znaków zakończony znakiem null bajtów.

### <a name="op_as"></a> operator =

```cpp
error_category& operator=(const error_category&) = delete;
```


### <a name="op_eq_eq"></a> operator ==

Testuje pod kątem równości pomiędzy `error_category` obiektów.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
Obiekt, który ma zostać przetestowana pod kątem równości.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

#### <a name="remarks"></a>Uwagi

Ten operator elementu członkowskiego zwraca `this == &right`.

### <a name="op_neq"></a> operator! =

Testuje pod kątem nierówności pomiędzy `error_category` obiektów.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
Obiekt, który ma zostać przetestowana pod kątem nierówności.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_category` obiektu nie jest równa `error_category` obiekt przekazany w *prawo*; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `(!*this == right)`.

### <a name="op_lt"></a> Operator&lt;

Sprawdza, czy [error_category](../standard-library/error-category-class.md) obiekt jest mniejszy od `error_category` obiekt przekazany do porównania.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parametry

*po prawej stronie*\
`error_category` Obiekt do porównania.

#### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `error_category` obiekt jest mniejszy od `error_category` obiekt przekazany do porównania; W przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zwraca `this < &right`.

### <a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a> value_type

Typ, który reprezentuje wartość kodu błędu przechowywanych.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Uwagi

Ta definicja typu jest synonimem dla **int**.
