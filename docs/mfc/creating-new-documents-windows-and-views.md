---
title: "Tworzenie nowych dokumentów, okien i widoków | Dokumentacja firmy Microsoft"
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
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01837b079ba08ea2961b141549476da11a481a0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-new-documents-windows-and-views"></a>Tworzenie nowych dokumentów, okien i widoków
Poniższe rysunki nadaj Omówienie procesu tworzenia dokumentów, widoków i okien ramowych. Inne artykuły, które skupić się na obiekty uczestniczących udostępniania dodatkowych szczegółów.  
  
 Po zakończeniu tego procesu współpracujących obiektów istnieje i Zapisz wskaźniki do siebie. Poniższe rysunki pokazują sekwencji, w których obiekty są tworzone. Możesz wykonać sekwencję rysunek rysunku.  
  
 ![Sekwencja tworzenia dokumentu](../mfc/media/vc387l1.gif "vc387l1")  
Sekwencja przy tworzeniu dokumentu  
  
 ![Sekwencja tworzenia okna ramowe](../mfc/media/vc387l2.png "vc387l2")  
Sekwencja tworzenia okna ramowe  
  
 ![Sekwencja tworzenia widoku](../mfc/media/vc387l3.gif "vc387l3")  
Sekwencja tworzenia widoku  
  
 Informacje, jak platformę inicjuje nowy dokument, widok i okien ramowych obiektów, zobacz klasy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [cframewnd —](../mfc/reference/cframewnd-class.md), [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md), i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) w odwołaniu biblioteki MFC. Zobacz też [22 Uwaga techniczna](../mfc/tn022-standard-commands-implementation.md), którym omówiono procesów tworzenia i inicjowania dalsze jego dyskusji w ramach standardowych poleceń dla `New` i **Otwórz** elementów w **Pliku** menu.  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicjowanie własne dodatki do tych klas  
 Poprzednimi również sugerować punktów, w których można zastąpić funkcji elementów członkowskich do zainicjowania obiekty Twojej aplikacji. Zastępowanie `OnInitialUpdate` w widoku klasy jest najlepszym miejscem, aby zainicjować widoku. `OnInitialUpdate` Wywołania występuje natychmiast po utworzeniu okno ramowe i widok do ramki okna jest dołączony do jego dokumentu. Na przykład, jeśli widok jest widokiem przewijania (pochodną `CScrollView` zamiast `CView`), należy ustawić rozmiar widoku, zależnie od rozmiaru dokumentu w Twojej `OnInitialUpdate` zastąpienia. (Ten proces jest opisany w opisie klasy [CScrollView](../mfc/reference/cscrollview-class.md).) Można zastąpić **CDocument** funkcje Członkowskie `OnNewDocument` i `OnOpenDocument` zapewnienie specyficzne dla aplikacji Inicjowanie dokumentu. Zazwyczaj konieczne jest przesłonięcie zarówno od dokumentu można utworzyć na dwa sposoby.  
  
 W większości przypadków zastąpienia powinny wywoływać wersja klasy podstawowej. Aby uzyskać więcej informacji, zobacz funkcji o nazwie elementu członkowskiego klasy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [cframewnd —](../mfc/reference/cframewnd-class.md), i [CWinApp](../mfc/reference/cwinapp-class.md) w MFC Odwołanie do biblioteki.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)   
 [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)   
 [Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)

