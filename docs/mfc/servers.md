---
title: Serwery
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: d1e0a8ca85055c289d1ef8e1c36fcd35eab61c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526507"
---
# <a name="servers"></a>Serwery

Aplikacja serwera (lub składnik aplikacji) tworzy elementy OLE (lub składniki) do użycia przez aplikacje kontenera. Wizualne edycji aplikacji serwera obsługuje również edycja wizualna lub aktywacji w miejscu. Jest inna forma serwera OLE [serwer automatyzacji](../mfc/automation-servers.md). Niektóre aplikacje serwera obsługuje tylko tworzenie elementów osadzonych; inne osoby obsługuje tworzenie elementy osadzone i połączone. Niektóre z nich obsługują łączenie tylko, mimo że jest to rzadkie. Wszystkie aplikacje serwera musi obsługiwać aktywacji przez aplikacje kontenera, gdy użytkownik chce, aby edytować element. Aplikacja może być zarówno kontenera, jak i serwera. Innymi słowy jego można zarówno dołączyć danych do swoich dokumentów i tworzyć dane, które można zintegrować jako elementy dokumenty w innych aplikacjach.

Miniserver jest specjalnym typem aplikacji serwera, które mogą być uruchamiane tylko przez kontener. Microsoft Draw i Microsoft Graph są przykładami miniservers. Miniserver nie przechowuje dokumenty jako pliki na dysku. Zamiast tego jego dokumentów z odczytuje i zapisuje je do elementów w dokumentach należących do kontenerów. W rezultacie miniserver obsługuje tylko osadzania w nie łączenie.

Pełny serwer można uruchamiać w aplikacji autonomicznej lub uruchomiona przez aplikację kontenera. Pełny serwer można przechowywać dokumenty, jako pliki na dysku. Może obsługiwać tylko osadzania, zarówno osadzania i łączenie lub tylko połączenie. Użytkownik aplikacji kontenera można utworzyć element osadzony, wybierając polecenia Wytnij lub Kopiuj w i na serwerze polecenie Paste w kontenerze. Połączony element jest tworzony przez wybranie polecenia kopiowania na serwerze i Wklej łącze w kontenerze. Alternatywnie użytkownik może utworzyć element osadzony lub połączony za pomocą okna dialogowego Wstawianie obiektu.

W poniższej tabeli przedstawiono charakterystykę różnego rodzaju serwerów:

### <a name="server-characteristics"></a>Właściwości serwera

|Typ serwera|Obsługuje wiele wystąpień|Liczba elementów na dokumentu|Dokumenty, dla każdego wystąpienia|
|--------------------|---------------------------------|------------------------|----------------------------|
|Miniserver|Tak|1|1|
|SDI pełny serwer|Tak|1 (Jeśli połączenie jest obsługiwany, co najmniej 1)|1|
|Pełny serwer MDI|Brak (nie jest wymagane)|1 (Jeśli połączenie jest obsługiwany, co najmniej 1)|0 lub więcej|

Aplikacja serwera powinien obsługiwać jednocześnie wiele kontenerów, aby w przypadku, gdy więcej niż jednego kontenera będzie służyć do edytować element osadzony lub połączony. Jeśli serwer jest aplikacją SDI (lub miniserver z interfejsem okno dialogowe), wielu wystąpień serwera musi mieć możliwość jednoczesnego uruchamiania. Dzięki temu osobne wystąpienie aplikacji do obsługi danego żądania kontenera.

Jeśli serwer znajduje się aplikacja MDI, może utworzyć nowe podrzędne okno MDI każdorazowo kontenera musi edytowanie elementu. Dzięki temu jedno wystąpienie aplikacji może obsługiwać wiele kontenerów.

Aplikacja serwera musisz poinformować OLE systemowych bibliotek DLL co należy zrobić, jeśli jedno wystąpienie serwera jest już uruchomiony podczas innego kontenera żądań swoich usług: czy należy uruchomić nowe wystąpienie serwera lub wszystkie kontenery żądania kierowane do jednego wystąpienia serwer.

Aby uzyskać więcej informacji na serwerach zobacz:

- [Serwery: implementowanie serwera](../mfc/servers-implementing-a-server.md)

- [Serwery: implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md)

- [Serwery: implementowanie okien ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md)

- [Serwery: elementy serwera](../mfc/servers-server-items.md)

- [Serwery: kwestie dotyczące interfejsu użytkownika](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Kontenery: funkcje zaawansowane](../mfc/containers-advanced-features.md)<br/>
[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Rejestracja](../mfc/registration.md)<br/>
[Serwery automatyzacji](../mfc/automation-servers.md)

