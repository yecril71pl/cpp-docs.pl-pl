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
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435077"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Microsoft Specific**

Dołącza `VARIANT` do obiektu **_variant_t** obiektu.

## <a name="syntax"></a>Składnia

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
A `VARIANT` obiekt dołączony do tego **_variant_t** obiektu.

## <a name="remarks"></a>Uwagi

Przejmuje na własność `VARIANT` poprzez hermetyzację go. Ta funkcja elementu członkowskiego zwalnia wszystkie istniejące hermetyzowane `VARIANT`, następnie kopiuje podane `VARIANT`i ustawia jego `VARTYPE` do VT_EMPTY, aby upewnić się, że można zwolnić tylko jej zasoby, **_variant_t** destruktor.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)