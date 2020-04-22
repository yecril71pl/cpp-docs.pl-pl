---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 60ad1c1bd95eb35f2a4f2800f79d0326c68a1176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745851"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Specyficzne dla firmy Microsoft**

Przypisuje ciąg do `_variant_t` tego obiektu.

## <a name="syntax"></a>Składnia

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*Psrc*<br/>
Wskaźnik do ciągu znaków.

## <a name="remarks"></a>Uwagi

Konwertuje ciąg znaków ANSI `BSTR` na ciąg Unicode `_variant_t` i przypisuje go do tego obiektu.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Klasa _variant_t](../cpp/variant-t-class.md)
