---
title: Struktura CREATESTRUCT
ms.date: 11/04/2016
f1_keywords:
- CREATESTRUCT
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
ms.openlocfilehash: 13f715dc914ccc052945790aeaff9c47bd34ed46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619651"
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
Wskazuje ciąg zakończony znakiem null, określający nazwę klasy Windows nowe okno ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury; Aby uzyskać więcej informacji, zobacz zestaw Windows SDK).

*dwExStyle*<br/>
Określa [rozszerzone style](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) dla nowego okna.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

