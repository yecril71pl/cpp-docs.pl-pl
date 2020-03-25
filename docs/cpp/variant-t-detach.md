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
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187742"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Specyficzne dla firmy Microsoft**

Odłącza obiekt hermetyzowany `VARIANT` z tego obiektu `_variant_t`.

## <a name="syntax"></a>Składnia

```
VARIANT Detach( );
```

## <a name="return-value"></a>Wartość zwracana

`VARIANT`hermetyzowane.

## <a name="remarks"></a>Uwagi

Wyodrębnia i zwraca hermetyzowane `VARIANT`, a następnie czyści ten obiekt `_variant_t` bez niszczenia go. Ta funkcja członkowska usuwa `VARIANT` z hermetyzacji i ustawia `VARTYPE` tego obiektu `_variant_t` na VT_EMPTY. Aby zwolnić zwrócone `VARIANT`, można wywołać funkcję [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
