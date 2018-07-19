---
title: Struktura1 WINDOWPOS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db51e8f9924d69406989b3a9ac12b45f0e55e870
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885965"
---
# <a name="windowpos-structure1"></a>Struktura1 WINDOWPOS
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
 *hwnd*  
 Identyfikuje okna.  
  
 *hwndInsertAfter*  
 Identyfikuje okna za zaporą, która znajduje się w tym oknie.  
  
 *x*  
 Określa położenie lewej krawędzi okna.  
  
 *y*  
 Określa położenie prawej krawędzi okna.  
  
 *CX*  
 Określa szerokość okna w pikselach.  
  
 *CY*  
 Określa wysokość okna w pikselach.  
  
 *flagi*  
 Określa opcje położenia okna. Ten element członkowski może być jednym z następujących wartości:  
  
- Rysuje SWP_DRAWFRAME a (zdefiniowane w opisie klasy okna) wokół ramkę okna. Okno odbiera komunikat WM_NCCALCSIZE.  
  
- Wysyła SWP_FRAMECHANGED WM_NCCALCSIZE komunikatu o do okna, nawet jeśli nie są zmieniane rozmiaru okna. Jeśli ta flaga nie zostanie określony, WM_NCCALCSIZE są wysyłane tylko wtedy, gdy zmianie rozmiaru okna.  
  
- SWP_HIDEWINDOW ukrywa okno.  
  
- SWP_NOACTIVATE nie uaktywnia okna.  
  
- SWP_NOCOPYBITS odrzuca całą zawartość obszaru klienta. Jeśli ta flaga nie zostanie określony, Nieprawidłowa zawartość obszaru klienckiego zapisywania i skopiowanych wróć do obszaru klienckiego okna jest rozmiar lub położenie.  
  
- Zachowuje SWP_NOMOVE bieżącego położenia (ignoruje `x` i `y` elementów członkowskich).  
  
- SWP_NOOWNERZORDER nie zmienia położenie okna właściciela w porządku osi Z.  
  
- SWP_NOSIZE zachowuje bieżący rozmiar (ignoruje `cx` i `cy` elementów członkowskich).  
  
- SWP_NOREDRAW nie są odświeżane zmiany.  
  
- SWP_NOREPOSITION taki sam jak SWP_NOOWNERZORDER.  
  
- SWP_NOSENDCHANGING uniemożliwia odbieranie wiadomości WM_WINDOWPOSCHANGING okna.  
  
- SWP_NOZORDER zachowuje kolejności bieżącego (ignoruje `hwndInsertAfter` element członkowski).  
  
- SWP_SHOWWINDOW Wyświetla okno.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

