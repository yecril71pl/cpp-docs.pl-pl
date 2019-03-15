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
ms.openlocfilehash: 46da8fc0cb98406bdf97285d7c6f824afd61c4bb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808355"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Klasy okien ramowych tworzone przez kreatora aplikacji

Gdy projekt do tworzenia nowych MFC z **nowy projekt** okno dialogowe, oprócz aplikacji, klasy dokumentów i widoków, Kreator aplikacji tworzy klasy pochodnej okno ramowe aplikacji głównej ramki okna. Nosi nazwę klasy `CMainFrame` domyślnie i pliki go zawierające są nazywane MAINFRM. H i MAINFRM. CPP.

Jeśli aplikacja jest SDI, Twoje `CMainFrame` klasa pochodzi od klasy [CFrameWnd](../mfc/reference/cframewnd-class.md).

Jeśli aplikacja MDI, `CMainFrame` pochodzi od klasy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). W tym przypadku `CMainFrame` implementuje głównej ramki, który przechowuje paski menu, pasek narzędzi i stanu. Kreator aplikacji nie jest pochodny nowej klasy okien ramowych dokumentu dla Ciebie. Zamiast tego używa implementacji domyślnej w [klasa CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). Struktura MFC tworzy okno podrzędne zawierają każdego widoku (które mogą być typu `CScrollView`, `CEditView`, `CTreeView`, `CListView`i tak dalej), aplikacja wymaga. Jeśli trzeba dostosować okna ramki dokumentu, można utworzyć nowej klasy okien ramowych dokumentu (zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)).

Jeśli zdecydujesz się obsługiwać paska narzędzi, klasa ma również zmiennych składowych typu [CToolBar](../mfc/reference/ctoolbar-class.md) i [CStatusBar](../mfc/reference/cstatusbar-class.md) i `OnCreate` funkcji obsługi wiadomości, aby zainicjować dwa [ paski sterowania](../mfc/control-bars.md).

Te klasy okien ramowych działają podczas tworzenia, ale aby zwiększyć ich funkcji, należy dodać zmienne Członkowskie i funkcje Członkowskie. Można również mieć swojej klasy okna obsługi innych komunikatów Windows. Aby uzyskać więcej informacji, zobacz [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Zobacz także

[Klasy okien ramowych](../mfc/frame-window-classes.md)<br/>
[Program MFC lub źródło kontroli i pliki nagłówkowe](../build/reference/mfc-program-or-control-source-and-header-files.md)

