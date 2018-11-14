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
ms.openlocfilehash: 719852c4556291747b612d54c44d4bf82caa9188
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519009"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Microsoft Specific**

Odłącza zhermetyzowany `VARIANT` obiektu z tego `_variant_t` obiektu.

## <a name="syntax"></a>Składnia

```
VARIANT Detach( );
```

## <a name="return-value"></a>Wartość zwracana

Zhermetyzowany `VARIANT`.

## <a name="remarks"></a>Uwagi

Wyodrębnia i zwraca zhermetyzowany `VARIANT`, powoduje to wyczyszczenie `_variant_t` obiektu bez niszczenia samego go. Ta funkcja członkowska usuwa `VARIANT` z hermetyzacji i zestawy `VARTYPE` tego `_variant_t` obiektu VT_EMPTY. To pozwala zwolnić zwracanego `VARIANT` przez wywołanie metody [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) funkcji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)