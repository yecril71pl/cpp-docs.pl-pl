---
title: Klasy okien ramowych tworzone przez Kreatora aplikacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CMainFrame
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 497dd21bba3e807349b793e3b37e774c833ccb40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Klasy okien ramowych tworzone przez kreatora aplikacji
Jeśli używasz [Kreatora aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md) utworzyć szkielet aplikacji, oprócz aplikacji, klasy dokumentów i widoków, Kreator aplikacji tworzy klasy pochodnej okno ramowe dla okna w ramce głównej aplikacji. Klasa jest nazywany `CMainFrame` domyślnie i pliki go zawierające są nazywane MAINFRM. H i MAINFRM. CPP.  
  
 Jeśli aplikacja jest SDI, Twoje `CMainFrame` klasa pochodzi od klasy [cframewnd —](../mfc/reference/cframewnd-class.md).  
  
 Jeśli aplikacja jest MDI, `CMainFrame` pochodzi od klasy [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md). W takim przypadku `CMainFrame` implementuje ramce głównej przechowuje paski menu, paska narzędzi i stanu. Kreator aplikacji nie pochodzi nowej klasy okien ramowych dokumentu dla Ciebie. Zamiast tego używa domyślną implementację w [cmdichildwnd — klasa](../mfc/reference/cmdichildwnd-class.md). Struktura MFC tworzy okno podrzędne zawierają każdego widoku (które mogą być typu `CScrollView`, `CEditView`, `CTreeView`, `CListView`i tak dalej) przez aplikację. Jeśli potrzebujesz Dostosowywanie okna ramowe dokumentów, można utworzyć nowej klasy okien ramowych dokumentu (zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)).  
  
 Jeśli wybierzesz do obsługi narzędzi, klasa również ma zmiennych członkowskich typu [ctoolbar —](../mfc/reference/ctoolbar-class.md) i [cstatusbar —](../mfc/reference/cstatusbar-class.md) i `OnCreate` funkcji obsługi wiadomości, aby zainicjować dwa [ paski sterowania](../mfc/control-bars.md).  
  
 Te klasy okien ramowych działa jako utworzone, ale w celu zwiększenia ich funkcji, należy dodać zmiennych Członkowskich i funkcji elementów członkowskich. Można również mieć klas okna obsługi innych komunikatów systemu Windows. Aby uzyskać więcej informacji, zobacz [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien ramowych](../mfc/frame-window-classes.md)   
 [Program MFC lub źródło kontroli i pliki nagłówkowe](../ide/mfc-program-or-control-source-and-header-files.md)

