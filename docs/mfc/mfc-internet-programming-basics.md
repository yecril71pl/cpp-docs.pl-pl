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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366288"
---
# <a name="mfc-internet-programming-basics"></a>MFC — podstawy programowania Internetu

Firma Microsoft udostępnia wiele interfejsów API do programowania aplikacji klienckich i serwerowych. Wiele nowych aplikacji są zapisywane dla Internetu, a w miarę zmiany technologii, możliwości przeglądarki i opcji zabezpieczeń, nowe typy aplikacji zostaną napisane. Przeglądarki działają na komputerach klienckich, zapewniając dostęp do sieci World Wide Web i wyświetlając strony HTML zawierające tekst, grafikę, kontrolki ActiveX i dokumenty. Serwery zapewniają usługi FTP, HTTP i gopher oraz uruchamiają aplikacje rozszerzenia serwera przy użyciu CGI. Aplikacja niestandardowa może pobierać informacje i dostarczać dane w Internecie.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji, zobacz [ActiveX Controls](activex-controls.md).

![Aplikacje klienckie i serwerowe](../mfc/media/vc38bq1.gif "Aplikacje klienckie i serwerowe")

MFC zapewnia klasy, które obsługują programowanie internetowe. Do pisania formantów ActiveX i aktywnych dokumentów można używać [colecontrol](../mfc/reference/colecontrol-class.md) i [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) i powiązanych klas MFC. Do pobierania plików i informacji przy użyciu protokołów internetowych, takich jak FTP, HTTP i gopher, można używać klas MFC, takich jak [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md)i [CAsyncMonikerFile.](../mfc/reference/casyncmonikerfile-class.md)

## <a name="in-this-section"></a>W tej sekcji

- [Klasy MFC związane z Internetem](../mfc/internet-related-mfc-classes.md)

- [Informacje internetowe według tematów](../mfc/internet-information-by-topic.md)

- [Informacje internetowe według zadań](../mfc/internet-information-by-task.md)

- [Technologia Active w Internecie](../mfc/active-technology-on-the-internet.md)

- [Podstawy WinInet](../mfc/wininet-basics.md)

- [Podstawy HTML](../mfc/html-basics.md)

## <a name="related-sections"></a>Sekcje pokrewne

- [Kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md)

- [Monikery asynchroniczne w Internecie](../mfc/asynchronous-monikers-on-the-internet.md)

- [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)

- [Opcje do wyboru przy projektowaniu aplikacji](../mfc/application-design-choices.md)

- [Pisanie aplikacji MFC](../mfc/writing-mfc-applications.md)

- [Testowanie aplikacji internetowych](../mfc/testing-internet-applications.md)

- [Zabezpieczenia internetowe](../mfc/internet-security-cpp.md)

- [Obsługa ALT dla kontrolek DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Witryny sieci Web, aby uzyskać więcej informacji

Aby uzyskać dodatkowe informacje na temat technologii internetowej firmy Microsoft, zobacz witrynę sieci Web [Microsoft Developer Network (MSDN).](https://go.microsoft.com/fwlink/p/?linkid=56322) (Linki mogą ulec zmianie bez powiadomienia).

Ta witryna sieci Web dla deweloperów zawiera informacje na temat korzystania z narzędzi i technologii deweloperskich firmy Microsoft oraz najważniejsze historie dotyczące ostatnich i nadchodzących konferencji. Na tej stronie można przejść do wielu powiązanych witryn deweloperów, w tym .NET i XML Developer Centers. Można również pobrać zestawy SDK wersji beta i przykłady.

[Konsorcjum World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publikuje specyfikacje dotyczące technologii HTML, HTTP, CGI i innych technologii sieci World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Więcej Pomocy w Internecie

Sekcja OLE w programie Windows SDK zawiera dodatkowe informacje dotyczące programowania OLE. Te informacje zawierają szczegółowe informacje na temat korzystania z funkcji Win32 WinInet bezpośrednio, a nie za pośrednictwem klas MFC. Zawiera również informacje ogólne dotyczące technologii internetowych.
