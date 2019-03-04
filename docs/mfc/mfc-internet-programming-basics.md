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
ms.openlocfilehash: 37fe5486d6d41ad182779a3a15b0aca3af51d04b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288444"
---
# <a name="mfc-internet-programming-basics"></a>MFC — podstawy programowania Internetu

Firma Microsoft udostępnia wiele interfejsów API do programowania aplikacji klienta i serwera. Wiele nowych aplikacji są zapisywane do korzystania z Internetu, a jako technologii, możliwości przeglądarki i zmień opcje zabezpieczeń będą zapisywane nowych typów aplikacji. Przeglądarki uruchamiane na komputerach klienckich, umożliwiając dostęp w sieci World Wide Web i wyświetlanie strony HTML, które zawierają tekst, grafikę, kontrolek ActiveX i dokumentów. Serwery usługi gopher, HTTP i FTP i uruchamiania aplikacji rozszerzenia serwera przy użyciu CGI. Twoją aplikacją niestandardową można pobrać informacji o i udostępniać dane w Internecie.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [formantów ActiveX](activex-controls.md).

![Aplikacje klienckie i serwerowe](../mfc/media/vc38bq1.gif "aplikacje klienckie i serwerowe")

Biblioteka MFC zawiera klasy, które obsługują Programowanie w Internecie. Możesz użyć [COleControl](../mfc/reference/colecontrol-class.md) i [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) i pokrewne klasy MFC do zapisania formantów ActiveX i dokumenty aktywne. Można użyć klas MFC, takich jak [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), i [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) do pobierania plików i informacji przy użyciu protokołów internetowych, takich jak FTP HTTP i gopher.

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

- [Obsługa ATL dla kontrolek DHTML](../atl/atl-support-for-dhtml-controls.md)

##  <a name="_core_web_sites_for_more_information"></a> Witryny sieci Web, aby uzyskać więcej informacji

Aby uzyskać dodatkowe informacje o technologii internetowych, zobacz [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) witryny sieci Web. (Linki mogą ulec zmianie bez powiadomienia).

Tę witrynę sieci Web dla deweloperów zawiera informacje na temat korzystania z narzędzi programistycznych firmy Microsoft i technologii i Najciekawsze o najnowsze i nadchodzących konferencji. Na tej stronie możesz przejść do wielu powiązane witryny dla deweloperów, łącznie z .NET i centra deweloperów XML. Można również pobrać zestawy SDK w wersji beta i przykłady.

[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publikuje specyfikacje dotyczące HTML, HTTP, CGI i inne technologie sieci World Wide Web.

##  <a name="_core_more_internet_help"></a> Więcej pomocy z Internetu

Sekcja OLE zestawu Windows SDK zawiera dodatkowe informacje na temat programowania OLE. Te informacje zawiera szczegółowe informacje o używaniu funkcji Win32 WinInet bezpośrednio, a nie przy użyciu klas MFC. Zawiera przegląd informacji dotyczących technologii internetowych.

## <a name="see-also"></a>Zobacz także
