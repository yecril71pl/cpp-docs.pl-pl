---
title: '&lt;system_error —&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d0a556505370078f599d6d667fa856723d9bac8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error —&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator ==

Testy, jeśli obiekt po lewej stronie operatora jest taki sam jak obiekt po prawej stronie.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Obiekt pod kątem równości.|
|`right`|Obiekt pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>  operator! =

Testy, jeśli obiekt po lewej stronie operatora nie jest taki sam jak obiekt po prawej stronie.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Obiekt pod kątem nierówności.|
|`right`|Obiekt pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli przekazano obiekt `left` nie jest równa przekazano obiekt `right`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `!(left == right)`.

## <a name="op_lt"></a>  Operator&lt;

Sprawdza, czy obiekt jest mniejszy niż obiekt przekazany do porównania.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`left`|Obiekt do porównania.|
|`right`|Obiekt do porównania.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli przekazano obiekt `left` jest mniejsza niż przekazano obiekt `right`; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza kolejność błędów.

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
