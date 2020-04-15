---
title: Podstawy WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367324"
---
# <a name="wininet-basics"></a>Podstawy WinInet

Za pomocą usługi WinInet można dodać obsługę protokołu FTP do pobierania i przekazywania plików z poziomu aplikacji. Można zastąpić [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) i użyć parametru *dwContext,* aby zapewnić użytkownikom informacje o postępie podczas wyszukiwania i pobierania plików.

Ten artykuł zawiera następujące tematy:

- [Tworzenie bardzo prostej przeglądarki](#_core_create_a_very_simple_browser)

- [Pobieranie strony sieci Web](#_core_download_a_web_page)

- [FTP plik](#_core_ftp_a_file)

- [Pobieranie katalogu Gopher](#_core_retrieve_a_gopher_directory)

- [Wyświetlanie informacji o postępie podczas przesyłania plików](#_core_display_progress_information_while_transferring_files)

Poniższe fragmenty kodu pokazują, jak utworzyć prostą przeglądarkę, pobrać stronę sieci Web, plik FTP i wyszukać plik gopher. Nie są one przeznaczone jako kompletne przykłady i nie wszystkie zawierają obsługę wyjątków.

Aby uzyskać dodatkowe informacje na temat wininet, zobacz [Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>Tworzenie bardzo prostej przeglądarki

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>Pobieranie strony sieci Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP plik

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>Pobieranie katalogu Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Użyj OnStatusCallback

Podczas korzystania z WinInet klasy, można użyć [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) członka obiektu [CInternetSession](../mfc/reference/cinternetsession-class.md) aplikacji do pobierania informacji o stanie. Jeśli wyprowadzisz własny `CInternetSession` obiekt, zastąpisz `OnStatusCallback`i włączysz wywołania zwrotne `OnStatusCallback` stanu, MFC wywoła funkcję z informacjami o postępie o całej aktywności w tej sesji internetowej.

Ponieważ pojedyncza sesja może obsługiwać kilka połączeń (które w ciągu `OnStatusCallback` ich istnienia mogą wykonywać wiele różnych operacji), wymaga mechanizmu do identyfikowania każdej zmiany stanu za pomocą określonego połączenia lub transakcji. Mechanizm ten jest dostarczany przez parametr identyfikatora kontekstu podane do wielu funkcji członkowskich w klasach pomocy technicznej WinInet. Ten parametr jest zawsze typu **DWORD** i zawsze nosi nazwę *dwContext*.

Kontekst przypisany do określonego obiektu internetowego jest używany tylko do `OnStatusCallback` identyfikowania działania, które obiekt powoduje w członówka `CInternetSession` obiektu. Wywołanie `OnStatusCallback` odbiera kilka parametrów; te parametry współpracują ze sobą, aby poinformować aplikację, jakie postępy zostały dokonane dla transakcji i połączenia.

Podczas tworzenia `CInternetSession` obiektu, można określić *dwContext* parametr do konstruktora. `CInternetSession`sam nie używa identyfikatora kontekstu; Zamiast tego przekazuje identyfikator kontekstu do dowolnego **InternetConnection**-pochodne obiekty, które jawnie nie uzyskać identyfikator kontekstu własnych. Z kolei `CInternetConnection` te obiekty przekażą identyfikator `CInternetFile` kontekstu wraz z obiektami, które tworzą, jeśli nie zostanie jawnie określony inny identyfikator kontekstu. Jeśli z drugiej strony, należy określić określony identyfikator kontekstu własnego, obiekt i wszelkie prace, które wykonuje będą skojarzone z tym identyfikatorem kontekstu. Identyfikatory kontekstu można użyć do określenia, jakie informacje o `OnStatusCallback` stanie są podane w funkcji.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>Wyświetlanie informacji o postępie podczas przesyłania plików

Na przykład, jeśli piszesz aplikację, która tworzy połączenie z serwerem FTP, aby odczytać plik, a także łączy `CInternetSession` się `CInternetConnection` z serwerem HTTP, aby uzyskać stronę sieci Web, będziesz miał obiekt, dwa obiekty (jeden będzie `CFtpSession` `CHttpSession`a), a drugi będzie ) i dwa `CInternetFile` obiekty (po jednym dla każdego połączenia). Jeśli użyto wartości domyślnych dla parametrów *dwContext,* nie `OnStatusCallback` można odróżnić wywołań wskazujących postęp połączenia FTP i wywołań wskazujących postęp połączenia HTTP. Jeśli określisz *dwContext* ID, który można `OnStatusCallback`później przetestować w , będzie wiesz, która operacja wygenerowała wywołanie zwrotne.

## <a name="see-also"></a>Zobacz też

[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
