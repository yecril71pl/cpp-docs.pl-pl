---
title: 'Windows Sockets: Tło'
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 6ab866609d0b75aaf9d06a01c204433d80e7e3d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274933"
---
# <a name="windows-sockets-background"></a>Windows Sockets: Tło

W tym artykule opisano ujawnienia Windows Sockets. Artykuł również:

- [Definiuje pojęcie "gniazda"](#_core_definition_of_a_socket).

- [Opisuje typ danych uchwyt GNIAZDA](#_core_the_socket_data_type).

- [W tym artykule opisano zastosowań sockets](#_core_uses_for_sockets).

Specyfikacja Windows Sockets definiuje zgodne dane binarne sieci interfejs programowania dla Microsoft Windows. Windows Sockets opierają się na implementacji gniazd systemu UNIX w Berkeley Software Distribution (BSD, wersji 4.3) z uniwersytet kalifornijski w Berkeley. Specyfikację obejmuje procedury gniazda BSD stylu i rozszerzenia specyficzne dla Windows. Przy użyciu usługi Windows Sockets pozwala aplikacji komunikowanie się przez żadną siecią, który jest zgodny z interfejsu API Windows Sockets. Na Win32 Windows Sockets zapewnienia bezpieczeństwa wątków.

Wielu dostawców oprogramowania sieci obsługuje Windows Sockets w obszarze protokoły sieciowe, łącznie z TCP/IP Transmission Control Protocol/Internet Protocol (), Xerox sieci systemu (XNS), protokołu sieci DECNet firmy Digital Equipment Corporation, Internet Novell Corporation Pakiet programu Exchange/Sequenced spakowane Exchange (IPX/SPX) i inne. Chociaż istnieje specyfikacji Windows Sockets definiuje abstrakcję gniazda TCP/IP, każdy protokół sieciowy może być zgodne z Windows Sockets podając własną wersję biblioteki dołączanej (dynamicznie DLL), który implementuje Windows Sockets. Przykładami aplikacji komercyjnych napisane na platformie Windows Sockets Windows X serwery terminali emulatorów i systemów poczty elektronicznej.

> [!NOTE]
>  Windows Sockets ma na celu abstrakcji odnośnej sieci tak, aby nie trzeba mieć odpowiednią wiedzę na temat tej sieci, a zatem aplikację można uruchomić na żadną siecią, która obsługuje gniazda. W związku z tym ta dokumentacja nie omówiono w nim szczegóły protokołów sieciowych.

Biblioteki Microsoft Foundation Class (MFC) obsługuje programowanie z interfejsem API Windows Sockets, podając dwóch klas. Jedną z tych klas `CSocket`, zapewnia wysoki poziom abstrakcji, aby uprościć programowanie komunikacji dla Twojej sieci.

Specyfikacja Windows Sockets Windows Sockets: Otwórz interfejs dla sieci obliczeniowych w ramach programu Microsoft Windows, teraz w wersji 1.1, został opracowany jako otwarty standard sieci przez dużą grupę użytkowników indywidualnych i firm w społeczności TCP/IP i jest dostępne bezpłatnie do użytku. Gniazda obecnie programowania modelu obsługuje jeden "komunikacji domena", przy użyciu zestawem protokołów internetowych. Specyfikacja jest dostępna w zestawie Windows SDK.

> [!TIP]
>  Ponieważ gniazda korzystają z zestawem protokołów internetowych, są one trasą preferowaną dla aplikacji, które obsługują komunikację z Internetem na "drogach informacji".

##  <a name="_core_definition_of_a_socket"></a> Definicja gniazda

Gniazdo jest punktem końcowym komunikacji — obiekt za pomocą którego aplikacja Windows Sockets wysyła lub odbiera pakiety danych w sieci. Gniazdo ma typ i jest skojarzona z uruchomionego procesu i może mieć nazwę. Obecnie sockets ogólnie wymiany danych z innych sockets, w tym samym "komunikacji domeny," który korzysta z zestawem protokołów internetowych.

Oba rodzaje gniazd jest dwukierunkowe; są one przepływów danych, które mogą być przekazywane w obu kierunkach jednocześnie (pełny dupleks).

Dostępne są dwa typy gniazda:

- Gniazda Stream

   Gniazda Stream zapewnienia przepływu danych, bez rekordów granic: strumień bajtów. Strumienie są gwarantowane dostarczanych i poprawnie sekwencjonowania i unduplicated.

- Do przesyłania datagramów

   Datagram sockets rekordu zorientowane na obsługę danych przepływ, który nie jest gwarantowane do dostarczenia i nie może być sekwencjonowania jako wysyłane lub unduplicated.

"Sekwencjonowania" oznacza, że pakiety są dostarczane w kolejności wysyłane. "Unduplicated" oznacza, że pobieranie określonego pakietu tylko raz.

> [!NOTE]
>  W obszarze niektóre protokoły sieciowe, takie jak XNS strumienie mogą być rekord obiektowo strumieni rekordów zamiast strumieni bajtów. W obszarze bardziej powszechne, protokół TCP/IP strumienie są jednak strumienie bajtów. Windows Sockets zapewnia poziom abstrakcji niezależne od podstawowych protokołów.

Aby uzyskać informacje o tych typach i jakiego rodzaju gniazda, aby użyć w sytuacji, w których, zobacz [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md) i [Windows Sockets: Do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md).

##  <a name="_core_the_socket_data_type"></a> Typ danych GNIAZDA

Każdy obiekt gniazda MFC hermetyzuje dojścia do obiektu Windows Sockets. Typ danych tego dojścia jest **GNIAZDA**. A **GNIAZDA** uchwyt jest odpowiednikiem `HWND` okna. Klasy gniazd MFC zapewniają operacje w dojściu do zhermetyzowanego.

**GNIAZDA** — typ danych jest szczegółowo opisane w zestawie Windows SDK. Zobacz "Gniazda typu danych i wartości błędów" w obszarze Windows Sockets.

##  <a name="_core_uses_for_sockets"></a> Zastosowań gniazda

Gniazda są bardzo przydatne w kontekstach co najmniej trzech komunikacji:

- Modele klient/serwer.

- Scenariusze peer-to-peer, np. aplikacji do obsługi komunikatów.

- Przez aplikację odbierającą interpretacji wiadomość jako wywołanie funkcji, dzięki czemu zdalnych wywołań procedur (RPC).

> [!TIP]
>  W idealnym rozwiązaniem w przypadku używanie gniazd MFC jest pisanego obu końcach komunikacji: używanie MFC na obu końcach. Aby uzyskać więcej informacji na ten temat, jak zarządzać w przypadku, gdy masz podczas komunikowania się z aplikacji innych niż MFC, w tym temacie [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).

Aby uzyskać więcej informacji, zobacz Windows Sockets specyfikacji: **ntohs**, **ntohl**, **htons**, **htonl**. Ponadto zobacz następujące tematy:

- [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
