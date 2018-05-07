---
title: Opcje projektowania aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76a49d2ecfc79e35da55d1393cf3880b15fba7d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="application-design-choices"></a>Opcje do wyboru przy projektowaniu aplikacji
W tym artykule omówiono niektóre zagadnienia, które należy uwzględnić podczas programowania dla Internetu.  
  
 Omówione w tym artykule tematy obejmują:  
  
-   [Intranet lub Internet](#_core_intranet_versus_internet)  
  
-   [Klienta lub serwera aplikacji](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [Przeglądarki lub aplikacji autonomicznej](#_core_browser_or_standalone)  
  
-   [COM w Internecie](#_core_com_on_the_internet)  
  
-   [Dane klienta pobrać usług](#_core_client_data_download_services)  
  
 Gdy wszystko będzie gotowe rozpocząć pisanie programu teraz, zobacz [pisanie aplikacji MFC](../mfc/writing-mfc-applications.md).  
  
##  <a name="_core_intranet_versus_internet"></a> Intranet lub Internet  
 Wiele aplikacji Uruchom w Internecie i są dostępne dla wszystkich osób z przeglądarki i dostęp do Internetu. Firm również wdrażania rozwiązań intranetowych, które są sieci firmowej za pomocą protokołów TCP/IP i przeglądarki sieci Web. Intranet oferują można łatwo rozbudować, centralnej źródłem informacji o firmie. Mogą one używane do uaktualniania oprogramowania, do dostarczania i tabularyzacja ankiet obsługi klienta i w celu dostarczania informacji. W poniższej tabeli porównano funkcje sieci intranet i Internet.  
  
|Internet|Intranet|  
|--------------|--------------|  
|O niskiej przepustowości|Wysoka przepustowość|  
|Zmniejszenie bezpieczeństwa systemów i danych|Kontrolowany dostęp do danych i systemów|  
|Minimalny kontroli zawartości|Wysoka kontroli zawartości|  
  
##  <a name="_core_client_or_server_application"></a> Klienta lub serwera aplikacji  
 Aplikacja może działać na komputerze klienckim lub na komputerze serwera. Aplikacja może również być przechowywane na serwerze, pobrane przez Internet i uruchom na komputerze klienckim. Klasy MFC WinInet są używane dla aplikacji klienckich, do pobierania plików. MFC i asynchroniczne krótkiej nazwy klas są używane do pobierania plików i właściwości formantu. Klasy dla formantów ActiveX i dokumenty aktywne są używane dla aplikacji klienckich i aplikacji, które zostaną pobrane z serwera do uruchomienia na komputerze klienckim.  
  
##  <a name="_core_the_web_page"></a> Strony sieci Web: Formanty ActiveX HTML, dokumentów aktywnych  
 Firma Microsoft oferuje kilka sposobów udostępniania zawartości na stronie sieci Web. Strony sieci Web można używać standardowych HTML lub HTML rozszerzenia, takie jak tag object w celu zapewnienia dynamicznej zawartości takiej jak kontrolki ActiveX.  
  
 Przeglądarki sieci Web zwykle wyświetlenia strony HTML. Dokumenty aktywne można także wyświetlić dane aplikacji w prosty interfejs punktu i kliknij przeglądarki z obsługą COM. Serwer dokumentów aktywnych można wyświetlić dokumentem, pełny ramki, w obszarze klienckim z menu i pasków narzędzi.  
  
 Kontrolki ActiveX, jaki można pobrane asynchronicznie z serwera i wyświetlane na stronie sieci Web. Język skryptów, takich jak VBScript służy do sprawdzania poprawności po stronie klienta przed wysłaniem informacji do serwera.  
  
##  <a name="_core_browser_or_standalone"></a> Przeglądarki lub aplikacji autonomicznej  
 Można napisać formantów ActiveX, które są osadzone w strony HTML i serwery dokumentów aktywnych, które są wyświetlane w przeglądarce. Można napisać strony HTML, które zawierają przycisk, aby przesłać żądanie do uruchamiania aplikacji ISAPI na serwerze sieci Web. Można zapisać autonomiczna aplikacja, która używa protokołów internetowych do pobierania plików i wyświetlenia informacji do użytkownika, bez kiedykolwiek przy użyciu aplikacji przeglądarki.  
  
##  <a name="_core_com_on_the_internet"></a> COM w Internecie  
 Kontrolki ActiveX, Active dokumentów i monikerów asynchronicznych używać technologii COM (Component Object Model).  
  
 Kontrolki ActiveX Podaj zawartość dynamiczną do dokumentów i stron w witrynach internetowych. W modelu COM można tworzyć formantów ActiveX i pełny ramki dokumentów za pomocą dokumentów aktywnych.  
  
 Monikery asynchroniczne udostępnia funkcje umożliwiające formantu do wykonania również w środowisku sieci Internet, w tym przyrostowe lub progresywnego oznacza, że do pobierania danych. Formanty musi działać prawidłowo w przypadku innych kontrolek, które mogą również być pobierania ich danych asynchronicznie w tym samym czasie.  
  
##  <a name="_core_client_data_download_services"></a> Dane klienta pobrać usług  
 Dwa zestawy interfejsów API, które pomogą transferu danych do klienta są WinInet i monikerów asynchronicznych. Jeśli masz dużą .gif i pliki AVI formantów na stronie HTML, pobierając asynchronicznie, monikery asynchroniczne lub asynchronicznie przy użyciu interfejsu WinInet można zwiększyć czas odpowiedzi dla użytkownika.  
  
 Typowe zadania w Internecie jest transferu danych. Jeśli już korzystasz z technologii Active (na przykład, jeśli formant ActiveX), można użyć monikery asynchroniczne stopniowo Renderowanie danych zgodnie z jego pliki do pobrania. Wininet — służy do przesyłania danych za pomocą wspólnych protokołów internetowych, takich jak HTTP, FTP i gopher. Obie metody Podaj niezależność protokołu i zapewnić warstwę abstrakcyjny przy użyciu WinSock i protokołu TCP/IP. Można nadal używać [WinSock](../mfc/windows-sockets-in-mfc.md) bezpośrednio.  
  
 W poniższej tabeli przedstawiono kilka sposobów użycia MFC do transferu danych za pośrednictwem Internetu.  
  
|Użyj tego protokołu|W tych warunkach|Korzystanie z tych klas|  
|-----------------------|----------------------------|-------------------------|  
|[Internet pobierania za pomocą monikery asynchroniczne](../mfc/asynchronous-monikers-on-the-internet.md)|Dla transferu asynchronicznego przy użyciu modelu COM, formantów ActiveX i protokołów internetowych.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Dla protokołów HTTP, FTP i gopher. Dane mogą być przenoszone synchronicznie lub asynchronicznie i są przechowywane w pamięci podręcznej całego systemu.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)i o wiele więcej.|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Maksymalnej wydajności i kontroli. Wymaga zrozumienia sockets i protokołów TCP/IP.|[CSocket —](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)   
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Monikery asynchroniczne w Internecie](../mfc/asynchronous-monikers-on-the-internet.md)

