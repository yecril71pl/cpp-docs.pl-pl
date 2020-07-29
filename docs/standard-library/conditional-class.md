---
title: conditional — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: 03ec6248ba3361622ad061ac3854a60995148f4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228378"
---
# <a name="conditional-class"></a>conditional — Klasa

Wybiera jeden z dwóch typów, w zależności od określonego warunku.

## <a name="syntax"></a>Składnia

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Parametry

*B*\
Wartość, która określa wybrany typ.

*Połączeń*\
Wynik typu, gdy B ma wartość true.

*T2*\
Wynik typu, gdy B ma wartość false.

## <a name="remarks"></a>Uwagi

Element członkowski szablonu typedef `conditional<B, T1, T2>::type` szacuje się na *T1* , gdy *b* szacuje się w **`true`** , i przyjmuje wartość *T2* , gdy *b* szacuje się **`false`** .

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
