---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 319c4fde808932e86021ee59b051261c43ca2edd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166207"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Microsoft Specific**

Zmienia typ `_variant_t` wskazany obiekt `VARTYPE`.

## <a name="syntax"></a>Składnia

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Parametry

*vartype*<br/>
`VARTYPE` Tego `_variant_t` obiektu.

*pSrc*<br/>
Wskaźnik do `_variant_t` obiekt do skonwertowania. Jeśli ta wartość wynosi NULL, konwersja odbywa się w miejscu.

## <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego konwertuje `_variant_t` wskazany obiekt `VARTYPE`. Jeśli *pSrc* ma wartość NULL, konwersja odbywa się w miejscu, w przeciwnym razie to `_variant_t` obiekt jest kopiowany z *pSrc* , a następnie konwertowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)