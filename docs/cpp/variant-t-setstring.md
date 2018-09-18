---
title: _variant_t::SetString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52ea719a2c9296ca1e64d881ac150994c041e206
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018733"
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