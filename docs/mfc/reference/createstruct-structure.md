---
title: Struktura CREATESTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594f71d5166261dbb1bb08422a564157bfce2721
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203664"
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
 *lpCreateParams*  
 Punkty danych, które ma być używany do tworzenia okna.  
  
 *hInstance*  
 Identyfikuje dojście wystąpienia modułu modułu, który jest właścicielem w nowym oknie.  
  
 *hMenu*  
 Określa menu, który będzie używany przez nowe okno. Jeśli okno podrzędne zawiera liczby całkowitej.  
  
 *hwndParent*  
 Identyfikuje okna, który jest właścicielem w nowym oknie. Ten element członkowski ma wartość NULL, jeśli nowe okno jest oknem najwyższego poziomu.  
  
 *CY*  
 Określa wysokość w nowym oknie.  
  
 *CX*  
 Określa szerokość w nowym oknie.  
  
 *y*  
 Określa współrzędną y lewego górnego rogu nowe okno. Współrzędne są względem okna nadrzędnego, jeśli nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 *x*  
 Określa współrzędną x lewym górnym rogu w nowym oknie. Współrzędne są względem okna nadrzędnego, jeśli nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 *Styl*  
 Określa nowe okno [styl](../../mfc/reference/styles-used-by-mfc.md).  
  
 *lpszName*  
 Wskazuje ciąg zakończony znakiem null, który określa nazwę nowego okna.  
  
 *lpszClass*  
 Wskazuje ciąg zakończony znakiem null, określający nazwę klasy Windows nowe okno ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Aby uzyskać więcej informacji, zobacz zestaw Windows SDK).  
  
 *dwExStyle*  
 Określa [rozszerzone style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) dla nowego okna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


