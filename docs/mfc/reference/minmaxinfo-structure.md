---
title: Struktura MINMAXINFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63589edbe47aa09b8a6be92b5b7eb7e29077c96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402294"
---
# <a name="minmaxinfo-structure"></a>Struktura MINMAXINFO

`MINMAXINFO` Struktura zawiera informacje dotyczące rozmiaru w trybie zmaksymalizowanym okna i położenie i rozmiar jego śledzenia minimalną i maksymalną.

## <a name="syntax"></a>Składnia

```
typedef struct tagMINMAXINFO {
    POINT ptReserved;
    POINT ptMaxSize;
    POINT ptMaxPosition;
    POINT ptMinTrackSize;
    POINT ptMaxTrackSize;
} MINMAXINFO;
```

#### <a name="parameters"></a>Parametry

*ptReserved*<br/>
Zarezerwowane do użytku wewnętrznego.

*ptMaxSize*<br/>
Określa maksymalną szerokość (point.x) i w trybie zmaksymalizowanym wysokość (point.y) okna.

*ptMaxPosition*<br/>
Określa położenie po lewej stronie zmaksymalizowane okno (point.x) oraz pozycji w górnej części zmaksymalizowane okno (point.y).

*ptMinTrackSize*<br/>
Określa co najmniej śledzenia szerokość (point.x) i minimalna wysokość (point.y) okna śledzenia.

*ptMaxTrackSize*<br/>
Określa maksymalną szerokość (point.x) śledzenia i maksymalną wysokość (point.y) okna śledzenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

