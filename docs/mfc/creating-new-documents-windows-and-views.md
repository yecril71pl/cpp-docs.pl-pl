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
ms.openlocfilehash: 7a714b5d7ba97c12b7134fa4890bddf5ed095c5b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620565"
---
# <a name="creating-new-documents-windows-and-views"></a>Tworzenie nowych dokumentów, okien i widoków

Poniższe ilustracje przedstawiają przegląd procesu tworzenia dokumentów, widoków i okien ramowych. Inne artykuły, które koncentrują się na obiektach uczestniczących, zawierają więcej szczegółów.

Po zakończeniu tego procesu obiekty współdziałające istnieją i są przechowywane ze wskaźnikami. Poniższe ilustracje przedstawiają sekwencję tworzenia obiektów. Można wykonać sekwencję od rysunku do rysunku.

![Sekwencja tworzenia dokumentu](../mfc/media/vc387l1.gif "Sekwencja tworzenia dokumentu") <br/>
Sekwencja tworzenia dokumentu

![Sekwencja tworzenia okna ramki](../mfc/media/vc387l2.png "Sekwencja tworzenia okna ramki") <br/>
Sekwencja w tworzeniu okna ramowego

![Sekwencja tworzenia widoku](../mfc/media/vc387l3.gif "Sekwencja tworzenia widoku") <br/>
Sekwencja w tworzeniu widoku

Aby uzyskać informacje na temat sposobu inicjowania przez platformę nowych obiektów dokumentów, widoków i okien ramowych, zobacz klasy [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [obiektu CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)i [CMDIChildWnd](reference/cmdichildwnd-class.md) w dokumentacji biblioteki MFC. Zapoznaj się również z [uwagą techniczną 22](tn022-standard-commands-implementation.md), która wyjaśnia procesy tworzenia i inicjowania w ramach dyskusji na temat standardowych poleceń struktury dla **nowych** i **otwartych** elementów w menu **plik** .

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicjowanie własnych dodatków do tych klas

Powyższe cyfry również sugerują punkty, w których można przesłonić funkcje składowe w celu zainicjowania obiektów aplikacji. Przesłonięcie `OnInitialUpdate` klasy widoku jest najlepszym miejscem, aby zainicjować widok. `OnInitialUpdate`Wywołanie odbywa się natychmiast po utworzeniu okna ramki, a widok w oknie ramki jest dołączony do dokumentu. Na przykład jeśli widok jest widokiem przewijania (pochodnym od `CScrollView` zamiast `CView` ), należy ustawić rozmiar widoku na podstawie rozmiaru dokumentu w `OnInitialUpdate` przesłonięciu. (Ten proces jest opisany w opisie klasy [CScrollView](reference/cscrollview-class.md)). Można przesłonić `CDocument` funkcje składowe `OnNewDocument` i `OnOpenDocument` w celu podania zainicjowanej przez aplikację dokumentu inicjującego. Zazwyczaj należy przesłonić oba, ponieważ dokument można utworzyć na dwa sposoby.

W większości przypadków przesłonięcie powinno wywołać wersję klasy bazowej. Aby uzyskać więcej informacji, zobacz funkcje należące do elementów członkowskich klas [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [obiektu CFrameWnd](reference/cframewnd-class.md)i [CWinApp](reference/cwinapp-class.md) w dokumentacji biblioteki MFC.

## <a name="see-also"></a>Zobacz też

[Szablony dokumentów i proces tworzenia dokumentu/widoku](document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](document-view-creation.md)<br/>
[Relacje między obiektami MFC](relationships-among-mfc-objects.md)
