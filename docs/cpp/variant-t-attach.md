---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: d0822dfc730cbbb64f8364e6fa8fe8bc7207f9f9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750739"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Specyficzne dla firmy Microsoft**

Dołącza `VARIANT` obiekt do **obiektu _variant_t.**

## <a name="syntax"></a>Składnia

```cpp
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc ( varSrc )*<br/>
Obiekt, `VARIANT` który ma być dołączony do tego **_variant_t** obiektu.

## <a name="remarks"></a>Uwagi

Przejmuje na `VARIANT` własność przez hermetyzację go. Ta funkcja elementu członkowskiego zwalnia `VARIANT`wszystkie istniejące hermetyzowane , a następnie kopiuje dostarczone `VARIANT`i ustawia jego `VARTYPE` VT_EMPTY, aby upewnić się, że jego zasoby mogą być zwolnione tylko przez **_variant_t** destruktora.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Klasa _variant_t](../cpp/variant-t-class.md)
