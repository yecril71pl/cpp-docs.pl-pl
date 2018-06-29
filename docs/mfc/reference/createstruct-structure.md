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
ms.openlocfilehash: b7bc510f0d0cfc88476c9e222f51bcfeb958e31a
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078470"
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
 Punkty danych ma być używany do tworzenia okna.  
  
 *hInstance*  
 Identyfikuje dojście wystąpienia modułu moduł, który jest właścicielem nowe okno.  
  
 *hMenu*  
 Identyfikuje menu, które mają być używane przez nowe okno. Jeśli okno podrzędne, zawiera liczby całkowitej.  
  
 *hwndParent*  
 Określa okno, który jest właścicielem nowe okno. Ten element członkowski jest **NULL** Jeśli nowe okno jest oknem najwyższego poziomu.  
  
 *CY*  
 Określa wysokość w nowym oknie.  
  
 *CX*  
 Określa szerokość nowe okno.  
  
 *y*  
 Określa współrzędną y lewego górnego rogu nowe okno. Współrzędne są względem okno nadrzędne, czy nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 *x*  
 Określa współrzędną x lewym górnym rogu nowe okno. Współrzędne są względem okno nadrzędne, czy nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.  
  
 *Styl*  
 Określa nowe okno [styl](../../mfc/reference/styles-used-by-mfc.md).  
  
 *lpszName*  
 Wskazuje zerem ciąg określający nazwę nowego okna.  
  
 *lpszClass*  
 Wskazuje zerem ciąg, który określa nazwę klasy nowe okno systemu Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Aby uzyskać więcej informacji, zobacz zestaw Windows SDK).  
  
 *dwExStyle*  
 Określa [rozszerzone style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) dla nowego okna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


