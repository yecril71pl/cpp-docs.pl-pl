---
title: Podstawy WinInet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ca2eab519cdfa3140d40adfd83070976dcc965
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435652"
---
# <a name="wininet-basics"></a>Podstawy WinInet

Aby dodać obsługę FTP do pobierania i przekazywania plików z poziomu aplikacji, można użyć interfejsu WinInet. Można zastąpić [onstatuscallback —](../mfc/reference/cinternetsession-class.md#onstatuscallback) i użyj *dwContext* parametru, aby zapewnić informacje o postępie do użytkowników, jak wyszukiwanie i pobieranie plików.

Ten artykuł zawiera następujące tematy:

- [Utwórz bardzo prosty przeglądarki](#_core_create_a_very_simple_browser)

- [Pobierz strony sieci Web](#_core_download_a_web_page)

- [FTP pliku](#_core_ftp_a_file)

- [Pobieranie katalogu Gopher](#_core_retrieve_a_gopher_directory)

- [Wyświetl informacje o postępie podczas transferu plików](#_core_display_progress_information_while_transferring_files)

Fragmenty kodu poniżej pokazują, jak utworzyć proste przeglądarki, pobierania strony sieci Web, FTP pliku i poszukaj pliku gopher. Nie są one należy traktować jako kompletne przykłady, a nie wszystkie zawierać obsługę wyjątków.

Aby uzyskać dodatkowe informacje na temat interfejsu WinInet, zobacz [rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md).

##  <a name="_core_create_a_very_simple_browser"></a> Utwórz bardzo prosty przeglądarki

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> Pobierz strony sieci Web

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> FTP pliku

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> Pobieranie katalogu Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Onstatuscallback — użycie

Podczas używania klas WinInet, można użyć [onstatuscallback —](../mfc/reference/cinternetsession-class.md#onstatuscallback) członkiem aplikacji [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu do pobrania informacji o stanie. Przypadku klasy wyprowadzonej własne `CInternetSession` obiektów, Zastąp `OnStatusCallback`i Włącz wywołania zwrotne stanu, wywoła MFC swoje `OnStatusCallback` funkcja informacje o postępie o wszystkich działań w ramach tej sesji Internet.

Ponieważ w jednej sesji może obsługiwać wiele połączeń, (które przez cały okres ich istnienia, mogą wykonywać wiele różnych operacji distinct), `OnStatusCallback` musi mechanizm do identyfikowania każda zmiana stanu z określonego połączenia lub transakcji. Ten mechanizm jest zapewniana przez parametr identyfikator kontekstu do wielu funkcji składowych w klasach WinInet pomocy technicznej. Ten parametr jest zawsze typu **DWORD** i nosi nazwę zawsze *dwContext*.

Kontekst przypisane do określonego obiektu Internet jest używany tylko do identyfikacji działania obiektu powoduje, że w `OnStatusCallback` członkiem `CInternetSession` obiektu. Wywołanie `OnStatusCallback` odbiera kilka parametrów; parametry te działają razem w celu poinformowanie aplikacji, w jaki jest postęp które transakcji i połączenie.

Po utworzeniu `CInternetSession` obiektu, można określić *dwContext* parametr do konstruktora. `CInternetSession` sam nie korzysta z Identyfikatorem kontekstu; Zamiast tego przekazuje identyfikator kontekstu do dowolnego **InternetConnection**-pochodnych obiektów, które jawnie nie uzyskasz identyfikator kontekstu w swoich własnych. Z kolei, te `CInternetConnection` obiektów zostanie przekazany identyfikator kontekstu wzdłuż do `CInternetFile` obiekty tworzą, jeśli nie określisz jawnie identyfikator inny kontekst Jeśli z drugiej strony, określ identyfikator kontekstowi własne, obiektu i wykonywania pracy będzie skojarzony z tym identyfikatorem kontekstu. Kontekst identyfikatory umożliwia określenie, jakie informacje o stanie są przyznawane na Ciebie w swojej `OnStatusCallback` funkcji.

##  <a name="_core_display_progress_information_while_transferring_files"></a> Wyświetl informacje o postępie podczas transferu plików

Na przykład jeśli piszesz aplikację, tworzone jest połączenie z serwerem FTP do odczytu pliku, który również łączy się z serwerem HTTP, można pobrać strony sieci Web, będziesz mieć `CInternetSession` object, dwa `CInternetConnection` obiektów (jeden będzie `CFtpSession` i innych `CHttpSession`) oraz dwóch `CInternetFile` obiektów (po jednym dla każdego połączenia). Jeśli używane wartości domyślne dla *dwContext* parametrów, czy nie można rozróżnić `OnStatusCallback` wywołania, które wskazują postęp dla połączenia FTP i wywołań, które wskazują postęp Połączenia HTTP. Jeśli określisz *dwContext* identyfikator, który można później sprawdzić, w `OnStatusCallback`, będzie wiadomo, która operacja generowane wywołania zwrotnego.

## <a name="see-also"></a>Zobacz też

[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

