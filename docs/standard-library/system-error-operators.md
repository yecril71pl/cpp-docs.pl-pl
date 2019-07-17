---
title: '&lt;system_error —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246208"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error —&gt; operatorów

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt, który ma zostać przetestowana pod kątem równości.

*po prawej stronie*\
Obiekt, który ma zostać przetestowana pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; **false** obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a> operator! =

Sprawdza, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt, który ma zostać przetestowana pod kątem nierówności.

*po prawej stronie*\
Obiekt, który ma zostać przetestowana pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt przekazany w *po lewej stronie* nie jest równa przekazany obiekt *prawo*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `!(left == right)`.

## <a name="op_lt"></a> Operator&lt;

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

*po lewej stronie*\
Obiekt do porównania.

*po prawej stronie*\
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt przekazany w *po lewej stronie* jest mniejszy niż obiekt przekazany w *prawo*; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza kolejność błędów.

## <a name="op_ostream"></a> Operator&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
