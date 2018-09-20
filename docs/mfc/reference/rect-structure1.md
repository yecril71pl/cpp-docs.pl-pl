---
title: Struktura1 RECT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa77af9dd97afc2e9b0cfb94c1fd4c69a50f309b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419597"
---
# <a name="rect-structure1"></a>Struktura1 RECT

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
