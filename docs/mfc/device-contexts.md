---
title: Konteksty urządzenia
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: d5337e8d8b83a641458a15612803feeec3b6361c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508658"
---
# <a name="device-contexts"></a>Konteksty urządzenia

Kontekst urządzenia to struktura danych systemu Windows zawierająca informacje o atrybutach rysowania urządzenia, takich jak wyświetlacz lub drukarka. Wszystkie wywołania rysowania są wykonywane za pomocą obiektu kontekstu urządzenia, który hermetyzuje interfejsy API systemu Windows do rysowania linii, kształtów i tekstu. Konteksty urządzeń umożliwiają rysowanie niezależne od urządzenia w systemie Windows. Kontekstów urządzenia można używać do rysowania na ekranie, do drukarki lub do metapliku.

Obiekty [CPaintDC](../mfc/reference/cpaintdc-class.md) hermetyzują wspólne idiom systemu Windows, wywołując `BeginPaint` funkcję, rysując w kontekście urządzenia `EndPaint` , a następnie wywołując funkcję. Konstruktor wywołuje `BeginPaint` użytkownika i destruktor wywołuje `EndPaint`. `CPaintDC` Uproszczony proces polega na utworzeniu obiektu [przechwytywania](../mfc/reference/cdc-class.md) zmian, narysowaniu i usunięciu `CDC` obiektu. W tym środowisku wiele nawet tego procesu jest zautomatyzowanych. W szczególności `OnDraw` funkcja jest `CPaintDC` już przygotowana (za pośrednictwem `OnPrepareDC`) i wystarczy do niej narysować. Jest niszczony przez platformę, a kontekst urządzenia podstawowego jest wydawany do systemu Windows po powrocie z `OnDraw` wywołania funkcji.

Obiekty [CClientDC —](../mfc/reference/cclientdc-class.md) hermetyzują pracę z kontekstem urządzenia, który reprezentuje tylko obszar klienta okna. Konstruktor wywołuje funkcję, a destruktor wywołuje `ReleaseDC` funkcję. `GetDC` `CClientDC` Obiekty [CWindowDC](../mfc/reference/cwindowdc-class.md) hermetyzują kontekst urządzenia reprezentujący całe okno, w tym jego ramkę.

Obiekty [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) hermetyzują rysowanie do metapliku systemu Windows. W przeciwieństwie do `CPaintDC` `OnDraw`, należy w tym przypadku wywołać [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) .

## <a name="mouse-drawing"></a>Rysowanie myszą

Większość rysunków w programie struktury — w związku z tym większość pracy w kontekście urządzenia — jest wykonywana w funkcji `OnDraw` składowej widoku. Można jednak nadal używać obiektów kontekstu urządzenia do innych celów. Na przykład aby umożliwić śledzenie informacji o przesunięciu myszy w widoku, należy narysować bezpośrednio w widoku bez oczekiwania `OnDraw` na ich wywołanie.

W takim przypadku można użyć obiektu kontekstu urządzenia [CClientDC —](../mfc/reference/cclientdc-class.md) , aby rysować bezpośrednio w widoku.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Konteksty urządzenia (definicja)](/windows/win32/gdi/device-contexts)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

- [Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku](../mfc/interpreting-user-input-through-a-view.md)

- [Linie i krzywe](/windows/win32/gdi/lines-and-curves)

- [Wypełnione kształty](/windows/win32/gdi/filled-shapes)

- [Czcionki i tekst](/windows/win32/gdi/fonts-and-text)

- [Kolory](/windows/win32/gdi/colors)

- [Przestrzenie i przekształcenia współrzędnych](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Zobacz także

[Obiekty okna](../mfc/window-objects.md)
