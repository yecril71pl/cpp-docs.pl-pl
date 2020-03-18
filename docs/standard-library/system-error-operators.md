---
title: '&lt;system_error operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420730"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;system_error operatory&gt;

## <a name="op_eq_eq"></a>operator = =

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

\ *lewo*
Obiekt, który ma być testowany pod kątem równości.

*prawa*\
Obiekt, który ma być testowany pod kątem równości.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli obiekty są równe; **Fałsz** , jeśli obiekty nie są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt, który ma być testowany pod kątem nierówności.

*prawa*\
Obiekt, który ma być testowany pod kątem nierówności.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obiekt przeszedł *po lewej stronie* nie jest równy obiektowi przekazannym w *prawej*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja zwraca `!(left == right)`.

## <a name="op_lt"></a>&lt; operatora

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

\ *lewo*
Obiekt do porównania.

*prawa*\
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli obiekt przeszedł *po lewej stronie* jest mniejszy niż obiekt przeszedł w *prawo*; W przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza kolejność błędów.

## <a name="op_ostream"></a>&lt;operatora &lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
