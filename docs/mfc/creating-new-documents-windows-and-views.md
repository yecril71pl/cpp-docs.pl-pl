---
title: Tworzenie nowych dokumentów, okien i widoków
ms.date: 11/19/2018
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
ms.openlocfilehash: 3d4ca55a9bff6ec42643db745896a2cea96dcefb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297813"
---
# <a name="creating-new-documents-windows-and-views"></a>Tworzenie nowych dokumentów, okien i widoków

Następujące dane liczbowe zapewniają Przegląd procesu tworzenia dokumentów, widoków i okien ramowych. Inne artykuły, które koncentrują się na obiektach uczestniczących w programie dostarczyć więcej szczegółów.

Po zakończeniu tego procesu współpracujących obiektów istnieje i Zapisz wskaźniki do siebie nawzajem. Poniższe rysunki pokazują kolejność, w którym tworzony jest obiekt. Rysunek rysunek można wykonać sekwencji.

![Sekwencja tworzenia dokumentu](../mfc/media/vc387l1.gif "sekwencji tworzenia dokumentu") <br/>
Sekwencja przy tworzeniu dokumentu

![Sekwencja tworzenia okna ramki](../mfc/media/vc387l2.png "Sekwencja tworzenia okna ramki") <br/>
Sekwencja tworzenia okna ramki

![Kolejność potrzeby tworzenia widoku](../mfc/media/vc387l3.gif "sekwencji na potrzeby tworzenia widoku") <br/>
Sekwencja w tworzeniu widoku

Informacje, jak struktura inicjuje nowy dokument, widok i okien ramowych obiektów, zobacz klasy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) w odwołanie do biblioteki MFC. Zobacz też [techniczne 22 Uwaga](../mfc/tn022-standard-commands-implementation.md), co wyjaśnia procesów tworzenia i inicjowania bardziej szczegółowo w obszarze dyskusji w ramach standardowych poleceń dla **New** i **Otwórz** elementów na **pliku** menu.

##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> Inicjowanie własne dodatki do tych klas

Poprzednimi również sugerować punkty, w których można zastąpić, funkcje składowe w celu zainicjowania obiektów Twojej aplikacji. Zastępowanie `OnInitialUpdate` w widoku klasy to najlepsze miejsce do zainicjowania tego widoku. `OnInitialUpdate` Wywołanie występuje natychmiast po utworzeniu ramki okna i widok w oknie ramki jest dołączony do swoich dokumentów. Na przykład, jeśli widok jest widokiem przewijania (pochodną `CScrollView` zamiast `CView`), należy ustawić rozmiar widoku, w zależności od rozmiaru dokumentu w swojej `OnInitialUpdate` zastąpienia. (Ten proces jest opisany w opisie klasy [CScrollView](../mfc/reference/cscrollview-class.md).) Można zastąpić `CDocument` elementów członkowskich `OnNewDocument` i `OnOpenDocument` zapewnienie specyficzne dla aplikacji Inicjowanie dokumentu. Zazwyczaj konieczne jest przesłonięcie zarówno od dokumentu, można utworzyć na dwa sposoby.

W większości przypadków przesłonięcia, należy wywołać wersję klasy podstawowej. Aby uzyskać więcej informacji, zapoznaj się z funkcjami nazwanego elementu członkowskiego klasy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), i [CWinApp](../mfc/reference/cwinapp-class.md) w MFC Odwołanie do biblioteki.

## <a name="see-also"></a>Zobacz także

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)
