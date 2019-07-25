---
title: conditional — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457323"
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

*POŁĄCZEŃ*\
Wynik typu, gdy B ma wartość true.

*T2*\
Wynik typu, gdy B ma wartość false.

## <a name="remarks"></a>Uwagi

Element członkowski szablonu typedef `conditional<B, T1, T2>::type` szacuje się na *T1* , gdy *b* zwróci **wartość true**, i szacuje się na *T2* , gdy *b* zwróci **wartość false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
