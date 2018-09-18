---
title: _variant_t::Dołącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e680f4f42881ea89510048f43d657d1579686527
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109265"
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