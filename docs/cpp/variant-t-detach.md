---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500559"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft Specific**

Odłącza `VARIANT` obiekt hermetyzowany z tego `_variant_t` obiektu.

## <a name="syntax"></a>Składnia

```
VARIANT Detach( );
```

## <a name="return-value"></a>Wartość zwracana

Hermetyzowane `VARIANT`.

## <a name="remarks"></a>Uwagi

Wyodrębnia i zwraca hermetyzowane `VARIANT`, a następnie czyści ten `_variant_t` obiekt bez jego niszczenia. Ta funkcja członkowska usuwa `VARIANT` hermetyzację i `VARTYPE` ustawia ten `_variant_t` obiekt na VT_EMPTY. Można zwolnić zwrócone `VARIANT` przez wywołanie funkcji [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)