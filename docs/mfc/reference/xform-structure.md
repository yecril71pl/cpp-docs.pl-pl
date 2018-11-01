---
title: Struktura XFORM
ms.date: 11/04/2016
f1_keywords:
- XFORM
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
ms.openlocfilehash: 621a01accf3c323f8098da68667f06f48b9d169b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457257"
---
# <a name="xform-structure"></a>Struktura XFORM

`XFORM` Struktura ma następującą postać:

## <a name="syntax"></a>Składnia

```
typedef struct  tagXFORM {  /* xfrm */
    FLOAT eM11;
    FLOAT eM12;
    FLOAT eM21;
    FLOAT eM22;
    FLOAT eDx;
    FLOAT eDy;
} XFORM;
```

## <a name="remarks"></a>Uwagi

`XFORM` Struktury określa miejsce na świecie transformację miejsce na stronie. `eDx` i `eDy` członków Określ składniki poziome i pionowe tłumaczenia, odpowiednio. W poniższej tabeli przedstawiono, jak inni członkowie są używane, w zależności od operacji:

|Operacja|eM11|eM12|eM21|eM22|
|---------------|----------|----------|----------|----------|
|`Rotation`|Cosinus kąta obrotu|Sinus kąta obrotu|Ujemna sinus kąta obrotu|Cosinus kąta obrotu|
|`Scaling`|Poziomy skalowania składnika|Nothing|Nothing|Składnik skalowanie pionowe|
|`Shear`|Nothing|Poziomy proporcjonalności — stała|Pionowe proporcjonalności — stała|Nothing|
|`Reflection`|Składnik poziomy odbicia|Nothing|Nothing|Składnik pionowy odbicia|

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

