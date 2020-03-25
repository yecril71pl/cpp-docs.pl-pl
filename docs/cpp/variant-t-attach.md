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
ms.openlocfilehash: 3792ed4d0fcd86c4a4e846771c450413fda130b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187768"
---
# <a name="_variant_tattach"></a>_variant_t::Attach

**Specyficzne dla firmy Microsoft**

Dołącza obiekt `VARIANT` do obiektu **_variant_t** .

## <a name="syntax"></a>Składnia

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
Obiekt `VARIANT` do dołączenia do tego obiektu **_variant_t** .

## <a name="remarks"></a>Uwagi

Przejmuje własność `VARIANT` przez hermetyzację. Ta funkcja członkowska zwalnia wszystkie istniejące hermetyzowane `VARIANT`, kopiuje podane `VARIANT`i ustawia `VARTYPE` do VT_EMPTY, aby upewnić się, że jego zasoby mogą być wydane tylko przez destruktor **_variant_t** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
