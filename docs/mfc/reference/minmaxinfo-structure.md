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
ms.openlocfilehash: 12161938f96e5044ae48f9eb5cf380fbc3840d3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369521"
---
# <a name="minmaxinfo-structure"></a>Struktura MINMAXINFO
`MINMAXINFO` Struktura zawiera informacje o zmaksymalizowane rozmiaru okna i pozycji i rozmiaru śledzenia minimalną i maksymalną.  
  
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
 Zarezerwowany do użytku wewnętrznego.  
  
 *ptMaxSize*  
 Określa maksymalną szerokość (point.x) i w trybie zmaksymalizowanym wysokość okna (point.y).  
  
 `ptMaxPosition`  
 Określa położenie lewej zmaksymalizowane okno (point.x) i umieść je u góry okna w trybie zmaksymalizowanym (point.y).  
  
 *ptMinTrackSize*  
 Określa minimalną szerokość (point.x) śledzenia i minimalna wysokość (point.y) okna śledzenia.  
  
 *ptMaxTrackSize*  
 Określa maksymalną szerokość (point.x) śledzenia i maksymalną wysokość (point.y) okna śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

