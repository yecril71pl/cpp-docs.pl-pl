---
title: '&lt;&gt;operatory system_error'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5ddd9135749c2dcfd40cd06a9b69cff65b1a8c8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232875"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;&gt;operatory system_error

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt, który ma być testowany pod kątem równości.

*Kliknij*\
Obiekt, który ma być testowany pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty są równe; **`false`** Jeśli obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca wartość `left.category() == right.category() && left.value() == right.value()` .

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt, który ma być testowany pod kątem nierówności.

*Kliknij*\
Obiekt, który ma być testowany pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt przeszedł *po lewej stronie* nie jest równy obiektowi przekazannym w *prawej*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca wartość `!(left == right)` .

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

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

*lewym*\
Obiekt do porównania.

*Kliknij*\
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt przeszedł *po lewej stronie* jest mniejszy niż obiekt przeszedł w *prawo*; W przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza kolejność błędów.

## <a name="operatorltlt"></a><a name="op_ostream"></a>zakład&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
