---
title: Opcje do wyboru przy projektowaniu aplikacji
ms.date: 11/04/2016
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
ms.openlocfilehash: cdb294e4ab808a7e4cbcec457f6e744eff9f12cb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302819"
---
# <a name="application-design-choices"></a>Opcje do wyboru przy projektowaniu aplikacji

W tym artykule omówiono niektóre zagadnienia do rozważenia podczas programowania dla sieci Internet.

Tematy omówione w tym artykule obejmują:

- [Intranet lub Internet](#_core_intranet_versus_internet)

- [Klienta lub serwera aplikacji](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [Przeglądarki lub aplikacji autonomicznej](#_core_browser_or_standalone)

- [COM w Internecie](#_core_com_on_the_internet)

- [Dane klienta Pobierz usługi](#_core_client_data_download_services)

Jeśli wszystko jest gotowe do rozpoczęcia pisania programu teraz, zobacz [pisanie aplikacji MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a> Intranet lub Internet

Wiele aplikacji, uruchom w Internecie i są dostępne dla wszystkich odbiorców za pomocą przeglądarki oraz dostęp do Internetu. Firmom także wdrażania rozwiązań intranetowych, które sieci firmowej za pomocą protokołów TCP/IP i przeglądarki sieci Web. Intranet oferują można łatwo rozbudować, centralnej źródłem informacji w całej firmie. Mogą one używane dla uaktualnienie oprogramowania, dostarczania i tabularyzacja ankiet, pomocy technicznej dla klienta i do dostarczania informacji. W poniższej tabeli porównano funkcje Internet i intranet.

|Internet|Intranet|
|--------------|--------------|
|Przy małej przepustowości|Wysoka przepustowość|
|Zmniejszenie bezpieczeństwa systemów i danych|Kontrolowany dostęp do danych i systemów|
|Minimalny kontrolę nad zawartością|Wysoka kontrolę nad zawartością|

##  <a name="_core_client_or_server_application"></a> Klienta lub serwera aplikacji

Aplikacja może działać na komputerze klienckim lub na komputerze serwera. Aplikacji może również przechowywane na serwerze i następnie pobrania w Internecie i uruchomienia na komputerze klienckim. Klas MFC WinInet służą aplikacjom klienckim do pobierania plików. MFC i moniker asynchronicznej klas są używane do pobierania plików i właściwości formantu. Klasy dla formantów ActiveX i dokumenty aktywne są używane dla aplikacji klienckich i aplikacji, które są pobierane z serwera w celu uruchomienia na komputerze klienckim.

##  <a name="_core_the_web_page"></a> Strona sieci Web: Kontrolki ActiveX HTML, dokumenty aktywne

Firma Microsoft oferuje kilka sposobów udostępniania zawartości na stronie sieci Web. Strony sieci Web można użyć standardowego kodu HTML lub HTML rozszerzeń, takich jak tag obiekt, aby zapewnić dynamicznej zawartości takiej jak kontrolki ActiveX.

Przeglądarki sieci Web wyświetlają zazwyczaj stron HTML. Dokumenty aktywne można również wyświetlić dane swojej aplikacji w prosty interfejs wskaż i kliknij w przeglądarce z możliwością korzystania z COM. Serwer aktywnego dokumentu wyświetlać dokumentem, pełną ramki w całego obszaru klienta, za pomocą menu i paski narzędzi.

Kontrolki ActiveX, którą piszesz można pobrane asynchronicznie z serwera i wyświetlać na stronie sieci Web. Język skryptów, takich jak VBScript można użyć do sprawdzenia poprawności po stronie klienta przed wysłaniem informacji do serwera.

##  <a name="_core_browser_or_standalone"></a> Przeglądarki lub aplikacji autonomicznej

Można napisać kontrolki ActiveX, które są osadzone w stronę HTML i serwery dokumentów aktywnych, które są wyświetlane w przeglądarce. Można napisać strony HTML, które zawierają przycisku, aby przesłać żądanie, aby uruchomić aplikację interfejsu ISAPI na serwerze sieci Web. Można napisać autonomiczna aplikacja, która korzysta z protokołów internetowych do pobierania plików i wyświetlenia informacji do użytkownika, bez kiedykolwiek za pomocą aplikacji przeglądarki.

##  <a name="_core_com_on_the_internet"></a> COM w Internecie

Kontrolki ActiveX, dokumenty aktywne i monikerów asynchronicznych wykorzystują technologie COM (Component Object Model).

Kontrolki ActiveX zapewniają dynamicznej zawartości do dokumentów i stron w witrynach internetowych. W modelu COM można tworzyć formanty ActiveX i pełnej ramki dla dokumentów za pomocą dokumenty aktywne.

Monikery asynchroniczne udostępnia funkcje umożliwiające formantu, który ma działać dobrze w środowisku Internet, w tym przyrostowych lub progresywnego oznacza, że można pobrać danych. Formanty musi również działać z innych formantów, które mogą również być pobierania ich dane asynchronicznie w tym samym czasie.

##  <a name="_core_client_data_download_services"></a> Dane klienta Pobierz usługi

Dwa zestawy interfejsów API, które ma na celu przeniesienia danych klienta są WinInet i monikerów asynchronicznych. Jeśli masz duży obraz GIF, plików AVI i formantów ActiveX na stronie HTML, można zwiększyć szybkość reakcji użytkownika, pobierając asynchronicznie, albo za pomocą monikerów asynchronicznych lub asynchronicznie przy użyciu interfejsu WinInet.

Typowe zadania w Internecie jest transfer danych. Jeśli już używasz Technologia Active (na przykład jeśli formant ActiveX), umożliwia monikerów asynchronicznych stopniowo Renderowanie danych, ponieważ pobiera on. WinInet służy do przesyłania danych za pomocą wspólnych protokołów internetowych, takich jak HTTP, FTP i gopher. Obie metody zapewniają niezależność protokołu i umożliwiają abstrakcyjne warstwy przy użyciu usługi WinSock i protokół TCP/IP. Można nadal używać [WinSock](../mfc/windows-sockets-in-mfc.md) bezpośrednio.

W poniższej tabeli przedstawiono kilka sposobów korzystania z biblioteki MFC do transferu danych za pośrednictwem Internetu.

|Użyj tego protokołu|W tych warunkach|Korzystanie z tych klas|
|-----------------------|----------------------------|-------------------------|
|[Internet pobierania za pomocą monikerów asynchronicznych](../mfc/asynchronous-monikers-on-the-internet.md)|Dla transferu asynchronicznego, korzystając z modelu COM, kontrolek ActiveX i protokołów internetowych.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Dla protokołów internetowych dla protokołu HTTP, FTP i gopher. Dane mogą być przenoszone synchronicznie lub asynchronicznie i są przechowywane w pamięci podręcznej całego systemu.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)i wiele innych.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Aby uzyskać maksymalną wydajność i kontroli. Wymaga zrozumienia sockets i protokołów TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Zobacz także

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikery asynchroniczne w Internecie](../mfc/asynchronous-monikers-on-the-internet.md)
