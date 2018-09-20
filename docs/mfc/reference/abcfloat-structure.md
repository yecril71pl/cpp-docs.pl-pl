---
title: Struktura ABCFLOAT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375417"
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

