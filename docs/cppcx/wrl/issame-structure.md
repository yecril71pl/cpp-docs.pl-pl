---
title: IsSame — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371346"
---
# <a name="issame-structure"></a>IsSame — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ.

*T2*<br/>
Inny typ.

## <a name="remarks"></a>Uwagi

Sprawdza, czy jeden określony typ jest taki sam jak inny określony typ.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Stałe publiczne

Nazwa                    | Opis
----------------------- | --------------------------------------------------
[IsSame::wartość](#value) | Wskazuje, czy jeden typ jest taki sam jak inny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsSame`

## <a name="requirements"></a>Wymagania

**Nagłówek:** internal.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="issamevalue"></a><a name="value"></a>IsSame::wartość

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Uwagi

Wskazuje, czy jeden typ jest taki sam jak inny.

`value`jest **true,** jeśli parametry szablonu są takie same i **false,** jeśli parametry szablonu są różne.
