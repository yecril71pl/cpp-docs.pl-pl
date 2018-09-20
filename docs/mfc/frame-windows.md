---
title: Ramki Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77035b50070478f5117635738f13c7bfd43edec2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431024"
---
# <a name="frame-windows"></a>Okna ramowe

Po uruchomieniu aplikacji w obszarze Windows, użytkownik wchodzi w interakcję z wyświetlana w oknach ramowych dokumentów. Okna ramki dokumentu ma dwa główne składniki: ramki i zawartość, która go ramek. Okna ramki dokumentu może być [interfejsu pojedynczego dokumentu](../mfc/sdi-and-mdi.md) okno ramowe (SDI) lub [interfejsu wielu dokumentów](../mfc/sdi-and-mdi.md) okna podrzędnego (MDI). Windows zarządza większość interakcji użytkownika z oknem ramki: przenoszenie i zmienia rozmiar okna, zamknięcie, minimalizowanie i jego zmaksymalizowaniu. Możesz zarządzać zawartość wewnątrz ramki.

## <a name="frame-windows-and-views"></a>Windows ramek i widokami

Struktura MFC używa okien ramowych do zawierają widoki. Dwa składniki — ramki i zawartości — są reprezentowane i zarządza dwoma różnymi klasami w MFC. Klasy okien ramowych zarządza ramki, a klasa widoku zarządza zawartość. Okno Widok jest elementem podrzędnym ramki okna. Rysowanie i innych interakcji użytkownika z dokumentem miejsce w obszar klienta tego widoku, nie obszaru klienckiego okna ramki. Okno ramowe zawiera widoczne ramkę wokół widoku, wraz z pasek podpisu i standardowego okna kontrolek, takich jak kontrolki menu, przyciski, aby zminimalizować i zmaksymalizuj okno i kontroluje do zmiany rozmiaru okna. "Zawartość" składają się z obszaru klienckiego okna, w pełni jest zajęta przez okno podrzędne — widok. Na poniższej ilustracji przedstawiono relację między oknem ramki i widokiem.

![Ramka okna widoku](../mfc/media/vc37fx1.gif "vc37fx1") ramki okna i widoku

## <a name="frame-windows-and-splitter-windows"></a>Ramka Windows i Windows rozdzielacza

Inny układ wspólnej dotyczy ramki okna ramki wiele widoków, zwykle za pomocą [okno rozdzielacza](../mfc/multiple-document-types-views-and-frame-windows.md). W oknie rozdzielacza obszaru klienckiego okna ramki jest zajęta przez okna dzielącego, która z kolei ma wiele okien podrzędnych o nazwie okienek, które są widoki.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

**Tematy ogólne, okno ramowe**

- [Obiekty okna](../mfc/window-objects.md)

- [Klasy okien ramowych](../mfc/frame-window-classes.md)

- [Klasy okien ramowych tworzone przez Kreatora aplikacji](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Style okna ramki](../mfc/frame-window-styles-cpp.md)

- [Co robią okna ramowe](../mfc/what-frame-windows-do.md)

**Tematy dotyczące używania Windows ramki**

- [Używanie okien ramowych](../mfc/using-frame-windows.md)

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

- [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)

- [Zarządzanie oknami podrzędnymi MDI](../mfc/managing-mdi-child-windows.md)

- [Zarządzanie bieżącym widokiem](../mfc/managing-the-current-view.md) w oknie ramki, który zawiera więcej niż jeden widok

- [Zarządzanie menu, paskami sterowania i akceleratorami (inne obiekty, które mają miejsce okno ramek)](../mfc/managing-menus-control-bars-and-accelerators.md)

**Tematy dotyczące możliwości okna ramki specjalne**

- [Przeciąganie i upuszczanie plików](../mfc/dragging-and-dropping-files-in-a-frame-window.md) z Eksploratora plików lub Menedżera plików, w oknie ramowym

- [Odpowiadanie na dynamiczną wymianę danych (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)

- [Stany półmodalne: Windows Context-sensitive Help (organizowanie innych akcji okna)](../mfc/orchestrating-other-window-actions.md)

- [Stany półmodalne: drukowanie i Podgląd wydruku (organizowanie innych akcji okna)](../mfc/orchestrating-other-window-actions.md)

**Tematy dotyczące innych rodzajów Windows**

- [Używanie widoków](../mfc/using-views.md)

- [Okna dialogowe](../mfc/dialog-boxes.md)

- [Kontrolki](../mfc/controls-mfc.md)

## <a name="see-also"></a>Zobacz też

[Windows](../mfc/windows.md)

