---
title: Struktura CREATESTRUCT
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 1de42ba3e26f7a06918a69358083e68f142836cc
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694702"
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

*lpCreateParams*<br/>
Punkty danych, które ma być używany do tworzenia okna.

*hInstance*<br/>
Identyfikuje dojście wystąpienia modułu modułu, który jest właścicielem w nowym oknie.

*hMenu*<br/>
Określa menu, który będzie używany przez nowe okno. Jeśli okno podrzędne zawiera liczby całkowitej.

*hwndParent*<br/>
Identyfikuje okna, który jest właścicielem w nowym oknie. Ten element członkowski ma wartość NULL, jeśli nowe okno jest oknem najwyższego poziomu.

*CY*<br/>
Określa wysokość w nowym oknie.

*CX*<br/>
Określa szerokość w nowym oknie.

*y*<br/>
Określa współrzędną y lewego górnego rogu nowe okno. Współrzędne są względem okna nadrzędnego, jeśli nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.

*x*<br/>
Określa współrzędną x lewym górnym rogu w nowym oknie. Współrzędne są względem okna nadrzędnego, jeśli nowe okno jest oknem podrzędnym; w przeciwnym razie współrzędne są podawane pokrewny ze źródłem ekranu.

*Styl*<br/>
Określa nowe okno [styl](../../mfc/reference/styles-used-by-mfc.md).

*lpszName*<br/>
Wskazuje ciąg zakończony znakiem null, który określa nazwę nowego okna.

*lpszClass*<br/>
Wskazuje ciąg zakończony znakiem null, określający nazwę klasy Windows nowe okno ( [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) struktury; Aby uzyskać więcej informacji, zobacz zestaw Windows SDK).

*dwExStyle*<br/>
Określa [rozszerzone style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) dla nowego okna.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

