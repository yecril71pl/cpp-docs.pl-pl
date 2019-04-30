---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403272"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft Specific**

Przypisuje ten ciąg `_variant_t` obiektu.

## <a name="syntax"></a>Składnia

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parametry

*pSrc*<br/>
Wskaźnik do ciągu znaków.

## <a name="remarks"></a>Uwagi

Konwertuje ciąg znaków ANSI Unicode `BSTR` ciąg, a następnie przypisuje go do tego `_variant_t` obiektu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)