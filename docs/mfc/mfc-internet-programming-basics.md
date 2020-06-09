---
title: MFC — podstawy programowania Internetu
ms.date: 11/19/2018
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
ms.openlocfilehash: 3265bffb393eeff1d8a04a41357e2b138aa0ebf7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615574"
---
# <a name="mfc-internet-programming-basics"></a>MFC — podstawy programowania Internetu

Firma Microsoft udostępnia wiele interfejsów API do programowania aplikacji klienta i serwera. Wiele nowych aplikacji jest pisanych dla Internetu, a w miarę jak technologie, możliwości przeglądarki i zmiany opcji zabezpieczeń zostaną naniesione nowe typy aplikacji. Przeglądarki są uruchamiane na komputerach klienckich, zapewniają dostęp do World Wide Web i wyświetlania stron HTML, które zawierają tekst, grafikę, kontrolki ActiveX i dokumenty. Serwery zapewniają usługi FTP, HTTP i gopher oraz uruchamiają aplikacje rozszerzeń serwera przy użyciu interfejsu CGI. Aplikacja niestandardowa może pobrać informacje i udostępnić je w Internecie.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX](activex-controls.md).

![Aplikacje klienta i serwera](../mfc/media/vc38bq1.gif "Aplikacje klienta i serwera")

MFC zawiera klasy, które obsługują programowanie Internetu. Można użyć [COleControl](reference/colecontrol-class.md) i [CDocObjectServer](reference/cdocobjectserver-class.md) oraz powiązanych klas MFC do zapisywania formantów ActiveX i dokumentów aktywnych. Można użyć klas MFC, takich jak [CInternetSession](reference/cinternetsession-class.md), [CFtpConnection](reference/cftpconnection-class.md)i [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) , do pobierania plików i informacji przy użyciu protokołów internetowych, takich jak FTP, http i gopher.

## <a name="in-this-section"></a>W tej sekcji

- [Klasy MFC związane z Internetem](internet-related-mfc-classes.md)

- [Informacje internetowe według tematów](internet-information-by-topic.md)

- [Informacje internetowe według zadań](internet-information-by-task.md)

- [Technologia Active w Internecie](active-technology-on-the-internet.md)

- [Podstawy WinInet](wininet-basics.md)

- [Podstawy HTML](html-basics.md)

## <a name="related-sections"></a>Sekcje pokrewne

- [Kontrolki ActiveX w Internecie](activex-controls-on-the-internet.md)

- [Monikery asynchroniczne w Internecie](asynchronous-monikers-on-the-internet.md)

- [Rozszerzenia internetowe Win32 (WinInet)](win32-internet-extensions-wininet.md)

- [MFC — zadania związane z programowaniem Internetu](mfc-internet-programming-tasks.md)

- [Opcje do wyboru przy projektowaniu aplikacji](application-design-choices.md)

- [Pisanie aplikacji MFC](writing-mfc-applications.md)

- [Testowanie aplikacji internetowych](testing-internet-applications.md)

- [Zabezpieczenia internetowe](internet-security-cpp.md)

- [Obsługa ALT dla kontrolek DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Witryny sieci Web, aby uzyskać więcej informacji

Aby uzyskać dodatkowe informacje na temat technologii Internet firmy Microsoft, zobacz witrynę sieci Web [Microsoft Developer Network (MSDN)](https://go.microsoft.com/fwlink/p/?linkid=56322) . (Linki mogą ulec zmianie bez powiadomienia).

Ta witryna sieci Web dla deweloperów zawiera informacje na temat korzystania z narzędzi i technologii programistycznych firmy Microsoft oraz najważniejszych scenariuszy dotyczących najnowszych i nadchodzących konferencji. Na tej stronie możesz przejść do wielu powiązanych witryn deweloperskich, takich jak .NET i Centra deweloperów XML. Możesz również pobrać zestawy SDK i przykłady dla wersji beta.

[Organizacja World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publikuje specyfikacje dla języka HTML, http, CGI i innych technologii World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Więcej pomocy internetowej

Sekcja OLE Windows SDK zawiera dodatkowe informacje na temat programowania OLE. Informacje te zawierają szczegółowe informacje o używaniu funkcji Win32 WinInet bezpośrednio, a nie za pośrednictwem klas MFC. Zawiera również przegląd informacji o technologiach internetowych.
