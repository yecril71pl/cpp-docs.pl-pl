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
ms.openlocfilehash: b205599ed3bf33e84516120b1855482797b86c9b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924913"
---
# <a name="application-design-choices"></a>Opcje do wyboru przy projektowaniu aplikacji

W tym artykule omówiono niektóre zagadnienia dotyczące projektowania, które należy wziąć pod uwagę podczas programowania dla Internetu.

Tematy omówione w tym artykule obejmują:

- [Intranet a Internet](#_core_intranet_versus_internet)

- [Aplikacja klienta lub serwera](#_core_client_or_server_application)

- [Strona sieci Web](#_core_the_web_page)

- [Przeglądarka lub aplikacja autonomiczna](#_core_browser_or_standalone)

- [COM w Internecie](#_core_com_on_the_internet)

- [Usługi pobierania danych klienta](#_core_client_data_download_services)

Jeśli chcesz teraz zacząć pisać program, zobacz [pisanie aplikacji MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a>Intranet a Internet

Wiele aplikacji jest uruchomionych w Internecie i są dostępne dla wszystkich osób z przeglądarką i dostępem do Internetu. Firmy obsługują również intranety, które są sieciami firmowymi przy użyciu protokołów TCP/IP i przeglądarek sieci Web. Sieci intranet oferują łatwe do uaktualnienia centralne źródło informacji w całej firmie. Mogą one służyć do uaktualniania oprogramowania, do dostarczania i znajdowania ankiet, obsługi klienta oraz do dostarczania informacji. Poniższa tabela zawiera porównanie funkcji internetowych i intranetowych.

|Internet|Obsługując|
|--------------|--------------|
|Niska przepustowość|Wysoka przepustowość|
|Obniżone bezpieczeństwo danych i systemów|Kontrolowany dostęp do danych i systemów|
|Minimalna kontrola nad zawartością|Wysoka Kontrola zawartości|

##  <a name="_core_client_or_server_application"></a>Aplikacja klienta lub serwera

Aplikacja może działać na komputerze klienckim lub na komputerze serwera. Aplikacja może być również przechowywana na serwerze, a następnie pobrana przez Internet i uruchomiona na komputerze klienckim. Klasy interfejsu WinInet platformy MFC są używane do pobierania plików przez aplikacje klienckie. Klasy MFC i asynchroniczne monikery są używane do pobierania właściwości plików i kontrolek. Klasy formantów ActiveX i dokumentów aktywnych są używane w aplikacjach klienckich i dla aplikacji, które są pobierane z serwera do uruchomienia na kliencie.

##  <a name="_core_the_web_page"></a>Strona sieci Web: HTML, dokumenty aktywne, kontrolki ActiveX

Firma Microsoft oferuje kilka sposobów udostępniania zawartości na stronie sieci Web. Strony sieci Web mogą używać standardowych rozszerzeń HTML lub HTML, takich jak tag Object, w celu zapewnienia zawartości dynamicznej, takiej jak kontrolki ActiveX.

Przeglądarki sieci Web zwykle wyświetlają strony HTML. Aktywne dokumenty mogą również wyświetlać dane aplikacji w prostym interfejsie i kliknięcia przeglądarki z obsługą modelu COM. Twój aktywny serwer dokumentów może wyświetlić dokument, pełną ramkę w całym obszarze klienta z własnymi menu i paskami narzędzi.

Kontrolki ActiveX, które można napisać, można pobrać asynchronicznie z serwera i wyświetlić je na stronie sieci Web. Możesz użyć języka skryptowego, takiego jak VBScript, aby przeprowadzić walidację po stronie klienta przed wysłaniem informacji na serwer.

##  <a name="_core_browser_or_standalone"></a>Przeglądarka lub aplikacja autonomiczna

Można napisać kontrolki ActiveX osadzone na stronie HTML i na serwerach dokumentów aktywnych, które są wyświetlane w przeglądarce. Można napisać strony HTML zawierające przycisk, aby przesłać żądanie uruchomienia aplikacji ISAPI na serwerze sieci Web. Można napisać autonomiczną aplikację, która korzysta z protokołów internetowych do pobierania plików i wyświetlania informacji dla użytkownika, bez użycia aplikacji przeglądarki.

##  <a name="_core_com_on_the_internet"></a>COM w Internecie

Kontrolki ActiveX, aktywne dokumenty i monikery asynchroniczne używają technologii COM (Component Object Model).

Formanty ActiveX udostępniają zawartość dynamiczną do dokumentów i stron w witrynach internetowych. Dzięki modelowi COM można tworzyć kontrolki ActiveX i dokumenty pełnotekstowe przy użyciu dokumentów aktywnych.

Monikery asynchroniczne zapewniają funkcje, które umożliwiają kontrolowanie dobrze w środowisku internetowym, w tym przyrostowe lub stopniowe pobieranie danych. Kontrolki muszą również działać poprawnie z innymi kontrolkami, które mogą również jednocześnie pobierać dane w tym samym czasie.

##  <a name="_core_client_data_download_services"></a>Usługi pobierania danych klienta

Dwa zestawy interfejsów API, które ułatwiają przesyłanie danych do klienta, to między innymi monikery WinInet i asynchronicznych. Jeśli masz duże pliki GIF i AVI oraz kontrolki ActiveX na stronie HTML, możesz zwiększyć czas odpowiedzi dla użytkownika, pobierając asynchronicznie, używając asynchronicznych monikerów lub asynchronicznie przy użyciu interfejsu WinInet.

Typowym zadaniem w Internecie jest transfer danych. Jeśli korzystasz już z technologii Active (na przykład w przypadku kontrolki ActiveX), możesz użyć monikery asynchroniczne do progresywnego renderowania danych podczas pobierania. Za pomocą usługi WinInet można przesyłać dane przy użyciu popularnych protokołów internetowych, takich jak HTTP, FTP i gopher. Obie metody zapewniają niezależność protokołu i zapewniają warstwę abstrakcyjną do korzystania z protokołów WinSock i TCP/IP. Nadal możesz używać usługi [Winsock](../mfc/windows-sockets-in-mfc.md) bezpośrednio.

Poniższa tabela zawiera podsumowanie kilku sposobów używania MFC do przesyłania danych przez Internet.

|Użyj tego protokołu|W tych warunkach|Korzystanie z tych klas|
|-----------------------|----------------------------|-------------------------|
|[Pobieranie z Internetu przy użyciu monikerów asynchronicznych](../mfc/asynchronous-monikers-on-the-internet.md)|W przypadku transferu asynchronicznego przy użyciu modelu COM, kontrolek ActiveX i dowolnego protokołu internetowego.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Protokoły internetowe dla protokołów HTTP, FTP i gopher. Dane można przenosić synchronicznie lub asynchronicznie i są przechowywane w pamięci podręcznej na poziomie systemu.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)i wiele innych.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|W celu uzyskania maksymalnej wydajności i kontroli. Wymaga znajomości gniazd i protokołów TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Zobacz także

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikery asynchroniczne w Internecie](../mfc/asynchronous-monikers-on-the-internet.md)
