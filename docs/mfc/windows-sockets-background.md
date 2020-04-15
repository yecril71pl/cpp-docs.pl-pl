---
title: 'Windows Sockets: podstawy'
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
ms.openlocfilehash: 1c4a6dc6740660d1097785578cdac355983cad18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360125"
---
# <a name="windows-sockets-background"></a>Windows Sockets: podstawy

W tym artykule wyjaśniono charakter i przeznaczenie gniazd systemu Windows. Artykuł również:

- [Definiuje termin "gniazdo"](#_core_definition_of_a_socket).

- [Zawiera opis typu danych uchwytu SOCKET](#_core_the_socket_data_type).

- [W tym artykule opisano zastosowania gniazd](#_core_uses_for_sockets).

Specyfikacja windows sockets definiuje interfejs programowania sieciowego zgodny z binarnym dla systemu Microsoft Windows. Gniazda systemu Windows są oparte na implementacji gniazd UNIX w berkeley Software Distribution (BSD, release 4.3) z Uniwersytetu Kalifornijskiego w Berkeley. Specyfikacja obejmuje zarówno procedury gniazd w stylu BSD, jak i rozszerzenia specyficzne dla systemu Windows. Korzystanie z gniazda systemu Windows umożliwia aplikacji komunikowanie się w dowolnej sieci, która jest zgodna z interfejsem API windows sockets. W systemie Win32 gniazda systemu Windows zapewniają bezpieczeństwo wątków.

Wielu dostawców oprogramowania sieciowego obsługuje gniazda systemu Windows w ramach protokołów sieciowych, w tym protokołu TCP/IP (Transmission Control Protocol/Internet Protocol), Xerox Network System (XNS), protokołu DECNet firmy Digital Equipment Corporation, internetowej wymiany pakietów novell corporation/sekwencjonowej wymiany pakietów (IPX/SPX) i innych. Chociaż obecna specyfikacja sockets systemu Windows definiuje abstrakcję gniazd dla protokołu TCP/IP, każdy protokół sieciowy może być zgodny z gniazdami systemu Windows, dostarczając własną wersję biblioteki dynamicznego łącza (DLL), która implementuje gniazda systemu Windows. Przykłady aplikacji komercyjnych napisanych za pomocą gniazd systemu Windows obejmują serwery X Windows, emulatory terminali i systemy poczty elektronicznej.

> [!NOTE]
> Celem windows sockets jest wyodrębnienie sieci podstawowej, dzięki czemu nie trzeba mieć wiedzę na temat tej sieci i tak aplikacja może działać w dowolnej sieci, która obsługuje gniazda. W związku z tym w tej dokumentacji nie omawia szczegółów protokołów sieciowych.

Biblioteka klas Microsoft Foundation (MFC) obsługuje programowanie za pomocą interfejsu API windows sockets, dostarczając dwie klasy. Jedna z tych `CSocket`klas, zapewnia wysoki poziom abstrakcji, aby uprościć programowanie komunikacji sieciowej.

Specyfikacja Windows Sockets, Windows Sockets: Otwarty interfejs do przetwarzania sieciowego w systemie Microsoft Windows, teraz w wersji 1.1, został opracowany jako otwarty standard sieciowy przez dużą grupę osób i korporacji w społeczności TCP / IP i jest swobodnie dostępny do użytku. Model programowania gniazd obsługuje obecnie jedną "domenę komunikacyjną" przy użyciu pakietu Internet Protocol Suite. Specyfikacja jest dostępna w usłudze Windows SDK.

> [!TIP]
> Ponieważ gniazda korzystają z pakietu Internet Protocol Suite, są preferowaną trasą dla aplikacji obsługujących komunikację internetową na "autostradzie informacyjnej".

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a>Definicja gniazda

Gniazdo jest punktem końcowym komunikacji — obiektem, za pośrednictwem którego aplikacja Windows Sockets wysyła lub odbiera pakiety danych w sieci. Gniazdo ma typ i jest skojarzone z uruchomionym procesem i może mieć nazwę. Obecnie gniazda zazwyczaj wymieniają dane tylko z innymi gniazdami w tej samej "domenie komunikacyjnej", która korzysta z pakietu Internet Protocol Suite.

Oba rodzaje gniazd są dwukierunkowe; są to przepływy danych, które mogą być przekazywane w obu kierunkach jednocześnie (pełny dupleks).

Dostępne są dwa typy gniazd:

- gniazda strumieni

   Gniazda strumienia zapewniają przepływ danych bez granic rekordu: strumień bajtów. Strumienie są gwarantowane do dostarczenia i być poprawnie sekwencjonowane i unduplicated.

- gniazda do przesyłania datagramów

   Gniazda Datagram obsługują przepływ danych zorientowany na rekord, który nie jest gwarantowany do dostarczenia i nie może być sekwencjonowany jako wysłany lub nienaplikowany.

"Sekwencjonowane" oznacza, że pakiety są dostarczane w wysyłanej kolejności. "Nienaplikowane" oznacza, że otrzymujesz konkretny pakiet tylko raz.

> [!NOTE]
> W niektórych protokołach sieciowych, takich jak XNS, strumienie mogą być zorientowane na rekordy, jako strumienie rekordów, a nie strumienie bajtów. Jednak w ramach bardziej powszechnego protokołu TCP/IP strumienie są strumieniami bajtów. Windows Sockets zapewnia poziom abstrakcji niezależnie od protokołu źródłowego.

Aby uzyskać informacje na temat tych typów i rodzaju gniazda do użycia w jakich sytuacjach, zobacz [Gniazda systemu Windows: Gniazda strumienia](../mfc/windows-sockets-stream-sockets.md) i [Gniazda systemu Windows: Gniazda Datagram](../mfc/windows-sockets-datagram-sockets.md).

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a>Typ danych GNIAZDA

Każdy obiekt gniazda MFC hermetyzuje dojście do obiektu Windows Sockets. Typ danych tego uchwytu to **SOCKET**. Uchwyt **socket** jest analogiczna `HWND` do dla okna. Klasy gniazda MFC zapewniają operacje na zhermetyzowany dojście.

Typ danych **SOCKET** jest szczegółowo opisany w zestaw Windows SDK. Zobacz "Typ danych gniazda i wartości błędów" w obszarze Gniazda systemu Windows.

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a>Zastosowania do gniazd

Gniazda są bardzo przydatne w co najmniej trzech kontekstach komunikacyjnych:

- Modele klient/serwer.

- Scenariusze peer-to-peer, takie jak aplikacje do obsługi wiadomości.

- Wykonywanie zdalnych wywołań procedury (RPC) przez aplikację odbierającą interpretować komunikat jako wywołanie funkcji.

> [!TIP]
> Idealnym przypadkiem przy użyciu gniazd MFC jest podczas pisania obu końcach komunikacji: przy użyciu MFC na obu końcach. Aby uzyskać więcej informacji na ten temat, w tym jak zarządzać sprawą podczas komunikowania się z aplikacjami innych niż MFC, zobacz [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

Aby uzyskać więcej informacji, zobacz Windows Sockets Specyfikacja: **ntohs**, **ntohl**, **htons**, **htonl**. Zobacz też następujące tematy:

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
