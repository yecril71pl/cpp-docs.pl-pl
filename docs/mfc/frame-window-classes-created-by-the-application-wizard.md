---
title: Klasy okien ramowych tworzone przez kreatora aplikacji
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: 00254bdf49015f26ac257789a15afd1e7f5cc31f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621706"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Klasy okien ramowych tworzone przez kreatora aplikacji

W przypadku tworzenia nowego projektu MFC z okna dialogowego **Nowy projekt** , oprócz klas aplikacji, dokumentów i widoków, Kreator aplikacji tworzy pochodną klasę okna ramki dla głównego okna ramki aplikacji. Klasa jest wywoływana `CMainFrame` Domyślnie, a pliki, które zawierają, mają nazwę MainFrm. H i MAINFRM. CPP.

Jeśli aplikacja jest SDI, Klasa pochodzi `CMainFrame` od klasy [obiektu CFrameWnd](reference/cframewnd-class.md).

Jeśli aplikacja jest MDI, pochodzi `CMainFrame` od klasy [CMDIFrameWnd](reference/cmdiframewnd-class.md). W tym przypadku `CMainFrame` implementuje ramkę główną, która zawiera menu, pasek narzędzi i paski stanu. Kreator aplikacji nie tworzy nowej klasy okna ramki dokumentu. Zamiast tego używa domyślnej implementacji w [klasie CMDIChildWnd](reference/cmdichildwnd-class.md). Struktura MFC tworzy okno podrzędne, aby zawierało każdy widok (który może być typu `CScrollView` , `CEditView` ,, `CTreeView` `CListView` i tak dalej), którego wymaga aplikacja. Jeśli musisz dostosować okno ramki dokumentu, możesz utworzyć nową klasę okna ramki dokumentu (zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)).

Jeśli zdecydujesz się na obsługę paska narzędzi, Klasa zawiera również zmienne członkowskie typu [CToolBar](reference/ctoolbar-class.md) i [CStatusBar](reference/cstatusbar-class.md) oraz `OnCreate` funkcję obsługi komunikatów, aby zainicjować dwa [paski sterowania](control-bars.md).

Te klasy okien ramowych działają jak utworzone, ale w celu zwiększenia ich funkcjonalności należy dodać zmienne składowe i funkcje członkowskie. Może być również konieczne, aby klasy okien obsługiwały inne komunikaty systemu Windows. Aby uzyskać więcej informacji, zobacz [Zmiana stylów okna utworzonego przez MFC](changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasy okien ramowych](frame-window-classes.md)<br/>
[Program MFC lub źródło kontroli i pliki nagłówkowe](../build/reference/mfc-program-or-control-source-and-header-files.md)
