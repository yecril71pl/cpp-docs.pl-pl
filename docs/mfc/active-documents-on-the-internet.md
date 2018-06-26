---
title: Dokumenty aktywne w Internecie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a18b84b30445060631589e72f6c158ea9b3626f0
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930891"
---
# <a name="active-documents-on-the-internet"></a>Dokumenty aktywne w Internecie
Dokumenty aktywne zapewniają rozszerzenie do tradycyjnych osadzonych obiektów. Dokumenty aktywne może być wielostronicowe i są wyświetlane w obszarze klienckim. Czy negocjacji tradycyjnych menu i może być edytowany w miejscu, a także w otwartym oknie w aplikacji serwera. Zamiast jako mały prostokąt otoczone obramowaniem kreskowanym dokumenty aktywne są ramki pełnego i zawsze aktywny w miejscu.  
  
 Dokumenty aktywne można wyświetlić w kontenerze, takich jak Microsoft Office Binder, która umożliwia tworzenie złożonego dokumentu składają się z różnych typów dokumentów takich jak Word, Excel i typ niestandardowy dokument z których każdy może być edytowany pełne ramki. Dokumenty aktywne mogą być także wyświetlane w przeglądarce, takich jak Microsoft Internet Explorer, która jest kontenerem dokumentów aktywnych.  
  
 **Zalety dokumentów aktywnych obejmują:**  
  
-   Dokumenty mogą być wyświetlane pełne ramki, w oknie całego klienta.  
  
-   Dokumenty można otworzyć w osobnym oknie aplikacji.  
  
     W dokumencie otworzyć aplikacją pomocniczą musi istnieć na komputerze klienckim lub można pobrać oddzielnie, zanim będzie można uruchomić aplikacji. Przeglądarka może zostać zapisany funkcje (Word, PowerPoint i Excel podanie przeglądarki dokumentów). Pełna wersja aplikacji zapewniają pełną obsługę edycji.  
  
-   Dokumenty są zawsze aktywny w miejscu.  
  
-   Polecenia menu wywoływane z kontenera mogą być kierowane do dokumentu.  
  
-   Dokumenty można wyświetlić w przeglądarce sieci Web. Zapewnia bezproblemową integrację między dokumentów i innych stron sieci Web.  
  
     Użytkownik może przejdź na stronę sieci Web, następnie arkusz kalkulacyjny programu Excel, a następnie do dokumentu, które zostały napisane przy użyciu MFC Obsługa dokumentów aktywnych. Użytkownika można nawigować przy użyciu znanych interfejs sieci Web, co przełączniki przeglądarki między menu i widoków strony HTML, Excel i dokumentów aplikacji.  
  
-   Wszystkie aplikacje są wyświetlane w ramce wspólnej.  
  
## <a name="requirements-for-active-documents"></a>Wymagania dotyczące dokumentów aktywnych  
 Interfejsów wymienionych w poniższej tabeli obejmują interfejsach już wymagany dla osadzonych serwerów i kilka nowych dotycząca dokumentów aktywnych. MFC zawiera domyślne implementacje większość tych interfejsów w [COleServerDoc](../mfc/reference/coleserverdoc-class.md) klasy.  
  
|Dokument A...|Implementuje te interfejsy|  
|-------------------------|---------------------------------|  
|Używa złożone plików jako mechanizm jego magazynu.|`IPersistStorage`.|  
|Obsługuje podstawowe funkcje osadzania Active dokumentów, w tym Utwórz z pliku.|`IPersistFile`, `IOleObject`, i `IDataObject`.|  
|Obsługuje Aktywacja w miejscu.|`IOleInPlaceObject` i `IOleInPlaceActiveObject` (przy użyciu kontenera `IOleInPlaceSite` i `IOleInPlaceFrame` interfejsów).|  
|Obsługuje obejmujących te nowe interfejsy rozszerzenia aktywnego dokumentu. Niektóre interfejsy są opcjonalne.|`IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, i `IPrint`.|  
  
 MFC umożliwia rozszerzanie istniejących obsługi serwera osadzonych do dokumentów aktywnych.  
  
## <a name="add-active-document-support-to-a-new-application"></a>Dodaj obsługę aktywnego dokumentu do nowej aplikacji  
 Aby utworzyć nową aplikację z obsługą dokumentów aktywnych: W Kreator aplikacji MFC na **obsługuje złożone dokumentu** w obszarze "Obsługa dokumentów złożonych wybierz" wybierz pozycję **pełny serwer** lub  **Kontener/pełny serwer**, a w obszarze "Wybierz dodatkowe opcje" zaznacz pole wyboru **serwer dokumentów aktywnych**.  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> Konwertuj istniejącego serwera w trakcie MFC na serwer dokumentów aktywnych  
 Jeśli aplikacja została utworzona z wersją programu Visual C++ poprzedzające wersję 4.2 i jest już w procesie serwera, można dodać obsługę dokumentów aktywnych, wprowadzając zmiany w następujących klas:  
  
|Typ klasy|Wcześniej pochodną|Zmień, aby dziedziczyć|  
|----------------|---------------------------|---------------------------|  
|Ramowe w miejscu|`COleIPFrameWnd`|`COleDocIPFrameWnd`|  
|Element|`COleServerItem`|`CDocObjectServerItem`|  
  
 Zostanie również zmienić sposób wprowadzania informacji w rejestrze i wprowadzić inne zmiany. Jeśli dana aplikacja zawiera obecnie nie obsługuje składników modelu COM, możesz dodać obsługę serwera przez uruchomienie Kreatora aplikacji i integrowanie kod specyficzny dla składnika modelu COM z istniejącej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

