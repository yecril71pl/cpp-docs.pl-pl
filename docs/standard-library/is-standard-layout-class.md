---
title: is_standard_layout — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: fba77be22796f3cb5495543d262dd270ac13d598
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560598"
---
# <a name="is_standard_layout-class"></a>is_standard_layout — Klasa

Testuje, czy typ jest układem standardowym.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania

## <a name="remarks"></a>Uwagi

Wystąpienie tego predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma standardowy układ obiektów składowych w pamięci, w przeciwnym razie ma wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[<type_traits>](../standard-library/type-traits.md)
