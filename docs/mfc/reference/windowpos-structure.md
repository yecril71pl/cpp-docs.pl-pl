---
title: Struktura WINDOWPOS
ms.date: 11/04/2016
f1_keywords:
- WINDOWPOS
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
ms.openlocfilehash: 16d9122a4141d2516118304fcdb4dd1b8fc14421
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439432"
---
# <a name="windowpos-structure"></a>Struktura WINDOWPOS

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

*hwnd*<br/>
Identyfikuje okna.

*hwndInsertAfter*<br/>
Identyfikuje okna za zaporą, która znajduje się w tym oknie.

*x*<br/>
Określa położenie lewej krawędzi okna.

*y*<br/>
Określa położenie prawej krawędzi okna.

*CX*<br/>
Określa szerokość okna w pikselach.

*CY*<br/>
Określa wysokość okna w pikselach.

*flagi*<br/>
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

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)
