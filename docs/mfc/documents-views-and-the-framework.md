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
ms.openlocfilehash: e59e8b69dcdf0bf3b22d4286ba4692558a11e096
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175759"
---
# <a name="documents-views-and-the-framework"></a>Dokumenty, widoki i struktura

W ramach programu MFC framework są koncepcji dokument i widok. Dokument jest obiekt danych, z którą użytkownik wchodzi w interakcję w sesji. Jest ono tworzone przez **New** lub **Otwórz** polecenie **pliku** menu i są zwykle zapisywane w pliku. (Dokumentów standardowych MFC, pochodzi z klasy `CDocument`, różnią się od dokumenty aktywne i dokumentów złożonych OLE.) Widok jest obiekt window, przez który użytkownik wchodzi w interakcję z dokumentem.

Obiekty kluczy w uruchomionej aplikacji są:

- Dokument lub dokumenty.

   Klasy dokumentów (pochodną [CDocument](../mfc/reference/cdocument-class.md)) określa danych aplikacji.

   Jeśli potrzebujesz funkcji OLE w aplikacji, pochodzi z klasy dokumentów z [COleDocument](../mfc/reference/coledocument-class.md) lub jedna z jej klas pochodnych, w zależności od typu funkcji, potrzebujesz.

- Widoki lub widok.

   Klasa widoku (pochodną [CView](../mfc/reference/cview-class.md)) jest użytkownika "okno na danych." Widok klasy określa, jak użytkownik widzi danych w dokumencie i wchodzi w interakcję z nią. W niektórych przypadkach może być dokumentu, aby mieć wiele widoków danych.

   Jeśli potrzebujesz przewijania, pochodzi od [CScrollView](../mfc/reference/cscrollview-class.md). Jeśli widok ma interfejs użytkownika, który jest rozmieszczony w zasobach szablonu okna dialogowego, pochodzi od [CFormView](../mfc/reference/cformview-class.md). W przypadku zwykłego tekstu danych, użyj lub pochodzić od [CEditView](../mfc/reference/ceditview-class.md). Dla aplikacji opartej na formularzu dostępu do danych, takich jak program wprowadzania danych pochodzi od [CRecordView](../mfc/reference/crecordview-class.md) (dla ODBC). Dostępne są też klasy [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), i [CRichEditView](../mfc/reference/cricheditview-class.md).

- Okien ramowych

   Widoki są wyświetlane w "okien ramowych dokumentu." W aplikacji interfejsu SDI ramki okna dokumentu jest również "ramką głównego okna" dla aplikacji. W aplikacji MDI okna dokumentu są okien podrzędnych wyświetlany w oknie głównym ramki. Klasy pochodne główne okno ramek określa stylów i inne cechy charakterystyczne okien ramowych, które zawierają widoków. Jeśli musisz dostosować okien ramowych dziedziczyć [CFrameWnd](../mfc/reference/cframewnd-class.md) dostosowywania okna ramki dokumentu dla aplikacji interfejsu SDI. Pochodzi od [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) dostosować w oknie głównym ramki aplikacji MDI. Ponadto należy wyprowadzić klasę z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dostosowywania każdego distinct rodzaju okien ramowych dokumentu MDI, obsługiwanych przez aplikację.

- Szablon dokumentu lub szablonów

   Szablon dokumentu organizuje tworzenie dokumentów, widoków i okien ramowych. Klasa określonego szablonu dokumentu, pochodząca z klasy [CDocTemplate](../mfc/reference/cdoctemplate-class.md), tworzy i którymi zarządza wszystkich otwartych dokumentach jednego typu. Aplikacje, które obsługują więcej niż jeden typ dokumentu ma wielu szablonów dokumentów. Używanie klasy [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) dla aplikacji interfejsu SDI lub użyj klasy [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) dla aplikacji MDI.

- Obiekt aplikacji

   Klasa aplikacji (pochodną [CWinApp](../mfc/reference/cwinapp-class.md)) kontroluje wszystkie obiekty powyżej i określa zachowanie aplikacji, takich jak inicjowanie i oczyszczanie. Jeden aplikacji oraz pouze aplikace obiekt tworzy i którymi zarządza szablonów dokumentów, dla każdego dokumentu typów obsługuje aplikacja.

- Obiekty wątków

   Jeśli aplikacja tworzy oddzielnych wątkach wykonywania — na przykład w celu wykonywania obliczeń w tle — użyjesz klasy pochodne [CWinThread](../mfc/reference/cwinthread-class.md). [Klasa CWinApp](../mfc/reference/cwinapp-class.md) sam jest tworzony na podstawie `CWinThread` i reprezentuje podstawowy wątek wykonywania (lub głównego procesu) w aplikacji. Umożliwia także MFC w wątków pomocniczych.

W uruchomionej aplikacji te obiekty wspólne reagować na działania użytkownika związane ze sobą polecenia i inne komunikaty. Obiekt pojedynczej aplikacji zarządza co najmniej jeden szablon dokumentu. Każdy szablon dokumentu, tworzy i zarządza jednego lub wielu dokumentów (w zależności od tego, czy aplikacja jest SDI lub MDI). Użytkownik przegląda i manipuluje dokumentu za pośrednictwem widoku zawarte wewnątrz okna ramki. Na poniższej ilustracji przedstawiono relacje między tymi obiektami dla aplikacji interfejsu SDI.

![Obiekty w uruchomionej aplikacji interfejsu SDI](../mfc/media/vc386v1.gif "obiektów w uruchomionej aplikacji interfejsu SDI") <br/>
Obiekty w uruchomionej aplikacji interfejsu SDI

Pozostała część tej rodziny artykuły wyjaśniono, jak narzędzia framework, Kreator aplikacji MFC i edytory zasobów, utworzyć te obiekty, jak one współdziałają ze sobą i sposób ich używania w programowaniu usługi. Dokumentów, widoków i okien ramowych zostały omówione bardziej szczegółowo w [obiektów okien](../mfc/window-objects.md) i [architektury dokument/widok](../mfc/document-view-architecture.md).

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
