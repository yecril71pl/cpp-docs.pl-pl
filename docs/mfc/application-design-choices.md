---
title: Opcje do wyboru przy projektowaniu aplikacji
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374629"
---
# <a name="application-design-choices"></a>Opcje do wyboru przy projektowaniu aplikacji

W tym artykule omówiono niektóre problemy z projektowaniem, które należy wziąć pod uwagę podczas programowania dla Internetu.

Tematy omówione w tym artykule obejmują:

- [Intranet a Internet](#_core_intranet_versus_internet)

- [Aplikacja klienta lub serwera](#_core_client_or_server_application)

- [Strona internetowa](#_core_the_web_page)

- [Przeglądarka lub aplikacja autonomiczna](#_core_browser_or_standalone)

- [COM w Internecie](#_core_com_on_the_internet)

- [Usługi pobierania danych klienta](#_core_client_data_download_services)

Jeśli chcesz teraz rozpocząć pisanie programu, zobacz [Pisanie aplikacji MFC](../mfc/writing-mfc-applications.md).

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet a Internet

Wiele aplikacji działa w Internecie i jest dostępnych dla każdego, kto ma dostęp do przeglądarki i Internetu. Firmy wdrażają również intranety, które są sieciami w całej firmie przy użyciu protokołów TCP/IP i przeglądarek sieci Web. Intranety oferują łatwe do rozbudowy, centralne źródło informacji dla całej firmy. Mogą być używane do uaktualniania oprogramowania, dostarczania i tworzenia raportów informacyjnych, obsługi klienta i dostarczania informacji. W poniższej tabeli porównano funkcje Internetu i intranetów.

|Internet|Intranet|
|--------------|--------------|
|Niska przepustowość|Wysoka przepustowość|
|Mniejsze bezpieczeństwo danych i systemów|Kontrolowany dostęp do danych i systemów|
|Minimalna kontrola treści|Wysoka kontrola treści|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>Aplikacja klienta lub serwera

Aplikacja może działać na komputerze klienckim lub na komputerze serwera. Aplikacja może być również przechowywana na serwerze, a następnie pobierana przez Internet i uruchamiana na komputerze klienckim. Klasy MFC WinInet są używane dla aplikacji klienckich do pobierania plików. Klasy MFC i asynchroniczne moniker są używane do pobierania plików i właściwości kontroli. Klasy formanty ActiveX i aktywne dokumenty są używane dla aplikacji klienckich i aplikacji, które są pobierane z serwera w celu uruchomienia na kliencie.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>Strona internetowa: HTML, Aktywne dokumenty, kontrolki ActiveX

Firma Microsoft oferuje kilka sposobów dostarczania zawartości na stronie sieci Web. Strony sieci Web mogą używać standardowych rozszerzeń HTML lub HTML, takich jak znacznik obiektu, w celu zapewnienia zawartości dynamicznej, takiej jak kontrolki ActiveX.

Przeglądarki internetowe zazwyczaj wyświetlają strony HTML. Aktywne dokumenty mogą również wyświetlać dane aplikacji w prostym interfejsie typu "wskaż i kliknij" przeglądarki obsługującej technologię COM. Serwer dokumentów aktywnych może wyświetlać dokument w pełnej ramce w całym obszarze klienta z własnymi menu i paskami narzędzi.

Formanty ActiveX, które piszesz, można pobrać asynchronicznie z serwera i wyświetlić na stronie sieci Web. Za pomocą języka skryptów, takiego jak VBScript, można przeprowadzić sprawdzanie poprawności po stronie klienta przed wysłaniem informacji do serwera.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>Przeglądarka lub aplikacja autonomiczna

Można zapisać formanty ActiveX osadzone na stronie HTML i aktywne serwery dokumentów wyświetlane w przeglądarce. Można napisać strony HTML zawierające przycisk, aby przesłać żądanie uruchomienia aplikacji ISAPI na serwerze sieci Web. Można napisać autonomiczną aplikację, która używa protokołów internetowych do pobierania plików i wyświetlania informacji użytkownikowi, bez konieczności korzystania z aplikacji przeglądarki.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>COM w Internecie

Formanty ActiveX, Aktywne dokumenty i monikery asynchroniczne używają technologii COM (Component Object Model).

Formanty ActiveX zapewniają dynamiczną zawartość dokumentów i stron w witrynach internetowych. Dzięki com, można tworzyć formanty ActiveX i pełnoklatkowych dokumentów przy użyciu aktywnych dokumentów.

Monikery asynchroniczne zapewniają funkcje umożliwiające kontrolę, aby dobrze działać w środowisku internetowym, w tym przyrostowe lub progresywne środki pobierania danych. Formanty muszą również działać dobrze z innymi formantami, które mogą również pobierać swoje dane asynchronicznie w tym samym czasie.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>Usługi pobierania danych klienta

Dwa zestawy interfejsów API, które pomogą przenieść dane do klienta są WinInet i asynchronicznych monikers. Jeśli na stronie HTML znajdują się duże pliki gif i .avi oraz formanty ActiveX, możesz zwiększyć czas reakcji użytkownika, pobierając asynchronicznie, używając asynchronicznych monikerów lub używając asynchronicznie WinInet.

Typowym zadaniem w Internecie jest przesyłanie danych. Jeśli używasz już technologii Active (na przykład, jeśli masz formant ActiveX), możesz użyć asynchronicznych monikerów do stopniowego renderowania danych podczas pobierania. Za pomocą usługi WinInet można przesyłać dane przy użyciu typowych protokołów internetowych, takich jak HTTP, FTP i gopher. Obie metody zapewniają niezależność protokołu i zapewniają warstwę abstrakcyjną do korzystania z WinSock i TCP/IP. Nadal można używać [WinSock](../mfc/windows-sockets-in-mfc.md) bezpośrednio.

W poniższej tabeli podsumowano kilka sposobów przesyłania danych przez Internet przy użyciu MFC.

|Użyj tego protokołu|W tych warunkach|Korzystanie z tych klas|
|-----------------------|----------------------------|-------------------------|
|[Pobieranie przez Internet za pomocą asynchronicznych monikerów](../mfc/asynchronous-monikers-on-the-internet.md)|Do transferu asynchronisty przy użyciu COM, ActiveX formantów i dowolnego protokołu internetowego.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|W przypadku protokołów internetowych dla protokołów HTTP, FTP i gopher. Dane mogą być przesyłane synchronicznie lub asynchronicznie i są przechowywane w pamięci podręcznej całego systemu.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md), i wiele innych.|
|[Winsock](../mfc/windows-sockets-in-mfc.md)|Dla maksymalnej wydajności i kontroli. Wymaga zrozumienia gniazd i protokołów TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikery asynchroniczne w Internecie](../mfc/asynchronous-monikers-on-the-internet.md)
