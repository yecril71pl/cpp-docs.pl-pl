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
ms.openlocfilehash: 8c209d5a8d2a35f2643e90e5595d86f41519f30b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216560"
---
# <a name="issame-structure"></a>IsSame — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

Testuje, czy jeden określony typ jest taki sam jak inny określony typ.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constants"></a>Stałe publiczne

Nazwa                    | Opis
----------------------- | --------------------------------------------------
[IsSame:: value](#value) | Wskazuje, czy jeden typ jest taki sam, jak inny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IsSame`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Internal. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="issamevalue"></a><a name="value"></a>IsSame:: value

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

Wskazuje, czy jeden typ jest taki sam, jak inny.

`value`czy **`true`** Parametry szablonu są takie same, a **`false`** Jeśli parametry szablonu są różne.
