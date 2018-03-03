---
title: "Zmienianie stylów okna utworzonego przez MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d17f49535078261669841ea502c6af821aa5e29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Zmienianie stylów okna utworzonego przez MFC
W wersji z `WinMain` funkcji MFC rejestruje kilka klas standardowego okna. Ponieważ nie normalnie edytować MFC `WinMain`, że funkcja daje możliwość zmienić domyślne style okien MFC. W tym artykule opisano, jak zmienić style taka klasa preregistered okna w istniejącej aplikacji.  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a>Zmienianie stylów w nowej aplikacji MFC  
 Jeśli używasz programu Visual C++ w wersji 2.0 lub nowszej, można zmienić domyślne style okna w Kreatorze aplikacji, podczas tworzenia aplikacji. Na stronie funkcje interfejsu użytkownika Kreatora aplikacji można zmienić style dla głównego okna ramowego i okien podrzędnych MDI. Dla dowolnego typu oknie można określić grubość ramki (grubość lub cienkich) i dowolne z następujących czynności:  
  
-   Określa, czy okno ma Minimalizuj lub Maksymalizuj formantów.  
  
-   Określa, czy okno początkowo zminimalizowane zmaksymalizowane, albo nie.  
  
 Dla ramki głównej systemu windows można również określić, czy okno ma Menu systemowego. Dla okien podrzędnych MDI można określić, czy okno obsługuje podziału okienka.  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a>Zmienianie stylów w istniejącej aplikacji  
 Jeśli chcesz zmienić atrybutów okna w istniejącej aplikacji, postępuj zgodnie z instrukcjami wyświetlanymi w dalszej części tego artykułu.  
  
 Aby zmienić domyślne atrybuty okna używany przez aplikację framework utworzonych za pomocą Kreatora aplikacji, należy zastąpić okna [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) wirtualnej funkcji członkowskiej. `PreCreateWindow`umożliwia aplikacji dostęp do procesu tworzenia zwykle zarządzane wewnętrznie przy [cdoctemplate —](../mfc/reference/cdoctemplate-class.md) klasy. Wywołania framework `PreCreateWindow` wcześniejszy niż Tworzenie okna. Zmieniając [CREATESTRUCT](../mfc/reference/createstruct-structure.md) struktury przekazany do `PreCreateWindow`, aplikacji, można zmienić atrybutów, używany do tworzenia okna. Na przykład aby upewnić się, czy okno nie używa podpis, użyj następujących operacji:  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../visual-cpp-samples.md) aplikacja przykładowa prezentuje ta technika Zmienianie atrybutów okna. W zależności od tego, jakie zmiany w aplikacji `PreCreateWindow`, może być konieczne do wywołania implementacji klasy podstawowej funkcji.  
  
 W przypadku SDI obejmuje następujące dyskusji i [przypadku MDI](#_core_the_mdi_case).  
  
##  <a name="_core_the_sdi_case"></a>W przypadku SDI  
 W aplikacji pojedynczego dokumentu (SDI) interfejsu domyślny styl okna w ramach jest kombinacją **ws_overlappedwindow —** i **fws_addtotitle —** style. **Fws_addtotitle —** jest styl specyficzne dla MFC, która sprawia, że platformę, by dodać tytuł dokumentu do tytuł okna. Aby zmienić atrybuty okna w aplikacji SDI, Przesłoń `PreCreateWindow` funkcji w klasie pochodnej z `CFrameWnd` (który nazwy aplikacji, Kreator `CMainFrame`). Na przykład:  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 Ten kod tworzy główne okno ramowe nie przyciski i nie może być zmieniany obramowanie. Okno początkowo skupia się na ekranie.  
  
##  <a name="_core_the_mdi_case"></a>W przypadku MDI  
 Zmień styl okna okna podrzędnego w wiele aplikacji interfejsu (MDI) dokumentu jest wymaga nieco więcej pracy. Domyślnie aplikacje MDI utworzone przy użyciu Kreatora aplikacji używa domyślnej [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) klas zdefiniowanych w MFC. Aby zmienić styl okna podrzędnego okna MDI, musi pochodzić z nową klasę `CMDIChildWnd` i Zastąp wszystkie odwołania do `CMDIChildWnd` w projekcie z odwołaniami do nowej klasy. Prawdopodobnie tylko odwołanie do `CMDIChildWnd` w aplikacji znajduje się w aplikacji `InitInstance` funkcję elementu członkowskiego.  
  
 Domyślny styl okna używane w aplikacji MDI jest kombinacją **ws_child —**, **ws_overlappedwindow —**, i **fws_addtotitle —** style. Aby zmienić atrybuty okna okien podrzędnych MDI aplikacji, należy zastąpić [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) funkcji w klasie pochodnej z `CMDIChildWnd`. Na przykład:  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 Ten kod tworzy formularz podrzędny MDI okna bez przycisk Maksymalizuj.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Style systemu Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
-   [Style okna ramowego](../mfc/frame-window-styles-cpp.md)  
  
-   [Style okna](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## <a name="see-also"></a>Zobacz też  
 [Style okna ramowego](../mfc/frame-window-styles-cpp.md)

