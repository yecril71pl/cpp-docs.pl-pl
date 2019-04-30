---
title: '&lt;system_error —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: d5c8f49c4a38862d62b7fe8212d98c87949fecfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412127"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error —&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator ==

Sprawdza, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt, który ma zostać przetestowana pod kątem równości.|
|*right*|Obiekt, który ma zostać przetestowana pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>  operator! =

Sprawdza, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt, który ma zostać przetestowana pod kątem nierówności.|
|*right*|Obiekt, który ma zostać przetestowana pod kątem nierówności.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt przekazany w *po lewej stronie* nie jest równa przekazany obiekt *prawo*; w przeciwnym razie **false**.

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
|*left*|Obiekt do porównania.|
|*right*|Obiekt do porównania.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt przekazany w *po lewej stronie* jest mniejszy niż obiekt przekazany w *prawo*; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza kolejność błędów.

## <a name="see-also"></a>Zobacz także

[<system_error>](../standard-library/system-error.md)<br/>
