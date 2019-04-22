---
title: 'Kontenery: Funkcje zaawansowane'
ms.date: 11/04/2016
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
ms.openlocfilehash: 350431975a4335fc06e436237b7e0d3388faab64
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769566"
---
# <a name="containers-advanced-features"></a>Kontenery: Funkcje zaawansowane

W tym artykule opisano kroki niezbędne do dołączyć opcjonalny zaawansowane funkcje do istniejących aplikacji kontenerowych. Te funkcje są:

- [Aplikacja kontenera i serwera](#_core_creating_a_container_server_application)

- [Łącze OLE na obiekt osadzony](#_core_links_to_embedded_objects)

##  <a name="_core_creating_a_container_server_application"></a> Tworzenie aplikacji kontenera/serwera

Aplikacja kontenera/serwera jest aplikacja, która działa jako kontener i serwerem. Program Microsoft Word dla Windows jest przykładem. Dokumenty programu Word for Windows można osadzić w innych aplikacjach, a elementy można również osadzić w dokumentach programu Word for Windows. Modyfikowanie aplikację kontenera do kontenera i całego serwera (nie można utworzyć aplikację kontenera/miniserver kombinacji) proces jest podobny do procesu tworzenia całego serwera.

Artykuł [serwerów: Implementowanie serwera](../mfc/servers-implementing-a-server.md) Wyświetla liczbę zadania wymagane do wdrożenia aplikacji serwera. Po skonwertowaniu aplikacji kontenera do aplikacji kontenera/serwera, należy wykonać niektóre z tych samych zadań, dodając kod do kontenera. Poniższa lista zawiera ważnych kwestii, które należy wziąć pod uwagę:

- Kod kontenera, tworzone przez Kreatora aplikacji już inicjuje podsystemu OLE. Nie musisz zmieniać lub dodawać żadnych tej obsługi.

- Wszędzie tam, gdzie jest klasą bazową klasy dokumentu `COleDocument`, Zmień klasę bazową do `COleServerDoc`.

- Zastąp `COleClientItem::CanActivate` w celu uniknięcia edytowanie elementów w miejscu, gdy sam serwer jest używany do edycji w miejscu.

   Na przykład MFC OLE próbki [OCLIENT](../overview/visual-cpp-samples.md) zawierający osadzone element, który został utworzony przez aplikację kontenera/serwera. Otwórz aplikację OCLIENT i w miejscu edytowania elementu tworzone przez testowaną aplikację kontenera/serwera. Podczas edytowania elementu aplikacji, zdecydujesz, którą chcesz osadzić elementu utworzonych w ramach przykładu MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Aby to zrobić, nie można użyć aktywacji w miejscu. Należy otworzyć pełni HIERSVR można aktywować tego elementu. Ponieważ biblioteki klas Microsoft Foundation nie obsługuje tej funkcji OLE, zastępowanie `COleClientItem::CanActivate` można to sprawdzić i uniknąć możliwych błędów czasu wykonywania w aplikacji.

Jeśli tworzysz nową aplikację i ją do działania jako aplikacji kontenera/serwera, wybierz opcję automatycznie utworzone opcji w oknie dialogowym Opcje OLE, Kreator aplikacji i wsparcie dzięki tym. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: Tworzenie kontenera kontrolek ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Aby uzyskać informacji na temat próbki MFC Zobacz próbki MFC.

Należy pamiętać, że aplikacja MDI nie można wstawić do niej samej. Aplikacja kontenera/serwera nie można wstawić do niej samej, chyba że jest aplikacją SDI.

##  <a name="_core_links_to_embedded_objects"></a> Łącza do osadzonych obiektów

Łącza do osadzonych obiektów funkcji pozwala użytkownikowi na tworzenie dokumentu za pomocą łączy OLE na obiekt osadzony w aplikacji kontenera. Na przykład można utworzyć dokumentu w edytorze tekstów, zawierający arkusz kalkulacyjny programu osadzonego. Jeśli aplikacja obsługuje łącza do osadzonych obiektów, można go wkleić link do arkusza kalkulacyjnego zawarte w dokumencie edytora tekstów. Ta funkcja umożliwia aplikacji na korzystanie z informacji zawartych w arkuszu kalkulacyjnym, nie wiedząc o tym, gdzie edytora tekstów pierwotnie rozumiem.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Aby utworzyć łącze do osadzonych obiektów w aplikacji

1. Pochodzi z klasy dokumentu `COleLinkingDoc` zamiast `COleDocument`.

1. Tworzenie Identyfikatora klasy OLE (**CLSID**) dla swojej aplikacji, korzystając z generatorem identyfikator klasy, które są dołączone do OLE narzędzi deweloperskich programu.

1. Zarejestrować aplikację w OLE.

1. Utwórz `COleTemplateServer` obiektu jako członek klasy aplikacji.

1. W klasie aplikacji `InitInstance` element członkowski funkcji, wykonaj następujące czynności:

   - Połącz swoje `COleTemplateServer` obiektu do szablonów dokumentów przez wywołanie obiektu `ConnectTemplate` funkcja elementu członkowskiego.

   - Wywołaj `COleTemplateServer::RegisterAll` funkcja elementu członkowskiego do rejestrowania wszystkich obiektów klasy przy użyciu systemu OLE.

   - Wywołaj `COleTemplateServer::UpdateRegistry`. Tylko parametr `UpdateRegistry` powinien być *OAT_CONTAINER* Jeśli aplikacja nie zostanie uruchomiona z przełącznikiem "/ osadzonego". To rejestruje aplikację jako kontener, który może obsługiwać łącza do osadzonych obiektów.

         If the application is launched with the "/Embedded" switch, it should not show its main window, similar to a server application.

Przykładowe MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) implementuje tę funkcję. Aby uzyskać przykład jak to zrobić, zobacz `InitInstance` działa w programach *OCLIENT. CPP* plików tej aplikacji przykładowej.

## <a name="see-also"></a>Zobacz także

[Kontenery](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)
