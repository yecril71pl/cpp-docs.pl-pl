---
title: Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 356027e151dcc94891b9c4043e4f1af8b2f0b947
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430920"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych

Rozszerzenia internetowe Win32 lub WinInet, zapewniają dostęp do wspólnych protokołów internetowych, w tym gopher, FTP i HTTP. Za pomocą interfejsu WinInet, można napisać klienckich aplikacji internetowych na wyższym poziomie programowania, bez konieczności WinSock, TCP/IP lub szczegółowe informacje o określonych protokołów internetowych. WinInet udostępnia spójny zestaw funkcji dla wszystkich trzech protokołów, za pomocą znajomego interfejsu Win32 API. Ten spójności minimalizuje zmian w kodzie, który należy upewnić się, jeśli podstawowym protokole zmieni się (na przykład z FTP, HTTP).

Visual C++ zapewnia dwa sposoby, aby używać interfejsu WinInet. Można bezpośrednio wywoływać funkcje internetowe Win32 (patrz dokumentacja OLE w zestawie Windows SDK, aby uzyskać więcej informacji) lub użyć WinInet za pośrednictwem [klas MFC WinInet](../mfc/mfc-classes-for-creating-internet-client-applications.md).

**Możesz użyć interfejsu WinInet do:**

- Pobierz stron HTML.

     Protokół HTTP jest protokół używany do przesyłania strony HTML z serwera do przeglądarki klienta.

- Wysyłanie żądań FTP do przekazywania lub pobierania plików lub uzyskaj listach zawartości katalogów.

     Typowe żądanie jest logowanie anonimowe, aby pobrać plik.

- System menu gopher firmy może być używany do uzyskiwania dostępu do zasobów w Internecie.

     Elementy menu może być kilka typów, w tym inne menu, indeksowanych bazy danych, które można przeszukiwać, grup dyskusyjnych lub pliku.

Wszystkie trzy protokoły nawiązać połączenie, wysyłać żądania do serwera i zamknij połączenie.

**Klas MFC WinInet ułatwiają:**

- Równie łatwo, jak odczytywanie plików z dysku twardego odczytu informacji z serwerami HTTP, FTP i gopher.

- Możesz używać protokołów HTTP, FTP i gopher bez programowania bezpośrednio do usługi WinSock lub protokołu TCP/IP.

     Deweloperzy korzystający z funkcji Win32 Internet jest konieczne należy zapoznać się z TCP/IP lub Windows Sockets. Można nadal programować na poziomie gniazda przy użyciu protokołów WinSock i protokół TCP/IP bezpośrednio, ale jest teraz jeszcze łatwiej jest używać klas MFC WinInet dostępu HTTP, FTP i protokołów gopher w Internecie. Wiele typowych operacji deweloperzy nie muszą poznać szczegóły określonego protokołu, którego używają.

Wiele operacji, które mogą być wykonywane przez komputer jako klienta na inne komputery w Internecie może zająć dużo czasu. Szybkość tych operacji zwykle jest ograniczona przez szybkość połączenia sieciowego, ale ich może mieć wpływ również przez innego ruchu sieciowego i złożoności wykonać operację. Na przykład nawiązywanie zdalnego serwera FTP wymaga, że na komputerze najpierw sprawdzić nazwę tego serwera, aby znaleźć jej adres. Aplikacja spróbuje połączyć się z serwerem pod tym adresem. Po otwarciu połączenia komputer i serwer zdalny zainicjuje konwersację z protokół transferu plików przed połączenie faktycznie służy do pobierania plików.

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Jak MFC ułatwia tworzenie klienckich aplikacji internetowych](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

