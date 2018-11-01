---
title: Struktura RGNDATA
ms.date: 11/04/2016
f1_keywords:
- RGNDATA
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
ms.openlocfilehash: d6ee25b490aa5c7055b4e8ccf63939fbdd8dd4ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638142"
---
# <a name="rgndata-structure"></a>Struktura RGNDATA

`RGNDATA` Struktura zawiera nagłówek i tablicę prostokąty wchodzących w skład region. Tych prostokątów posortowane od góry do dołu od lewej do prawej, nie pokrywają się.

## <a name="syntax"></a>Składnia

```
typedef struct _RGNDATA { /* rgnd */
    RGNDATAHEADER rdh;
    char Buffer[1];
} RGNDATA;
```

#### <a name="parameters"></a>Parametry

*rdh*<br/>
Określa [RGNDATAHEADER](/windows/desktop/api/wingdi/ns-wingdi-_rgndataheader) struktury. (Aby uzyskać więcej informacji na temat tej struktury, zobacz zestaw Windows SDK). Członkowie tej struktury Określ typ regionu (czy jest prostokątne lub trapezoidal), liczba prostokątami, które tworzą regionu, rozmiaru buforu, który zawiera struktury prostokąt, i tak dalej.

*Bufor*<br/>
Określa dowolnego rozmiaru buforu, który zawiera [Prostokąt](../../mfc/reference/rect-structure1.md) struktur, które składają się na region.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)<br/>
[CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

