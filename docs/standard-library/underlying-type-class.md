---
title: Klasa underlying_type
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 465383357e6c0306c24fe8325327327c3a3b64c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454985"
---
# <a name="underlyingtype-class"></a>Klasa underlying_type

Tworzy podstawowy typ całkowity dla typu wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Element typedef `type` elementu członkowskiego klasy szablonu nazywa się podstawowym typem całkowitym t, gdy t jest typem wyliczenia, w przeciwnym razie nie ma składowej typedef.  `type`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
