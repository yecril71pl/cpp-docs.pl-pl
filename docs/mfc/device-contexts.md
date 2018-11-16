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
ms.openlocfilehash: 105e438a9ed3e8f7de7edc813fec516c0e99700a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694689"
---
# <a name="device-contexts"></a>Konteksty urządzenia

Kontekst urządzenia jest strukturą danych Windows, zawierający informacje o atrybuty rysowania urządzenia, np. wyświetlania lub drukarki. Wszystkie wywołania rysowania są nawiązywane przy użyciu obiektu kontekstu urządzenia, który hermetyzuje interfejsy API Windows rysowania linii, kształty i tekst. Konteksty urządzenia umożliwiają rysowanie niezależne od urządzenia w Windows. Konteksty urządzenia może służyć do rysowania ekranu, drukarki lub metaplik.

[CPaintDC](../mfc/reference/cpaintdc-class.md) obiektów hermetyzacji wspólnych idiom systemu Windows, wywołanie `BeginPaint` funkcji rysowania w kontekście urządzenia, a następnie wywoływania `EndPaint` funkcji. `CPaintDC` Konstruktor wywołuje `BeginPaint` dla Ciebie i wywołania destruktora `EndPaint`. Uproszczony proces jest utworzenie [CDC](../mfc/reference/cdc-class.md) obiektu, rysowania, a następnie zniszcz `CDC` obiektu. W ramach większość nawet ten proces jest zautomatyzowany. W szczególności usługi `OnDraw` funkcji jest przekazywany `CPaintDC` już przygotowane (za pośrednictwem `OnPrepareDC`), a po prostu narysuj tę sytuację. Jest niszczony przez platformę i udostępnieniem podstawowy kontekst urządzenia Windows po powrocie z wywołania sieci `OnDraw` funkcji.

[Cclientdc —](../mfc/reference/cclientdc-class.md) obiekty hermetyzują pracę z kontekstu urządzenia, który reprezentuje tylko obszaru klienckiego okna. `CClientDC` Konstruktor wywołuje `GetDC` funkcji i wywołania destruktora `ReleaseDC` funkcji. [CWindowDC](../mfc/reference/cwindowdc-class.md) obiekty hermetyzują kontekst urządzenia, który reprezentuje całego okna, w tym jego ramki.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md) obiekty hermetyzują rysowania w metaplik Windows. W przeciwieństwie do `CPaintDC` przekazany do `OnDraw`, w tym przypadku należy wywołać [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) samodzielnie.

## <a name="mouse-drawing"></a>Rysowanie myszy

Większość Rysowanie w ramach programu — i dlatego większość pracy kontekstu urządzenia — odbywa się w widoku `OnDraw` funkcja elementu członkowskiego. Można jednak nadal używać obiektów kontekstu urządzenia do innych celów. Na przykład, aby przekazać opinię śledzenia dla ruchów myszy w widoku, należy narysować bezpośrednio w widoku bez oczekiwania na `OnDraw` do wywołania.

W takim przypadku można użyć [cclientdc —](../mfc/reference/cclientdc-class.md) obiekt kontekstu urządzenia, aby narysować bezpośrednio w widoku.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Konteksty urządzenia (definicja)](/windows/desktop/gdi/device-contexts)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

- [Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku](../mfc/interpreting-user-input-through-a-view.md)

- [Linii i krzywych](/windows/desktop/gdi/lines-and-curves)

- [Wypełnione kształty](/windows/desktop/gdi/filled-shapes)

- [Czcionki i tekst](/windows/desktop/gdi/fonts-and-text)

- [Kolory](/windows/desktop/gdi/colors)

- [Współrzędnych miejsca do magazynowania i przekształcenia](/windows/desktop/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

