---
title: Struktura LOGBRUSH | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bef2c9b9219231b6a61bfad0a282b3af1b4e0c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374778"
---
# <a name="logbrush-structure"></a>Struktura LOGBRUSH

`LOGBRUSH` Definiuje struktury, style, kolor i wzoru pędzla fizycznych. Jest on używany przez Windows [CreateBrushIndirect](/windows/desktop/api/wingdi/nf-wingdi-createbrushindirect) i [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen) funkcji.

## <a name="syntax"></a>Składnia

```
typedef struct tag LOGBRUSH { /* lb */
    UINT lbStyle;
    COLORREF lbColor;
    LONG lbHatch;
} LOGBRUSH;
```

#### <a name="parameters"></a>Parametry

*lbStyle*<br/>
Określa styl pędzla. `lbStyle` Element członkowski musi mieć jedną z następujących stylów:

- Pędzla wzoru BS_DIBPATTERN A zdefiniowane przez mapę bitową niezależnych od urządzenia (DIB) specyfikacji. Jeśli *lbStyle* jest BS_DIBPATTERN, `lbHatch` elementu członkowskiego zawiera dojście do upakowaną DIB.

- Pędzla wzoru BS_DIBPATTERNPT A zdefiniowane przez mapę bitową niezależnych od urządzenia (DIB) specyfikacji. Jeśli *lbStyle* jest BS_DIBPATTERNPT, `lbHatch` elementu członkowskiego zawiera wskaźnik do upakowaną DIB.

- Wyklutych BS_HATCHED pędzla.

- Pusty BS_HOLLOW pędzla.

- BS_NULL taki sam jak BS_HOLLOW.

- Pędzel BS_PATTERN wzorzec zdefiniowany przez mapę bitową w pamięci.

- BS_SOLID pędzla.

*lbColor*<br/>
Określa kolor, w którym ma być rysowany pędzla. Jeśli *lbStyle* jest styl BS_HOLLOW lub BS_PATTERN *lbColor* jest ignorowana. Jeśli *lbStyle* BS_DIBPATTERN lub BS_DIBPATTERNBT, słowo niskiego rzędu *lbColor* Określa, czy `bmiColors` członkowie [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) struktury zawiera jawne czerwony, zielony, niebieski wartości (RGB) lub wskaźniki do aktualnie zrealizowane logiczną paletę. `lbColor` Element członkowski musi mieć jedną z następujących wartości:

- DIB_PAL_COLORS tabeli kolorów składa się z tablicy wskaźników 16-bitowych do aktualnie zrealizowane palety logiczne.

- DIB_RGB_COLORS tabeli kolorów zawiera wartości RGB literału.

*lbHatch*<br/>
Określa styl kreskowania. Znaczenie zależy od stylu pędzla, zdefiniowane przez *lbStyle*. Jeśli *lbStyle* jest BS_DIBPATTERN, `lbHatch` elementu członkowskiego zawiera dojście do upakowaną DIB. Jeśli *lbStyle* jest BS_DIBPATTERNPT, `lbHatch` elementu członkowskiego zawiera wskaźnik do upakowaną DIB. Jeśli *lbStyle* jest BS_HATCHED, `lbHatch` elementu członkowskiego Określa orientację wiersze użyty do utworzenia kreskowania. Może to być jedna z następujących wartości:

- HS_BDIAGONAL A 45 stopni palcem, od lewej do prawej kreskowania

- HS_CROSS poziome i pionowe kreskowany

- Kreskowany 45 stopni HS_DIAGCROSS

- HS_FDIAGONAL A 45 stopni w dół, od lewej do prawej kreskowania

- Kreskowanie poziome HS_HORIZONTAL

- Kreskowanie pionowe HS_VERTICAL

Jeśli *lbStyle* jest BS_PATTERN, *lbHatch* jest uchwytem do mapy bitowej, który definiuje wzorzec. Jeśli *lbStyle* BS_SOLID lub BS_HOLLOW, *lbHatch* jest ignorowana.

## <a name="remarks"></a>Uwagi

Mimo że *lbColor* Określa kolor pierwszego planu pędzel kreskowania [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) i [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) funkcje sterowania kolor tła.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

