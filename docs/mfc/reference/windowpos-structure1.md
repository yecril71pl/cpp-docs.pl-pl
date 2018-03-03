---
title: WINDOWPOS Structure1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7db3991a6767e33c73857daf40a977ac5f6f0b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windowpos-structure1"></a>WINDOWPOS Structure1
`WINDOWPOS` Struktura zawiera informacje o rozmiar i położenie okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>Parametry  
 *Właściwość hwnd*  
 Identyfikuje okna.  
  
 *hwndInsertAfter*  
 Identyfikuje okna, pod którym znajduje się tego okna.  
  
 *x*  
 Określa pozycję od lewej krawędzi okna.  
  
 *y*  
 Określa położenie prawej krawędzi okna.  
  
 `cx`  
 Określa szerokość okna w pikselach.  
  
 `cy`  
 Określa wysokość okna w pikselach.  
  
 `flags`  
 Określa położenie okna Opcje. Ten element członkowski może być jedną z następujących wartości:  
  
- **SWP_DRAWFRAME** ramki (zdefiniowany w opisie klasy okna) jest rysowane wokół okna. Odbiera okna `WM_NCCALCSIZE` wiadomości.  
  
- **SWP_FRAMECHANGED** wysyła `WM_NCCALCSIZE` wiadomości do okna, nawet jeśli nie są zmieniane rozmiaru okna. Jeśli ta flaga nie zostanie określony, `WM_NCCALCSIZE` jest wysyłana tylko wtedy, gdy trwa modyfikowanie rozmiaru okna.  
  
- **SWP_HIDEWINDOW** ukrywa okno.  
  
- `SWP_NOACTIVATE`Nie aktywować okna.  
  
- **SWP_NOCOPYBITS** odrzuca całą zawartość obszaru klienckiego. Jeśli ta flaga nie zostanie określony, Nieprawidłowa zawartość obszaru klienckiego są zapisywane i kopiowane do obszaru klienckiego po okna jest rozmiaru lub położenia.  
  
- `SWP_NOMOVE`Zachowuje bieżące położenie (ignoruje **x** i **y** elementów członkowskich).  
  
- **SWP_NOOWNERZORDER** nie zmienia położenie okno właściciela w porządku osi Z.  
  
- `SWP_NOSIZE`Zachowuje bieżący rozmiar (ignoruje **cx** i **cy** elementów członkowskich).  
  
- **SWP_NOREDRAW** zmiany nie są odświeżane.  
  
- **SWP_NOREPOSITION** taki sam jak **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** uniemożliwia odbieranie okna `WM_WINDOWPOSCHANGING` wiadomości.  
  
- `SWP_NOZORDER`Zachowuje bieżący porządkowanie (ignoruje **hwndInsertAfter** element członkowski).  
  
- **SWP_SHOWWINDOW** Wyświetla okna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

