---
title: Dokumenty, widoki i struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2a30f2ccf1963fe2985794a2bf8eca0c49474cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="documents-views-and-the-framework"></a>Dokumenty, widoki i struktura
Istotą programu MFC framework są dokumentu i widoku. Dokument jest obiekt danych, z którą użytkownik wchodzi w interakcję w sesji. Jest tworzona przez `New` lub **Otwórz** na **pliku** menu i są zwykle zapisywane w pliku. (Dokumentów standardowego MFC, pochodzi z klasy **CDocument**, są inne niż dokumenty aktywne i dokumentów złożonych OLE.) Widok jest obiekt window, za pomocą którego użytkownik wchodzi w interakcję z dokumentu.  
  
 Obiekt klucza w uruchomionej aplikacji są:  
  
-   Dokument lub dokumenty.  
  
     Klasy dokumentów (pochodną [CDocument](../mfc/reference/cdocument-class.md)) określa dane aplikacji.  
  
     Chcąc funkcji OLE w aplikacji, pochodzi z klasy dokumentu [COleDocument](../mfc/reference/coledocument-class.md) lub jednej z jej klas pochodnych, w zależności od typu funkcji należy.  
  
-   Widok lub widoków.  
  
     Klasy widoku (pochodną [CView](../mfc/reference/cview-class.md)) użytkownika "okna na danych." Klasa widoku Określa, jak użytkownik widzi danych dokumentu i wchodzi w interakcję z nią. W niektórych przypadkach można mieć wiele widoków danych dokumentu.  
  
     Jeśli potrzebujesz przewijania, pochodzi z [CScrollView](../mfc/reference/cscrollview-class.md). Jeśli widok ma interfejs użytkownika, który jest rozmieszczona w zasobie szablonu okna dialogowego, pochodzi z [CFormView](../mfc/reference/cformview-class.md). Prosty tekst danych, użyj lub pochodzić od [CEditView](../mfc/reference/ceditview-class.md). Dla aplikacji opartej na formularzu dostępu do danych, takich jak program wprowadzania danych pochodzi od [CRecordView](../mfc/reference/crecordview-class.md) (dla ODBC). Dostępne są także klasy [CTreeView —](../mfc/reference/ctreeview-class.md), [clistview —](../mfc/reference/clistview-class.md), i [cricheditview —](../mfc/reference/cricheditview-class.md).  
  
-   Okna ramowe  
  
     Widoki są wyświetlane w elemencie "okien ramowych dokumentu." W aplikacji SDI okno ramowe dokument jest również "głównego okna ramowego" dla aplikacji. W aplikacji MDI okna dokumentów są wyświetlane w elemencie główne okno ramowe okien podrzędnych. Klasy pochodne głównego okna ramowego określa style i inne właściwości systemu windows ramki, które zawierają widoków. Jeśli musisz dostosować okien ramowych, pochodzi z [cframewnd —](../mfc/reference/cframewnd-class.md) dostosować okno ramowe dokumentów dla SDI — aplikacje. Pochodzić od [cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md) dostosować głównego okna ramowego dla aplikacji MDI. Również pochodzić z klasy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dostosować każdego rodzaju różne okien ramowych dokumentu MDI obsługiwanych przez aplikację.  
  
-   Szablon dokumentu lub szablonów  
  
     Szablon dokumentu organizuje tworzenie dokumentów, widoków i okien ramowych. Klasa określonego szablonu dokumentu, pochodzi z klasy [cdoctemplate —](../mfc/reference/cdoctemplate-class.md), tworzy i którymi zarządza wszystkie otwarte dokumenty jednego typu. Aplikacje, które obsługują więcej niż jeden typ dokumentu ma wielu szablonów dokumentów. Klasa [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI — aplikacje, lub użyj klasy [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) dla aplikacji MDI.  
  
-   Obiekt aplikacji  
  
     Klasy aplikacji (pochodną [CWinApp](../mfc/reference/cwinapp-class.md)) wszystkie obiekty powyżej kontrolki oraz określa zachowanie aplikacji, takich jak inicjowanie i oczyszczanie. Tylko aplikacji i aplikacji jeden obiekt tworzy i którymi zarządza szablonów dokumentów, dla każdego dokumentu typy aplikacja obsługuje.  
  
-   Obiekty wątków  
  
     Jeśli aplikacja tworzy oddzielnych wątkach wykonywania — na przykład w celu wykonywania obliczeń w tle — użyjesz klasy pochodzące od [cwinthread —](../mfc/reference/cwinthread-class.md). [Cwinapp —](../mfc/reference/cwinapp-class.md) sam jest pochodną `CWinThread` i reprezentuje podstawowy wątku wykonania (lub proces główny) w aplikacji. Umożliwia także MFC w dodatkowej wątków.  
  
 W uruchomionej aplikacji te obiekty wspólnie odpowiadanie na działania użytkownika związane ze sobą polecenia i inne komunikaty. Obiekt pojedynczą aplikacją zarządza co najmniej jeden szablon dokumentu. Każdy szablon dokumentu tworzy i którymi zarządza jednego lub wielu dokumentów (w zależności od tego, czy aplikacja jest SDI lub MDI). Widoki i manipuluje dokumentu za pośrednictwem widoku znajdująca się wewnątrz okno ramowe użytkownika. Na poniższej ilustracji przedstawiono relacje między tymi obiektami SDI aplikacji.  
  
 ![Obiekty w uruchomionej aplikacji SDI](../mfc/media/vc386v1.gif "vc386v1")  
Obiekty w uruchomionej aplikacji SDI  
  
 Pozostała część tej rodziny artykułów wyjaśniono, jak narzędzia framework, Kreator aplikacji MFC i edytory zasobów, utworzyć te obiekty, jak one współdziałają i sposobie korzystania w programowaniu usługi sieci. Dokumentów, widoków i okien ramowych omówiono bardziej szczegółowo w [obiektów okien](../mfc/window-objects.md) i [architektury dokument/widok](../mfc/document-view-architecture.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
