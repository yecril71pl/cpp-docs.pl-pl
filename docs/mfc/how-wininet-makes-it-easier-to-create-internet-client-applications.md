---
title: Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 54f63da7451dfef39a33e6b437be938cb1652326
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624573"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych

Rozszerzenia internetowe Win32 lub WinInet zapewniają dostęp do typowych protokołów internetowych, w tym gopher, FTP i HTTP. Za pomocą usługi WinInet można pisać internetowe aplikacje klienckie na wyższym poziomie programowania, bez konieczności korzystania z protokołu WinSock, TCP/IP lub szczegółów określonych protokołów internetowych. Interfejs WinInet zapewnia spójny zestaw funkcji dla wszystkich trzech protokołów przy użyciu znanego interfejsu Win32 API. Ta spójność minimalizuje zmiany w kodzie, które należy wprowadzić w przypadku zmiany podstawowego protokołu (na przykład z protokołu FTP do protokołu HTTP).

Visual C++ zapewnia dwa sposoby korzystania z usługi WinInet. Możesz wywoływać funkcje internetowe Win32 bezpośrednio (zobacz dokumentację OLE w Windows SDK, aby uzyskać więcej informacji) lub użyć usługi WinInet za pośrednictwem [klas MFC WinInet](mfc-classes-for-creating-internet-client-applications.md).

**Za pomocą interfejsu WinInet można:**

- Pobierz strony HTML.

   HTTP to protokół używany do transferowania stron HTML z serwera do przeglądarki klienta.

- Wysyłaj żądania FTP w celu przekazywania lub pobierania plików albo uzyskiwania list katalogów.

   Typowym żądaniem jest Logowanie anonimowe, aby pobrać plik.

- Używanie systemu menu usługi gopher do uzyskiwania dostępu do zasobów w Internecie.

   Elementy menu mogą być kilka typów, w tym inne menu, indeksowana baza danych, która umożliwia wyszukiwanie, grupę dyskusyjną lub plik.

Dla wszystkich trzech protokołów nawiązywane jest połączenie, wykonywanie żądań do serwera i zamykanie połączenia.

**Klasy MFC WinInet ułatwiają:**

- Odczytaj informacje z serwerów HTTP, FTP i gopher jak łatwo odczytywanie plików z dysku twardego.

- Używaj protokołów HTTP, FTP i gopher bez programowania bezpośrednio w interfejsie WinSock lub TCP/IP.

   Deweloperzy korzystający z funkcji internetowych Win32 nie muszą znać protokołów TCP/IP ani Windows Sockets. Nadal można programować na poziomie gniazda przy użyciu protokołów WinSock i TCP/IP, ale jeszcze łatwiej jest używać klas MFC WinInet do uzyskiwania dostępu do protokołów HTTP, FTP i gopher przez Internet. W przypadku wielu typowych operacji deweloperzy nie muszą znać szczegółowych informacji o konkretnym używanym protokole.

Wiele operacji, które mogą być wykonywane przez komputer, jako klient do innych komputerów w Internecie, może zająć dużo czasu. Szybkość tych operacji jest zwykle ograniczona przez szybkość połączenia sieciowego, ale może również mieć wpływ na ruch sieciowy i złożoność operacji. Na przykład połączenie ze zdalnym serwerem FTP wymaga, aby komputer najpierw wyszukał nazwę tego serwera w celu znalezienia jego adresu. Aplikacja podejmie następnie próbę nawiązania połączenia z serwerem o tym adresie. Po otwarciu połączenia komputer i serwer zdalny inicjują konwersację z protokołem transferu plików, zanim będzie można w rzeczywistości używać połączenia do pobierania plików.

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Jak MFC ułatwia tworzenie klienckich aplikacji internetowych](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
