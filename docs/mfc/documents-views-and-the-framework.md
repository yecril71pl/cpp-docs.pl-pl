---
title: Dokumenty, widoki i struktura
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 17956c0b175e978c6e4e2fefcdad5f744929d457
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621836"
---
# <a name="documents-views-and-the-framework"></a>Dokumenty, widoki i struktura

Na początku struktury MFC są pojęcia dotyczące dokumentów i widoków. Dokument jest obiektem danych, z którym użytkownik pracuje w sesji edytowania. Jest on tworzony przez polecenie **New** lub **Open** w menu **plik** i jest zazwyczaj zapisywany w pliku. (Standardowe dokumenty MFC, pochodzące z klasy `CDocument` , różnią się od aktywnych dokumentów i dokumentów złożonych OLE). Widok to obiekt okna, za pomocą którego użytkownik współdziała z dokumentem.

Najważniejsze obiekty w działającej aplikacji to:

- Dokument lub dokumenty.

   Klasa dokumentu (pochodna od [CDocument](reference/cdocument-class.md)) określa dane aplikacji.

   Jeśli potrzebujesz funkcji OLE w aplikacji, Utwórz klasę dokumentu z [COleDocument](reference/coledocument-class.md) lub jednej z jej klas pochodnych, w zależności od typu funkcjonalności, której potrzebujesz.

- Widok lub widoki.

   Klasa widoku (pochodna from [CView](reference/cview-class.md)) jest oknem użytkownika "dane". Klasa widoku kontroluje sposób, w jaki użytkownik widzi dane dokumentu i współdziała z nim. W niektórych przypadkach może być konieczne, aby dokument miał wiele widoków danych.

   Jeśli potrzebujesz przewijania, Utwórz wynik z [CScrollView](reference/cscrollview-class.md). Jeśli widok ma interfejs użytkownika, który został określony w zasobie szablonu okna dialogowego, pochodzi od [CFormView](reference/cformview-class.md). W przypadku prostych danych tekstowych Użyj lub pochodnych z [elementu CEditView](reference/ceditview-class.md). W przypadku aplikacji dostępu do danych opartej na formularzach, takiej jak program do wprowadzania danych, pochodzi od [formularzy CRecordView](reference/crecordview-class.md) (dla ODBC). Dostępne są również klasy [CTreeView](reference/ctreeview-class.md), [CListView](reference/clistview-class.md)i [CRichEditView](reference/cricheditview-class.md).

- Okna ramowe

   Widoki są wyświetlane wewnątrz "okien ramowych dokumentu". W aplikacji SDI okno ramki dokumentu jest również "głównym oknem ramek" dla aplikacji. W aplikacji MDI okna dokumentów są oknami podrzędnymi wyświetlanymi w oknie ramka główna. Pochodna główna Klasa okien ramowych określa style i inne cechy okien ramowych, które zawierają widoki. Jeśli musisz dostosować okna ramowe, Utwórz pochodne od [obiektu CFrameWnd](reference/cframewnd-class.md) , aby dostosować okno ramki dokumentu dla aplikacji SDI. Utwórz pochodne od [CMDIFrameWnd](reference/cmdiframewnd-class.md) , aby dostosować główne okno ramek dla aplikacji MDI. Tworzy również klasę z [CMDIChildWnd](reference/cmdichildwnd-class.md) , aby dostosować każdy odrębny rodzaj okien ramowych dokumentu MDI obsługiwanych przez aplikację.

- Szablon dokumentu lub szablony

   Szablon dokumentu organizuje tworzenie dokumentów, widoków i okien ramowych. Określona Klasa szablonu dokumentu, pochodząca z klasy [CDocTemplate](reference/cdoctemplate-class.md), tworzy i zarządza wszystkimi otwartymi dokumentami jednego typu. Aplikacje obsługujące więcej niż jeden typ dokumentu mają wiele szablonów dokumentów. Użyj klasy [CSingleDocTemplate](reference/csingledoctemplate-class.md) dla aplikacji SDI lub użyj klasy [CMULTIDOCTEMPLATE](reference/cmultidoctemplate-class.md) dla aplikacji MDI.

- Obiekt aplikacji

   Klasa aplikacji (pochodna from [CWinApp](reference/cwinapp-class.md)) steruje wszystkimi powyższymi obiektami i określa zachowanie aplikacji, takie jak inicjowanie i oczyszczanie. Jeden i tylko obiekt aplikacji tworzy szablony dokumentów i zarządza nimi dla każdego typu dokumentu obsługiwanego przez aplikację.

- Obiekty wątków

   Jeśli aplikacja tworzy oddzielne wątki wykonywania — na przykład do wykonywania obliczeń w tle — używane są klasy pochodne z [CWinThread](reference/cwinthread-class.md). [CWinApp](reference/cwinapp-class.md) sama pochodzi od `CWinThread` i reprezentuje podstawowy wątek wykonywania (lub główny proces) w aplikacji. Można również użyć MFC w wątkach pomocniczych.

W działającej aplikacji te obiekty wspólnie reagują na akcje użytkownika, powiązane ze sobą za pomocą poleceń i innych komunikatów. Pojedynczy obiekt aplikacji zarządza jednym lub wieloma szablonami dokumentów. Każdy szablon dokumentu tworzy jeden lub więcej dokumentów i zarządza nimi (w zależności od tego, czy aplikacja jest SDI czy MDI). Użytkownik wyświetla i operuje na dokumencie za pomocą widoku zawartego w oknie ramki. Na poniższej ilustracji przedstawiono relacje między tymi obiektami dla aplikacji SDI.

![Obiekty w działającej aplikacji SDI](../mfc/media/vc386v1.gif "Obiekty w działającej aplikacji SDI") <br/>
Obiekty w działającej aplikacji SDI

Pozostała część tej rodziny artykułów wyjaśnia, jak narzędzia platformy, Kreator aplikacji MFC i edytory zasobów tworzą te obiekty, jak współpracują ze sobą i jak są używane w programowaniu. Okna dokumenty, widoki i ramki zostały omówione bardziej szczegółowo w temacie [obiekty okna](window-objects.md) i [Architektura dokumentu/widoku](document-view-architecture.md).

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](using-the-classes-to-write-applications-for-windows.md)
