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
ms.openlocfilehash: cf9a6e6a1397b9361df5372af09be8e61d997e62
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337817"
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
 *ptReserved*  
 Zarezerwowane do użytku wewnętrznego.  
  
 *ptMaxSize*  
 Określa maksymalną szerokość (point.x) i w trybie zmaksymalizowanym wysokość (point.y) okna.  
  
 *ptMaxPosition*  
 Określa położenie po lewej stronie zmaksymalizowane okno (point.x) oraz pozycji w górnej części zmaksymalizowane okno (point.y).  
  
 *ptMinTrackSize*  
 Określa co najmniej śledzenia szerokość (point.x) i minimalna wysokość (point.y) okna śledzenia.  
  
 *ptMaxTrackSize*  
 Określa maksymalną szerokość (point.x) śledzenia i maksymalną wysokość (point.y) okna śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

