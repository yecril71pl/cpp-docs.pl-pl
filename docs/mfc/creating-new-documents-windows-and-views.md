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
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371667"
---
# <a name="creating-new-documents-windows-and-views"></a>Tworzenie nowych dokumentów, okien i widoków

Poniższe rysunki zawierają omówienie procesu tworzenia dokumentów, widoków i okien ramek. Inne artykuły, które koncentrują się na uczestniczących obiektów podać dalsze szczegóły.

Po zakończeniu tego procesu współpracujące obiekty istnieją i przechowują wskaźniki względem siebie nawzajem. Poniższe rysunki przedstawiają kolejność tworzenia obiektów. Można śledzić sekwencję od rysunku do rysunku.

![Sekwencja tworzenia dokumentu](../mfc/media/vc387l1.gif "Sekwencja tworzenia dokumentu") <br/>
Sekwencja w tworzeniu dokumentu

![Sekwencja tworzenia okna ramki](../mfc/media/vc387l2.png "Sekwencja tworzenia okna ramki") <br/>
Sekwencja w tworzeniu okna ramki

![Sekwencja tworzenia widoku](../mfc/media/vc387l3.gif "Sekwencja tworzenia widoku") <br/>
Sekwencja w tworzeniu widoku

Aby uzyskać informacje o tym, jak struktura inicjuje nowy dokument, widok i frame-window obiektów, zobacz klasy [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)i [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) w odwołaniu do biblioteki MFC. Zobacz także [Uwaga techniczna 22](../mfc/tn022-standard-commands-implementation.md), która wyjaśnia procesy tworzenia i inicjowania dalej w ramach dyskusji na temat standardowych poleceń struktury dla **nowych** i **otwartych** elementów w menu **Plik.**

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicjowanie własnych dodatków do tych klas

Powyższe liczby sugerują również punkty, w których można zastąpić funkcje członkowskie, aby zainicjować obiekty aplikacji. Zastąpienie `OnInitialUpdate` w klasie widoku jest najlepszym miejscem do zainicjowania widoku. Wywołanie `OnInitialUpdate` występuje natychmiast po utworzeniu okna ramki i do niego dołączony jest widok w oknie ramki. Na przykład, jeśli widok jest widokiem przewijania (pochodzącym z `CScrollView` a nie `CView`), należy `OnInitialUpdate` ustawić rozmiar widoku na podstawie rozmiaru dokumentu w przesłonięciu. (Ten proces jest opisany w opisie klasy [CScrollView](../mfc/reference/cscrollview-class.md).) Można zastąpić funkcje `CDocument` `OnNewDocument` członkowskie `OnOpenDocument` i zapewnić inicjowanie specyficzne dla aplikacji dokumentu. Zazwyczaj należy zastąpić zarówno, ponieważ dokument może być tworzony na dwa sposoby.

W większości przypadków zastąpienie należy wywołać wersję klasy podstawowej. Aby uzyskać więcej informacji, zobacz nazwane funkcje członkowskie klas [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md)i [CWinApp](../mfc/reference/cwinapp-class.md) w odwołaniu do biblioteki MFC.

## <a name="see-also"></a>Zobacz też

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)
