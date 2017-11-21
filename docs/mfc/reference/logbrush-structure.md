---
title: Struktura LOGBRUSH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LOGBRUSH
dev_langs: C++
helpviewer_keywords: LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: abc5a751d6edf0aa5d51666592927bf5713d1908
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="logbrush-structure"></a>Struktura LOGBRUSH
`LOGBRUSH` Struktury definiuje styl, kolor i wzorzec fizycznych pędzla. Jest on używany przez system Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) i [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Parametry  
 `lbStyle`  
 Określa styl pędzla. `lbStyle` Elementu członkowskiego musi być jedną z następujących stylów:  
  
- **BS_DIBPATTERN** pędzla w specyfikacji map bitowych niezależnych od urządzenia (DIB). Jeśli `lbStyle` jest **BS_DIBPATTERN**, **lbHatch** elementu członkowskiego zawiera dojścia do spakowanej DIB.  
  
- **BS_DIBPATTERNPT** pędzla w specyfikacji map bitowych niezależnych od urządzenia (DIB). Jeśli `lbStyle` jest **BS_DIBPATTERNPT**, **lbHatch** elementu członkowskiego zawiera wskaźnik do spakowanej DIB.  
  
- **BS_HATCHED** wyklutych pędzla.  
  
- **BS_HOLLOW** pusty pędzla.  
  
- **BS_NULL** taki sam jak **BS_HOLLOW**.  
  
- **BS_PATTERN** wzoru pędzla wynika z mapą bitową pamięci.  
  
- **BS_SOLID** pędzla pełnego koloru.  
  
 `lbColor`  
 Określa kolor, w którym ma być rysowany pędzla. Jeśli `lbStyle` jest **BS_HOLLOW** lub **BS_PATTERN** styl **lbColor** jest ignorowana. Jeśli `lbStyle` jest **BS_DIBPATTERN** lub **BS_DIBPATTERNBT**, wyrazu znaczącymi bitami **lbColor** Określa, czy **bmiColors**członkami [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) struktura zawiera jawne czerwony, zielony, niebieski wartości (RGB) lub wskaźników do aktualnie zrealizowanych logiczną paletę. **LbColor** elementu członkowskiego musi być jedną z następujących wartości:  
  
- **DIB_PAL_COLORS** tabeli kolorów składa się z tablicy 16-bitowych wskaźników do aktualnie zrealizowanych logiczną paletę.  
  
- **DIB_RGB_COLORS** tabeli kolorów zawiera wartości RGB literałów.  
  
 *lbHatch*  
 Określa styl kreskowania. Znaczenie zależy od styl pędzla zdefiniowane przez `lbStyle`. Jeśli `lbStyle` jest **BS_DIBPATTERN**, **lbHatch** elementu członkowskiego zawiera dojścia do spakowanej DIB. Jeśli `lbStyle` jest **BS_DIBPATTERNPT**, **lbHatch** elementu członkowskiego zawiera wskaźnik do spakowanej DIB. Jeśli `lbStyle` jest **BS_HATCHED**, **lbHatch** elementu członkowskiego Określa orientację pozwala utworzyć kreskowania linii. Może być jedną z następujących wartości:  
  
- `HS_BDIAGONAL`Kreskowania górę, od lewej do prawej 45 stopni  
  
- `HS_CROSS`Kreskowany poziome i pionowe  
  
- `HS_DIAGCROSS`Kreskowany 45 stopni  
  
- `HS_FDIAGONAL`Kreskowania 45 stopni w dół, od lewej do prawej  
  
- `HS_HORIZONTAL`Poziomy kreskowania  
  
- `HS_VERTICAL`Pionowy kreskowania  
  
 Jeśli `lbStyle` jest **BS_PATTERN**, **lbHatch** jest dojścia do mapy bitowej, który definiuje wzorzec. Jeśli `lbStyle` jest **BS_SOLID** lub **BS_HOLLOW**, **lbHatch** jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 Mimo że **lbColor** Określa kolor pierwszego planu pędzla kreskowania [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) i [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) funkcje kontroli kolor tła.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

