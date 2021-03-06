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
ms.openlocfilehash: 1ef4ed9865d3a88a6ff85f777984b856d03cc48e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616360"
---
# <a name="containers-advanced-features"></a>Kontenery: funkcje zaawansowane

W tym artykule opisano kroki niezbędne do uwzględnienia opcjonalnych zaawansowanych funkcji w istniejących aplikacjach kontenera. Te funkcje są następujące:

- [Aplikacja, która jest zarówno kontenerem, jak i serwerem](#_core_creating_a_container_server_application)

- [Łącze OLE do osadzonego obiektu](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Tworzenie aplikacji kontenera/serwera

Aplikacja kontenera/serwera to aplikacja, która działa zarówno jako kontener, jak i serwer. Przykładem tego programu jest program Microsoft Word dla systemu Windows. Możesz osadzić program Word for Windows Documents w innych aplikacjach, a także osadzić elementy w programie Word dla dokumentów systemu Windows. Proces modyfikowania aplikacji kontenera jako kontenera i pełnego serwera (nie można utworzyć kombinacji kontenera/aplikacji miniserver) jest podobny do procesu tworzenia pełnego serwera.

Artykuł [serwery: implementacja serwera](servers-implementing-a-server.md) zawiera kilka zadań wymaganych do zaimplementowania aplikacji serwera. W przypadku konwertowania aplikacji kontenera do aplikacji kontenera/serwera należy wykonać niektóre z tych samych zadań, dodając kod do kontenera. Poniżej wymieniono ważne zagadnienia, które należy wziąć pod uwagę:

- Kod kontenera utworzony przez Kreatora aplikacji już inicjuje podsystem OLE. Nie trzeba zmieniać ani dodawać żadnych elementów do pomocy technicznej.

- Niezależnie od klasy bazowej klasy dokumentu `COleDocument` , należy zmienić klasę bazową na `COleServerDoc` .

- Przesłoń `COleClientItem::CanActivate` , aby uniknąć edytowania elementów w miejscu, gdy sam serwer jest używany do edycji w miejscu.

   Na przykład [OCLIENT](../overview/visual-cpp-samples.md) MFC OLE przykład osadzony element utworzony przez aplikację kontener/serwer. Otwórz aplikację OCLIENT i w miejscu Edytuj element utworzony przez aplikację kontener/serwer. Podczas edytowania elementu aplikacji użytkownik decyduje o osadzeniu elementu utworzonego przez przykładową [HIERSVR](../overview/visual-cpp-samples.md)MFC OLE. W tym celu nie można użyć aktywacji w miejscu. Aby aktywować ten element, należy w pełni otworzyć HIERSVR. Ponieważ biblioteka MFC nie obsługuje tej funkcji OLE, zastępowanie `COleClientItem::CanActivate` umożliwia sprawdzenie tej sytuacji i uniemożliwienie możliwego błędu czasu wykonywania w aplikacji.

Jeśli tworzysz nową aplikację i chcesz, aby działała ona jako aplikacja kontenera/serwera, wybierz tę opcję w oknie dialogowym Opcje OLE w Kreatorze aplikacji, a ta obsługa zostanie utworzona automatycznie. Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Tworzenie kontenera kontrolki ActiveX](reference/creating-an-mfc-activex-control-container.md). Aby uzyskać informacje na temat przykładów MFC, zobacz [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Należy pamiętać, że nie można wstawić aplikacji MDI do samej siebie. Aplikacji, która jest kontenerem/serwerem, nie można wstawić do samego siebie, chyba że jest to aplikacja SDI.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Linki do osadzonych obiektów

Funkcja linków do obiektów osadzonych umożliwia użytkownikowi utworzenie dokumentu z linkiem OLE do osadzonego obiektu wewnątrz aplikacji kontenera. Na przykład Utwórz dokument w edytorze tekstów zawierający osadzony arkusz kalkulacyjny. Jeśli aplikacja obsługuje linki do osadzonych obiektów, może wkleić link do arkusza kalkulacyjnego zawartego w dokumencie edytora tekstów. Ta funkcja pozwala aplikacji na korzystanie z informacji zawartych w arkuszu kalkulacyjnym bez znajomości tego, gdzie został pierwotnie uzyskany przez procesor wyrazów.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Aby połączyć się z osadzonymi obiektami w aplikacji

1. Utwórz klasę dokumentu od `COleLinkingDoc` zamiast `COleDocument` .

1. Utwórz identyfikator klasy OLE (**CLSID**) dla aplikacji przy użyciu generatora identyfikatora klasy dołączonego do narzędzi deweloperskich OLE.

1. Zarejestruj aplikację za pomocą OLE.

1. Utwórz `COleTemplateServer` obiekt jako element członkowski klasy aplikacji.

1. W `InitInstance` funkcji składowej klasy aplikacji wykonaj następujące czynności:

   - Połącz `COleTemplateServer` obiekt z szablonami dokumentów, wywołując `ConnectTemplate` funkcję elementu członkowskiego obiektu.

   - Wywołaj `COleTemplateServer::RegisterAll` funkcję członkowską, aby zarejestrować wszystkie obiekty klasy w systemie OLE.

   - Wywołanie `COleTemplateServer::UpdateRegistry` . Jedynym parametrem, który `UpdateRegistry` powinien zostać *OAT_CONTAINER* , jeśli aplikacja nie jest uruchomiona z przełącznikiem "/Embedded". To rejestruje aplikację jako kontener, który może obsługiwać linki do osadzonych obiektów.

      Jeśli aplikacja jest uruchamiana z przełącznikiem "/Embedded", nie powinien zawierać okna głównego, podobnego do aplikacji serwerowej.

Przykład [OCLIENT](../overview/visual-cpp-samples.md) MFC OLE implementuje tę funkcję. Aby zapoznać się z przykładem tego, jak to zrobić, zobacz `InitInstance` Funkcja w *OCLIENT. Plik CPP* tej przykładowej aplikacji.

## <a name="see-also"></a>Zobacz też

[Containers](containers.md)<br/>
[Serwery](servers.md)
