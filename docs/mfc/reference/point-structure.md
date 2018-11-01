---
title: Struktura POINT
ms.date: 10/12/2018
f1_keywords:
- POINT
- LPPOINT
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
ms.openlocfilehash: c53f250b714c66e74a12432b879cbc4bcc1fd88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646904"
---
# <a name="point-structure"></a>Struktura POINT

`POINT` Struktury definiuje x*-* i współrzędne y punktu.

## <a name="syntax"></a>Składnia

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>Parametry

*x*<br/>
Określa współrzędną x punktu.

*y*<br/>
Określa współrzędną y punktu.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** windef.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint, klasa](../../atl-mfc-shared/reference/cpoint-class.md)
