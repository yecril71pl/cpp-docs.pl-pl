---
title: 'Windows Sockets: W tle | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 446719d9d37d2930e08dc66303fd2d952fd88820
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-background"></a>Windows Sockets: podstawy
W tym artykule opisano ujawnienia Windows Sockets. Artykuł również:  
  
-   [Definiuje termin "gniazda"](#_core_definition_of_a_socket).  
  
-   [Opisuje typ danych uchwytu GNIAZDA](#_core_the_socket_data_type).  
  
-   [Opis zastosowania sockets](#_core_uses_for_sockets).  
  
 Specyfikacja Windows Sockets definiuje interfejs programowania zgodnych binarnie sieci systemu Microsoft Windows. Windows Sockets opierają się na implementacji sockets UNIX w dystrybucji oprogramowania Berkeley (BSD, wersji 4.3) z University Kalifornijskiej w Berkeley. Specyfikacja zawiera procedury gniazda BSD stylu i rozszerzenia specyficznych dla systemu Windows. Przy użyciu usługi Windows Sockets zezwala aplikacjom komunikują się za pośrednictwem każdej sieci, który jest zgodny z interfejsem API Windows Sockets. Na Win32 Windows Sockets zapewnienia bezpieczeństwa wątków.  
  
 Wielu dostawców oprogramowania sieci obsługuje Windows Sockets w obszarze protokoły sieciowe łącznie TCP/IP Transmission Control Protocol/Internet Protocol (), Xerox sieci System (XNS), cyfrowe Corporation urządzeń sieci DECNet protokołu, Internet Novell Corporation Pakiet Exchange/Sequenced spakowane Exchange (IPX/SPX) i inne. Mimo że obecny specyfikacji Windows Sockets definiuje abstrakcję sockets TCP/IP, każdy protokół sieciowy zgodne z usługi Windows Sockets podając własną wersję biblioteki dołączanej (dynamicznie DLL), który implementuje Windows Sockets. Przykładami komercyjnych aplikacji napisanych z usługi Windows Sockets serwerów X Windows, emulatory terminalu i systemów poczty elektronicznej.  
  
> [!NOTE]
>  Windows Sockets ma na celu abstrakcyjnej odnośnej sieci, dzięki czemu nie trzeba mieć wiedzę o tej sieci w związku z czym aplikację można uruchomić na dowolnej sieci obsługującej gniazda. W związku z tym w tej dokumentacji nie omówiono w nim szczegóły protokołów sieciowych.  
  
 Biblioteka Microsoft Foundation Class (MFC) obsługuje programowania za pomocą interfejsu API systemu Windows Sockets podając dwóch klas. Jeden z tych klas, `CSocket`, zapewnia wysoki poziom abstrakcji do upraszczają programowanie komunikacji z sieci.  
  
 Windows Sockets specyfikację Windows Sockets: Otwórz interfejs sieci przetwarzania danych w obszarze systemu Microsoft Windows, teraz w wersji 1.1, został opracowany jako standard sieci otwarte przez dużą grupę użytkowników indywidualnych i firmy w społeczności TCP/IP i jest jest to dostępne bezpłatnie do użytku. Gniazda, w obecnie programowania modelu obsługuje jeden "komunikacji domeny", używając zestawem protokołów internetowych. Specyfikacja jest dostępne w zestawie Windows SDK.  
  
> [!TIP]
>  Ponieważ sockets korzystają z zestawem protokołów internetowych, są preferowane trasy dla aplikacji, które obsługują komunikację z Internetem na "autostrady informacji."  
  
##  <a name="_core_definition_of_a_socket"></a>Definicja gniazda  
 Gniazdo jest punkt końcowy komunikacji — obiekt, za pomocą którego aplikacji Windows Sockets wysyła i odbiera pakiety danych w sieci. Gniazda ma typ i są skojarzone z uruchomionego procesu i może mieć nazwę. Obecnie sockets zazwyczaj wymiany danych z innych sockets w tej samej"komunikacji," używający zestawem protokołów internetowych.  
  
 Oba rodzaje sockets są dwukierunkowych; są one przepływów danych, które mogą być przekazywane w obu kierunkach jednocześnie (pełny dupleks).  
  
 Dostępne są dwa typy gniazda:  
  
-   Gniazda strumieni  
  
     Gniazda strumieni podanie przepływu danych, bez rekordów granice: strumień bajtów. Strumienie są gwarancji dostarczenia i poprawnie sekwencjonowania i unduplicated.  
  
-   Gniazda do przesyłania datagramów  
  
     Przepływ danych obsługi zorientowane na rekordy sockets datagram, który nie jest gwarantowana dostarczanej i nie może być sekwencjonowania jako wysyłane lub unduplicated.  
  
 "Sekwencjonowania" oznacza, że pakiety są dostarczane w kolejności wysłane. "Unduplicated" oznacza, Pobierz pakiet określonego tylko raz.  
  
> [!NOTE]
>  W niektórych protokołów sieciowych, takich jak XNS strumienie można rekordu ukierunkowane jako strumienie rekordów zamiast strumienie bajtów. W obszarze częściej protokołu TCP/IP jednak strumienie są strumienie bajtów. Windows Sockets zapewnia poziom abstrakcji niezależne od podstawowej protokołu.  
  
 Aby uzyskać informacje o tych typach i jakiego rodzaju gniazda do używania w jakich sytuacjach, zobacz [Windows Sockets: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md) i [Windows Sockets: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md).  
  
##  <a name="_core_the_socket_data_type"></a>Typ danych GNIAZDA  
 Każdy obiekt MFC gniazda hermetyzuje uchwyt do obiektu Windows Sockets. Typ danych ta dojścia jest **GNIAZDA**. A **GNIAZDA** dojścia jest odpowiednikiem `HWND` okna. Klasy MFC gniazda Podaj operacje na hermetyzowany dojścia.  
  
 **GNIAZDA** — typ danych jest opisane szczegółowo w zestawie Windows SDK. Zobacz "Gniazda — typ danych i wartości błędów" w obszarze usługi Windows Sockets.  
  
##  <a name="_core_uses_for_sockets"></a>Używa dla gniazda  
 Gniazda są bardzo przydatne w kontekstach co najmniej trzy komunikacji:  
  
-   Modele klient/serwer.  
  
-   Scenariusze peer-to-peer, takich jak aplikacje do obsługi komunikatów.  
  
-   Tworzenie zdalnych wywołań procedur (RPC) przez aplikację odbierającą zinterpretować komunikatu jako wywołania funkcji.  
  
> [!TIP]
>  Jest idealne rozwiązanie w przypadku używanie gniazd MFC podczas pisania obu końców komunikacji: używanie MFC obu końców. Aby uzyskać więcej informacji na ten temat, łącznie ze sposobem zarządzanie w przypadku, gdy w przypadku komunikacji z aplikacjami innego typu niż MFC, zobacz [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).  
  
 Aby uzyskać więcej informacji, zobacz Specyfikacja systemu Windows Sockets: **ntohs**, **ntohl**, **htons**, **htonl**. Zobacz też poniższe tematy:  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: przykład gniazd korzystających z archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

