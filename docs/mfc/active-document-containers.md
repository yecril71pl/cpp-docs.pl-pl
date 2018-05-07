---
title: Kontenery dokumentów aktywnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a47db4f9715c539ecf9bcbfb78e48b7e8edbc94b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="active-document-containers"></a>Kontenery dokumentów aktywnych
Kontener dokumentów aktywnych, takich jak Microsoft Office Binder lub program Internet Explorer umożliwia pracę z dokumentami kilka typów innej aplikacji w ramach jednej ramki (zamiast wymuszania wielokrotnego do utworzenia i użycia wielu klatek aplikacji dla każdego Typ dokumentu).  
  
 Kontenery dokumentów aktywnych w MFC zapewnia pełną obsługę `COleDocObjectItem` klasy. Kreator aplikacji MFC umożliwia utworzenie kontenera dokumentów aktywnych wybierając **kontenera dokumentów aktywnych** pole wyboru na **Obsługa dokumentów złożonych** Kreatora aplikacji MFC. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji kontenera dokumentów aktywnych](../mfc/creating-an-active-document-container-application.md).  
  
 Aby uzyskać więcej informacji na temat kontenery dokumentów aktywnych zobacz:  
  
-   [Wymagania dotyczące kontenera](#container_requirements)  
  
-   [Obiekty witryny dokumentów](#document_site_objects)  
  
-   [Wyświetlanie obiektów witryny](#view_site_objects)  
  
-   [Obiekt ramki](#frame_object)  
  
-   [Scalanie menu Pomoc](../mfc/help-menu-merging.md)  
  
-   [Drukowanie programowe](../mfc/programmatic-printing.md)  
  
-   [Obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> Wymagania dotyczące kontenera  
 Obsługa dokumentów aktywnych w kontenera dokumentów aktywnych wymaga więcej niż tylko implementacje interfejsu: wymagany jest również znajomość przy użyciu interfejsów zawartego w nim obiektu. To samo dotyczy rozszerzenia aktywnego dokumentu, gdy kontener musi również wiedzieć, jak używać tych interfejsów rozszerzenia na same dokumenty aktywne.  
  
 Kontener dokumentów aktywnych, która integruje się dokumenty aktywne musi:  
  
-   Być może obsługiwać obiektu magazynu za pośrednictwem **IPersistStorage** interfejs, oznacza to, musi ona `IStorage` wystąpienie do każdego aktywnego dokumentu.  
  
-   Obsługuje podstawowe funkcje osadzania dokumentów OLE, wymagających obiektów "witryna", (po jednym dla każdego dokumentu lub osadzania) które implementują **IOleClientSite** i **IAdviseSink**.  
  
-   Obsługuje aktywacji w miejscu osadzonych obiektów lub dokumentów aktywnych. Obiekty lokacji kontenera musi implementować `IOleInPlaceSite` i podać kontener ramki **IOleInPlaceFrame**.  
  
-   Obsługuje dokumenty aktywne rozszerzeń zaimplementowanie `IOleDocumentSite` zapewnienie mechanizmu dla kontenera komunikował się z dokumentu. Opcjonalnie kontenera mogą implementować interfejsów dokumentów aktywnych `IOleCommandTarget` i `IContinueCallback` do pobrania prostych poleceń, takich jak drukowania lub zapisywania.  
  
 Opcjonalnie można zaimplementować obiekt ramki, obiekty widoku i kontenera obiektu **iolecommandtarget —** do obsługi wysyłania niektórych poleceń, zgodnie z opisem w [obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md). Opcjonalnie można zaimplementować widoku i kontenera obiektów `IPrint` i `IContinueCallback`, aby obsługiwać drukowanie programowe, zgodnie z opisem w [drukowanie programowe](../mfc/programmatic-printing.md).  
  
 Na poniższej ilustracji przedstawiono ogólne relacje między kontenera i jego składników (po lewej) i aktywny dokument i widokach (po prawej). Aktywny dokument zarządza magazynu i danych, a widok wyświetla lub opcjonalnie wyświetla dane. Interfejsy pogrubione są wymagane dla aktywnego dokumentu udział; pogrubionego oraz pochylonego są opcjonalne. Wszystkie inne interfejsy są wymagane.  
  
 ![Interfejsy kontenera dokumentów aktywnych](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 Dokument, który obsługuje tylko jeden widok można zaimplementować składniki widoku oraz dokumentu (to znaczy ich odpowiednich interfejsów) na jednej klasy konkretnej. Ponadto lokacji kontenera, który obsługuje tylko jeden widok naraz można łączyć z witryny dokumentów i wyświetlanie witryny w klasa pojedyncza lokacja konkretnych. Obiektu ramki kontenera, musi być jednak różne i składnik dokumentów kontenera jedynie znajduje się tutaj aby zapewnić pełną obraz architektury; nie ma wpływu na architekturę zawierania dokumentów aktywnych.  
  
##  <a name="document_site_objects"></a> Obiekty witryny dokumentów  
 W architekturze zawierania dokumentów aktywnych lokacji dokumentu jest taka sama jak obiekt lokacji klienta w dokumentach OLE z uwzględnieniem `IOleDocument` interfejsu:  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 Z witryny dokumentów koncepcyjnie to kontener dla co najmniej jeden obiekt "Widok site". Każdy obiekt lokacji widok jest skojarzone z obiektami poszczególnych widoku dokumentu zarządzani przez lokację dokumentu. Jeśli kontener obsługuje tylko jeden widok dla każdej witryny dokumentu, można go również implementować witryny dokumentów i wyświetlanie witryny z konkretną klasę.  
  
##  <a name="view_site_objects"></a> Wyświetlanie obiektów witryny  
 Kontener lokacji widok zarządza obszaru wyświetlania dokumentu w danym widoku. Oprócz obsługi standardowego `IOleInPlaceSite` ogólnie implementuje interfejs, Wyświetl witrynę `IContinueCallback` programowe kontrolki drukowania. (Należy pamiętać, że obiekt widoku nigdy nie przesyła zapytanie dotyczące `IContinueCallback` tak faktycznie można ją wdrożyć na dowolnej obiekt uznania kontenera.)  
  
 Kontener, który obsługuje wiele widoków musi mieć możliwość tworzenia widoku wielu obiektów lokacji w lokacji dokumentu. Zapewnia każdego widoku z oddzielnych Aktywacja i dezaktywacja usługi zgodnie z za pośrednictwem `IOleInPlaceSite`.  
  
##  <a name="frame_object"></a> Obiekt ramki  
 Kontener ramki jest w większości przypadków tej samej ramki, w której jest używany do aktywacji w miejscu w dokumentach OLE, oznacza to, który obsługuje negocjacje menu i paska narzędzi. Wyświetl obiekt ma dostęp do tego obiektu ramki za pośrednictwem **IOleInPlaceSite::GetWindowContext**, zapewniające dostęp do obiektu kontenera reprezentujący kontenerem (która może obsłużyć negocjacji poziomu okienka narzędzi i wyliczanie obiektów zawartych w niej).  
  
 Kontener dokumentów aktywnych można rozszerzyć ramki, dodając `IOleCommandTarget`. Dzięki temu odbierania poleceń, które pochodzą z dokumentów aktywnych interfejsu użytkownika w taki sam sposób, że ten interfejs umożliwia kontenera do wysyłania tych samych poleceń (takich jak **nowy plik**, **Otwórz**,  **Zapisz jako**, **drukowania**; **Edytować kopii**, **Wklej**, **Cofnij**i inne) do aktywnego dokumentu. Aby uzyskać więcej informacji, zobacz [obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

