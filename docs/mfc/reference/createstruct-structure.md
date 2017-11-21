---
title: Struktura CREATESTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CREATESTRUCT
dev_langs: C++
helpviewer_keywords: CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67f04b70b47e980455c73550e56d92f4433ee31c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="createstruct-structure"></a>Struktura CREATESTRUCT
`CREATESTRUCT` Struktury definiuje parametry inicjacji przekazany do procedury okna aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpCreateParams`  
 Punkty danych ma być używany do tworzenia okna.  
  
 `hInstance`  
 Identyfikuje dojście wystąpienia modułu moduł, który jest właścicielem nowe okno.  
  
 `hMenu`  
 Identyfikuje menu, które mają być używane przez nowe okno. Jeśli okno podrzędne, zawiera liczby całkowitej.  
  
 `hwndParent`  
 Określa okno, który jest właścicielem nowe okno. Ten element członkowski jest **NULL** Jeśli nowe okno jest oknem najwyższego poziomu.  
  
 `cy`  
 Określa wysokość w nowym oknie.  
  
 `cx`  
 Określa szerokość nowe okno.  
  
 `y`  
 Określa współrzędną y lewego górnego rogu nowe okno. Współrzędne są względem okno nadrzędne, czy nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 `x`  
 Określa współrzędną x lewym górnym rogu nowe okno. Współrzędne są względem okno nadrzędne, czy nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 `style`  
 Określa nowe okno [styl](../../mfc/reference/styles-used-by-mfc.md).  
  
 `lpszName`  
 Wskazuje zerem ciąg określający nazwę nowego okna.  
  
 `lpszClass`  
 Wskazuje zerem ciąg, który określa nazwę klasy nowe okno systemu Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Aby uzyskać więcej informacji, zobacz zestaw Windows SDK).  
  
 `dwExStyle`  
 Określa [rozszerzone style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) dla nowego okna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


