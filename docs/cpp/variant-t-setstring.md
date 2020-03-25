---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187560"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Specyficzne dla firmy Microsoft**

Przypisuje ciąg do tego obiektu `_variant_t`.

## <a name="syntax"></a>Składnia

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Wskaźnik do ciągu znaków.

## <a name="remarks"></a>Uwagi

Konwertuje ciąg znaków ANSI na ciąg `BSTR` Unicode i przypisuje go do tego `_variant_t` obiektu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
