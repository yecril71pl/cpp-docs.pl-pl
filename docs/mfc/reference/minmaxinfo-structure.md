---
title: Struktura MINMAXINFO
ms.date: 11/04/2016
f1_keywords:
- MINMAXINFO
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
ms.openlocfilehash: 11f55b1756623626769e21c006543b6993607b08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517848"
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

