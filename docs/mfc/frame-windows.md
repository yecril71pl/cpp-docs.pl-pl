---
title: Okna ramowe
ms.date: 11/19/2018
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 39c0b4b866fa123d8bcae639342c925570d96e1b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625821"
---
# <a name="frame-windows"></a>Okna ramowe

Gdy aplikacja działa w systemie Windows, użytkownik współdziała z dokumentami wyświetlanymi w oknach ramowych. Okno ramki dokumentu ma dwa główne składniki: ramkę i zawartość, którą zawiera ramka. Okno ramki dokumentu może być oknem ramki [interfejsu pojedynczego dokumentu](sdi-and-mdi.md) (SDI) lub oknem podrzędnym [wielu dokumentów](sdi-and-mdi.md) (MDI). System Windows zarządza większością interakcji użytkownika z oknem ramki: przeniesienie i zmiana rozmiarów okna, jego zamknięcie i zminimalizowanie i zmaksymalizowanie. Zawartość wewnątrz ramki jest zarządzana.

## <a name="frame-windows-and-views"></a>Okna ramowe i widoki

Struktura MFC używa okien ramowych do znajdowania widoków. Dwa składniki — Frame i Contents — są reprezentowane i zarządzane przez dwie różne klasy w MFC. Klasa okien ramowych zarządza ramką, a Klasa widoku zarządza zawartością. Okno widok jest elementem podrzędnym okna ramki. Rysowanie i inne interakcje użytkownika z dokumentem odbywają się w obszarze klienta widoku, a nie w obszarze klienta okna ramki. Okno ramki zawiera widoczną ramkę dookoła widoku, kompletną z paskiem podpisu i formantami okna standardowego, takimi jak menu kontrolki, przyciski umożliwiające minimalizowanie i Maksymalizowanie okna oraz kontrolki zmiany rozmiarów okna. "Zawartość" składa się z obszaru klienta okna, który jest w pełni zajęty oknem podrzędnym — widok. Poniższy rysunek przedstawia relację między oknem ramki a widokiem.

![Widok okna ramowego](../mfc/media/vc37fx1.gif "Widok okna ramowego") <br/>
Okno i widok ramki

## <a name="frame-windows-and-splitter-windows"></a>Okna ramowe i okna rozdzielacza

Innym typowym rozmieszczeniem jest to, aby okno ramki było ramką wielu widoków, zwykle przy użyciu [okna rozdzielacza](multiple-document-types-views-and-frame-windows.md). W oknie rozdzielacza obszar klienta okna ramki jest zajmowany przez okno rozdzielacza, które z kolei ma wiele okien podrzędnych o nazwie okienka, które są widokami.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

**Ogólne tematy dotyczące okien ramowych**

- [Obiekty okna](window-objects.md)

- [Klasy okien ramowych](frame-window-classes.md)

- [Klasy okien ramowych tworzone przez Kreatora aplikacji](frame-window-classes-created-by-the-application-wizard.md)

- [Style okna ramowego](frame-window-styles-cpp.md)

- [Co robią okna ramowe](what-frame-windows-do.md)

**Tematy dotyczące korzystania z okien ramowych**

- [Korzystanie z okien ramowych](using-frame-windows.md)

- [Tworzenie okien ramowych dokumentu](creating-document-frame-windows.md)

- [Niszczenie okien ramowych](destroying-frame-windows.md)

- [Zarządzanie oknami podrzędnymi MDI](managing-mdi-child-windows.md)

- [Zarządzanie bieżącym widokiem](managing-the-current-view.md) w oknie ramki zawierającym więcej niż jeden widok

- [Zarządzanie menu, paskami sterowania i akceleratorami (inne obiekty, które współdzielą przestrzeń okna ramki)](managing-menus-control-bars-and-accelerators.md)

**Tematy dotyczące funkcji okna ramki specjalnej**

- [Przeciąganie i upuszczanie plików](dragging-and-dropping-files-in-a-frame-window.md) z Eksploratora plików lub Menedżera plików do okna ramowego

- [Reagowanie na dynamiczną wymianę danych (DDE)](responding-to-dynamic-data-exchange-dde.md)

- [Stany półmodalne: kontekstowa Pomoc systemu Windows (organizowanie innych akcji okna)](orchestrating-other-window-actions.md)

- [Stany półmodalne: drukowanie i Podgląd wydruku (organizowanie innych akcji okna)](orchestrating-other-window-actions.md)

**Tematy dotyczące innych rodzajów okien**

- [Używanie widoków](using-views.md)

- [Okna dialogowe](dialog-boxes.md)

- [Formanty](controls-mfc.md)

## <a name="see-also"></a>Zobacz też

[Windows](windows.md)
