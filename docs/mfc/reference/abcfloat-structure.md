---
title: Struktura ABCFLOAT
ms.date: 11/04/2016
f1_keywords:
- ABCFLOAT
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
ms.openlocfilehash: b9e3923e8c70e38fe5efe959db8da43118cc6445
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443666"
---
# <a name="abcfloat-structure"></a>Struktura ABCFLOAT

`ABCFLOAT` Struktura zawiera A, B i C szerokości czcionki znaku.

## <a name="syntax"></a>Składnia

```
typedef struct _ABCFLOAT { /* abcf */
    FLOAT abcfA;
    FLOAT abcfB;
    FLOAT abcfC;
} ABCFLOAT;
```

#### <a name="parameters"></a>Parametry

*abcfA*<br/>
Określa odstępy A znaku. Element jest odległość do dodania do bieżącego położenia przed narysowaniem symbol znaku.

*abcfB*<br/>
Określa odstępy B znaku. Odstępy B jest szerokość rysowane część symbol znaku.

*abcfC*<br/>
Określa odstępy C znaku. Odstępy C jest odległość, aby dodać do aktualnej pozycji, aby zapewnić biały znak z prawej strony symbolu znaku.

## <a name="remarks"></a>Uwagi

Szerokości A, B i C są mierzone wzdłuż linii bazowej czcionki. Przyrost znak (łączna szerokość), znaku jest sumą A, B i C miejsca do magazynowania. Element lub miejsca C może być ujemna na wskazywać underhangs lub znacznego udziału.

## <a name="requirements"></a>Wymagania

**Nagłówek:** wingdi.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

