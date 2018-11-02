---
title: Struktura RECT
ms.date: 11/04/2016
f1_keywords:
- LPRECT
- RECT
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
ms.openlocfilehash: 1cb997fc0f1ec89eabf5e4d2c2c5ccb15e3bafec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549018"
---
# <a name="rect-structure"></a>Struktura RECT

`RECT` Struktury określa współrzędne lewym i prawym dolnym rogu prostokąta.

## <a name="syntax"></a>Składnia

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>Elementy członkowskie

`left`<br/>
Określa współrzędną x lewego górnego rogu prostokąta.

`top`<br/>
Określa współrzędną y lewego górnego rogu prostokąta.

`right`<br/>
Określa współrzędną x w prawym dolnym rogu prostokąta.

`bottom`<br/>
Określa współrzędną y prawego dolnego rogu prostokąta.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** windef.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)
