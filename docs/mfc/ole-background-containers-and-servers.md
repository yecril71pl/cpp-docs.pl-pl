---
title: 'Podstawy OLE: Kontenery i serwery'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: c154562e58cf8f37d77df61556fe25b19ca54c70
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346111"
---
# <a name="ole-background-containers-and-servers"></a>Podstawy OLE: Kontenery i serwery

Aplikacja kontenera jest aplikacja, która można zastosować osadzony lub połączony elementy w swoich własnych dokumentów. Dokumenty, zarządzane przez aplikację kontenera musi mieć możliwość przechowywania i wyświetlania elementów dokumentu OLE, a także dane utworzone przez samą aplikację. Aplikacja kontenera należy także zezwolić użytkownikom na wstawianie nowych elementów lub edycji istniejących elementów, aktywując aplikacji serwerowych, gdy jest to konieczne. Wymagania dotyczące interfejsu użytkownika aplikacji kontenera są wymienione w artykule [kontenerów: Problemy z interfejsem użytkownika](../mfc/containers-user-interface-issues.md).

Serwer aplikacji lub składnika aplikacji to aplikacja, można utworzyć elementów dokumentu OLE do użycia przez aplikacje kontenera. Aplikacje serwera zwykle obsługi przeciągania i upuszczania lub kopiowania danych do Schowka, tak, aby wstawić dane jako element osadzony lub połączony aplikacji kontenera. Aplikacja może być zarówno kontenera, jak i serwera.

Większość serwerów są aplikacje autonomiczne lub pełne serwerów; one albo mogą być uruchamiane jako autonomiczne aplikacje lub można uruchamiać przez aplikację kontenera. Miniserver jest specjalnym typem aplikacji serwera, które mogą być uruchamiane tylko przez kontener. Nie można uruchomić jako autonomiczną aplikację. Przykładami miniservers są serwery Microsoft Draw i programu Microsoft Graph.

Kontenery i serwery nie komunikują się bezpośrednio. Zamiast tego komunikują się za pośrednictwem bibliotek OLE systemu dołączana dynamicznie (DLL). Te biblioteki DLL udostępniają funkcje, które wywołują kontenery i serwery i kontenery i serwery udostępniają funkcje wywołania zwrotnego, które wywołują biblioteki dll.

Za pomocą oznacza, że komunikacji, kontener nie musi wiedzieć, szczegóły implementacji aplikacji serwera. Umożliwia to kontener zaakceptować elementy utworzone przez dowolnego serwera bez konieczności wcześniejszego definiowania typów serwerów, z którymi można pracować. W rezultacie użytkownik aplikacji kontenera korzystać z zalet formatów danych i aplikacji tworzonych w przyszłości. Jeśli te nowe aplikacje są składnikami OLE, złożonego dokumentu będą mieć możliwość zawierać elementy utworzone przez te aplikacje.

## <a name="see-also"></a>Zobacz także

[Podstawy OLE](../mfc/ole-background.md)<br/>
[Podstawy OLE: implementacja MFC](../mfc/ole-background-mfc-implementation.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)<br/>
[Kontenery: elementy klienckie](../mfc/containers-client-items.md)<br/>
[Serwery: elementy serwera](../mfc/servers-server-items.md)
