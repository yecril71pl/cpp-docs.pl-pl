---
title: Struktura WINDOWPLACEMENT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 829b3c90acb089bd91d71c498df5906fff919f22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379476"
---
# <a name="windowplacement-structure"></a>Struktura WINDOWPLACEMENT
`WINDOWPLACEMENT` Struktury zawiera informacje dotyczące rozmieszczenia okna na ekranie **.**  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
    UINT length;  
    UINT flags;  
    UINT showCmd;  
    POINT ptMinPosition;  
    POINT ptMaxPosition;  
    RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *długość*  
 Określa długość w bajtach struktury **.**  
  
 `flags`  
 Określa flagi sterujące pozycji zminimalizowanego okna i metody, za pomocą którego jest przywracany okna. Ten element członkowski może być co najmniej jednej z następujących flag:  
  
- **WPF_SETMINPOSITION** Określa, czy można określić pozycji x i y zminimalizowanego okna **.** Ta flaga musi być określona, jeśli współrzędne są ustawiane w **ptMinPosition** elementu członkowskiego.  
  
- **WPF_RESTORETOMAXIMIZED** Określa, czy okno przywrócone zostaną zmaksymalizowane, niezależnie od tego, czy został zmaksymalizowany przed jego zostało zminimalizowane. To ustawienie jest prawidłowa tylko gdy okno jest przywrócone. Nie zmienia domyślne zachowanie przywracania. Ta flaga jest prawidłowe tylko w przypadku **SW_SHOWMINIMIZED** określono wartość dla **showCmd** elementu członkowskiego.  
  
 *showCmd*  
 Określa aktualny stan Pokaż okna. Ten element członkowski może być jedną z następujących wartości:  
  
- **SW_HIDE** ukrywa okno i przekazuje aktywacji do innego okna.  
  
- **SW_MINIMIZE** minimalizuje określone okno i aktywuje okno najwyższego poziomu w liście systemu.  
  
- **SW_RESTORE** Activates i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywracania go w jego oryginalny rozmiar i położenie (taki sam jak **SW_SHOWNORMAL**).  
  
- **SW_SHOW** aktywuje okno i wyświetla je w jego bieżący rozmiar i położenie.  
  
- **SW_SHOWMAXIMIZED** aktywuje okno i wyświetla je jako okno zmaksymalizowane.  
  
- **SW_SHOWMINIMIZED** aktywuje okno i wyświetla je w postaci ikony.  
  
- **SW_SHOWMINNOACTIVE** Wyświetla okna w postaci ikony. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNA** Wyświetla okno w bieżącym stanie. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNOACTIVATE** Wyświetla okna w najnowszych rozmiar i położenie. Okno, który jest obecnie aktywny pozostaje aktywna.  
  
- **SW_SHOWNORMAL** Activates i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywracania go w jego oryginalny rozmiar i położenie (taki sam jak **SW_RESTORE**).  
  
 *ptMinPosition*  
 Określa położenie lewego górnego rogu okna, gdy okno jest zminimalizowany.  
  
 `ptMaxPosition`  
 Określa położenie lewego górnego rogu okna, gdy okno jest zmaksymalizowane.  
  
 *rcNormalPosition*  
 Określa współrzędne okna, gdy okno jest w normalnej pozycji (przywróconej).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

