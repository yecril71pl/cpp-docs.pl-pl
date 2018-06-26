---
title: 'Kontenery: Funkcje zaawansowane | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2999e82bd05d75cb8637ba7404c36cdc2be047a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932175"
---
# <a name="containers-advanced-features"></a>Kontenery: funkcje zaawansowane
W tym artykule opisano kroki niezbędne do włączają opcjonalne funkcje zaawansowane do istniejących aplikacji kontenera. Te funkcje są:  
  
-   [Aplikacja, która jest kontenerem i serwera](#_core_creating_a_container_server_application)  
  
-   [Połączenie osadzonych obiektów OLE](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container_server_application"></a> Tworzenie aplikacji kontenera/serwera  
 Aplikacja kontenera/serwera jest aplikacja, która działa jako kontener i serwer. Na przykład jest program Microsoft Word dla systemu Windows. Dokumenty Word dla systemu Windows można osadzić w innych aplikacjach, a można również osadzić elementy w dokumentach programu Word dla systemu Windows. Proces modyfikowania aplikacji kontenera zarówno kontener i pełny serwer (nie można utworzyć aplikacji kontenera/miniserver kombinacja) jest podobny do procesu tworzenia całego serwera.  
  
 Artykuł [serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md) Wyświetla liczbę zadań wymaganych do wdrożenia aplikacji serwera. Jeśli Konwertuj aplikacji kontenera do aplikacji kontenera/serwera, należy wykonać niektóre z tych samych zadań, dodawanie kodu do kontenera. Poniższa lista zawiera ważne zagadnienia, które należy wziąć pod uwagę:  
  
-   Kod kontenera tworzone przez Kreatora aplikacji już inicjuje podsystemu OLE. Nie musisz zmieniać lub dodawać żadnych stron na obsługę.  
  
-   Wszędzie tam, gdzie jest klasa podstawowa klasy dokumentu `COleDocument`, Zmień klasę podstawową do `COleServerDoc`.  
  
-   Zastąpienie `COleClientItem::CanActivate` do należy unikać edytowania elementów w miejsce, gdy sam serwer jest używany do edycji w miejscu.  
  
     Na przykład MFC OLE próbki [OCLIENT](../visual-cpp-samples.md) osadzone elementu utworzone przez aplikację kontenera/serwera. Otwórz aplikację OCLIENT i w miejscu edytowania elementu utworzonej przez aplikację kontener/serwer. Podczas edycji elementu aplikacji, zdecydujesz, aby osadzić elementu utworzone przez próbki MFC OLE [HIERSVR](../visual-cpp-samples.md). Aby to zrobić, nie można użyć aktywacji w miejscu. Należy otworzyć pełni HIERSVR do aktywowania tego elementu. Ponieważ Microsoft Foundation Class Library nie obsługuje tej funkcji OLE, zastępowanie `COleClientItem::CanActivate` można sprawdzić w takiej sytuacji należy również uniemożliwić możliwych błędów czasu wykonywania w aplikacji.  
  
 Jeśli tworzysz nową aplikację, a będzie działać jako aplikacja kontenera/serwera, wybierz czy opcji w oknie dialogowym Opcje OLE w Kreatorze aplikacji i ta obsługa zostanie utworzony automatycznie. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: Tworzenie kontenera formantu ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Informacje o MFC — przykłady znajdują się w temacie MFC — przykłady.  
  
 Należy pamiętać, że nie można wstawić aplikacji MDI do siebie samego. Nie można wstawić aplikacji kontenera/serwera do tego samego, chyba że jest to aplikacja SDI.  
  
##  <a name="_core_links_to_embedded_objects"></a> Łącza do osadzonych obiektów  
 Łącza do osadzonych obiektów funkcji umożliwia użytkownikowi utworzenie dokumentu o połączenie OLE osadzonego wewnątrz kontenera aplikacji. Na przykład utworzyć dokumentu w edytorze tekstu, zawierających osadzone arkusza kalkulacyjnego. Jeśli aplikacja obsługuje łącza do osadzonych obiektów, można go wkleić łącze do arkusza kalkulacyjnego zawarte w dokumencie edytora tekstów. Ta funkcja umożliwia aplikacji umożliwiająca użycie informacji zawartych w arkuszu kalkulacyjnym bez wiedzy o którym tekstów pierwotnie wiem.  
  
#### <a name="to-link-to-embedded-objects-in-your-application"></a>Aby utworzyć łącze do osadzonych obiektów w aplikacji  
  
1.  Pochodzi z klasy dokumentu `COleLinkingDoc` zamiast `COleDocument`.  
  
2.  Tworzenie Identyfikatora klasy OLE (**CLSID**) dla aplikacji za pomocą dołączonego Tools OLE programowanie generatora identyfikator klasy.  
  
3.  Zarejestrować aplikację w OLE.  
  
4.  Utwórz `COleTemplateServer` obiektu jako elementu członkowskiego klasy aplikacji.  
  
5.  W klasie aplikacji `InitInstance` elementu członkowskiego działać, wykonaj następujące czynności:  
  
    -   Połącz z `COleTemplateServer` obiektu do szablonów dokumentu przez wywołanie obiektu `ConnectTemplate` funkcję elementu członkowskiego.  
  
    -   Wywołanie `COleTemplateServer::RegisterAll` funkcji członkowskiej do rejestrowania wszystkich obiektów klasy w systemie OLE.  
  
    -   Wywołanie `COleTemplateServer::UpdateRegistry`. Tylko parametr `UpdateRegistry` powinien być *oat_container —* Jeśli aplikacja nie zostanie uruchomiona z przełącznikiem "/ osadzonego". To rejestruje aplikację jako kontener, który może obsługiwać łącza do osadzonych obiektów.  
  
         Jeśli aplikacja jest uruchomiona z przełącznikiem "/ osadzonego", nie powinny mieć jego głównego okna, podobnie jak aplikacja serwera.  
  
 Przykładowe MFC OLE [OCLIENT](../visual-cpp-samples.md) implementuje tę funkcję. Na przykład, jak to zrobić, zobacz `InitInstance` działać w *OCLIENT. CPP* plików tej aplikacji przykładowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Serwery](../mfc/servers.md)

