---
title: 'Kontenery: funkcje zaawansowane'
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
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376497"
---
# <a name="containers-advanced-features"></a>Kontenery: funkcje zaawansowane

W tym artykule opisano kroki niezbędne do włączenia opcjonalnych funkcji zaawansowanych do istniejących aplikacji kontenera. Te funkcje są następujące:

- [Aplikacja, która jest zarówno kontenerem, jak i serwerem](#_core_creating_a_container_server_application)

- [Łącze OLE do obiektu osadzonego](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Tworzenie aplikacji kontenera/serwera

Aplikacja kontenera/serwera jest aplikacją, która działa zarówno jako kontener, jak i serwer. Microsoft Word dla Windows jest tego przykładem. Dokumenty programu Word dla systemu Windows można osadzać w innych aplikacjach, a także osadzać elementy w dokumentach programu Word dla systemu Windows. Proces modyfikowania aplikacji kontenera jako kontenera i pełnego serwera (nie można utworzyć kombinacji aplikacji kontenera/miniserweru) jest podobny do procesu tworzenia pełnego serwera.

Artykuł [Serwery: Implementowanie serwera](../mfc/servers-implementing-a-server.md) zawiera listę szeregu zadań wymaganych do zaimplementowania aplikacji serwera. Jeśli konwertujesz aplikację kontenera do aplikacji kontenera/serwera, należy wykonać niektóre z tych samych zadań, dodając kod do kontenera. Poniżej wymieniono ważne kwestie, które należy wziąć pod uwagę:

- Kod kontenera utworzony przez kreatora aplikacji inicjuje już podsystem OLE. Nie trzeba będzie zmieniać ani dodawać niczego dla tej pomocy technicznej.

- Wszędzie tam, gdzie jest `COleDocument`klasa podstawowa klasy `COleServerDoc`dokumentu, zmień klasę podstawową na .

- Zastądnij, `COleClientItem::CanActivate` aby uniknąć edytowania elementów w miejscu, podczas gdy sam serwer jest używany do edycji w miejscu.

   Na przykład przykładowy [OCLIENT](../overview/visual-cpp-samples.md) OLE MFC osadzł element utworzony przez aplikację kontenera/serwera. Otwórz aplikację OCLIENT i edytuj element utworzony przez aplikację kontenera/serwera. Podczas edytowania elementu aplikacji, zdecydujesz, że chcesz osadzić element utworzony przez przykładowy program MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). W tym celu nie można użyć aktywacji w miejscu. Aby aktywować ten przedmiot, musisz w pełni otworzyć program HIERSVR. Ponieważ biblioteka klas programu Microsoft Foundation nie obsługuje `COleClientItem::CanActivate` tej funkcji OLE, zastępowanie umożliwia sprawdzenie tej sytuacji i zapobieganie ewentualnemu błędowi w czasie wykonywania w aplikacji.

Jeśli tworzysz nową aplikację i chcesz, aby działała jako aplikacja kontenera/serwera, wybierz tę opcję w oknie dialogowym Opcje OLE w kreatorze aplikacji, a ta obsługa zostanie utworzona automatycznie. Aby uzyskać więcej informacji, zobacz artykuł [Omówienie: Tworzenie kontenera sterowania ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Aby uzyskać informacje na temat próbek MFC, zobacz [Próbki MFC](../overview/visual-cpp-samples.md#mfc-samples).

Należy zauważyć, że nie można wstawić aplikacji MDI do siebie. Nie można wstawić do siebie aplikacji będącej kontenerem/serwerem, chyba że jest to aplikacja SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Łącza do obiektów osadzonych

Funkcja Łącza do obiektów osadzonych umożliwia użytkownikowi utworzenie dokumentu z łączem OLE do obiektu osadzonego wewnątrz aplikacji kontenera. Na przykład utwórz dokument w edytorze tekstu zawierającym osadzony arkusz kalkulacyjny. Jeśli aplikacja obsługuje łącza do obiektów osadzonych, może wkleić łącze do arkusza kalkulacyjnego znajdującego się w dokumencie edytora tekstu. Ta funkcja umożliwia aplikacji korzystanie z informacji zawartych w arkuszu kalkulacyjnym bez wiedzy, gdzie pierwotnie został użyty edytor tekstu.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Aby połączyć się z osadzonymi obiektami w aplikacji

1. Wywoż klasę `COleLinkingDoc` dokumentu `COleDocument`z zamiast .

1. Utwórz identyfikator klasy OLE **(CLSID)** dla aplikacji przy użyciu generatora identyfikatora klasy dołączonego do narzędzi programistycznych OLE.

1. Zarejestruj aplikację w ole.

1. Utwórz `COleTemplateServer` obiekt jako element członkowski klasy aplikacji.

1. W funkcji członkowskiej `InitInstance` klasy aplikacji wykonaj następujące czynności:

   - Połącz `COleTemplateServer` obiekt z szablonami dokumentów, wywołując `ConnectTemplate` funkcję elementu członkowskiego obiektu.

   - Wywołanie `COleTemplateServer::RegisterAll` funkcji elementu członkowskiego, aby zarejestrować wszystkie obiekty klasy w systemie OLE.

   - Zadzwoń `COleTemplateServer::UpdateRegistry`. Jedynym parametrem, który `UpdateRegistry` należy *OAT_CONTAINER,* jeśli aplikacja nie zostanie uruchomiona za pomocą przełącznika "/Embedded". Rejestruje aplikację jako kontener, który może obsługiwać łącza do obiektów osadzonych.

      Jeśli aplikacja jest uruchamiana za pomocą przełącznika "/Embedded", nie powinna ona wyświetlać swojego okna głównego, podobnego do aplikacji serwera.

Przykładowy [OCLIENT](../overview/visual-cpp-samples.md) OLE MFC implementuje tę funkcję. Na przykład, jak to zrobić, `InitInstance` zobacz funkcję w *OCLIENT. CPP* tej przykładowej aplikacji.

## <a name="see-also"></a>Zobacz też

[Containers](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)
