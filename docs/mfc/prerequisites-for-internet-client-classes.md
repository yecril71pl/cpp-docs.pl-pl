---
title: Wymagania wstępne dotyczące klas klientów internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e374305586db3c69a19194e866d5a03d3de91f4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402658"
---
# <a name="prerequisites-for-internet-client-classes"></a>Wymagania wstępne dotyczące klas klientów internetowych

Niektóre akcje podjęte przez klienta internetowego (na przykład podczas odczytywania pliku) dostępne akcje wymagań wstępnych (w tym przypadku nawiązywania połączenia z Internetem). W poniższej tabeli wymieniono wymagania wstępne w przypadku niektórych działań klienta.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Ogólne internetowych adresów URL (FTP, Gopher lub HTTP)

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Nawiąż połączenie.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) nawiązać podstawę klienckich aplikacji internetowych.|
|Otwórz adres URL.|Nawiąż połączenie. Wywołaj [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). `OpenURL` Funkcja zwraca obiekt zasobów tylko do odczytu.|
|Dane odczytu adresu URL.|Otwórz adres URL. Wywołaj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Ustaw opcję Internet.|Nawiąż połączenie. Wywołaj [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|
|Ustaw funkcję, która ma zostać wywołany z informacji o stanie.|Nawiąż połączenie. Wywołaj [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback). Zastąp [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) do obsługi połączeń.|

### <a name="ftp"></a>FTP

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Ustanawianie połączenia FTP.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołaj [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection) utworzyć [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|
|Znajdź pierwszy zasób.|Ustanawianie połączenia FTP. Tworzenie [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) obiektu. Wywołaj [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|
|Wylicza wszystkie dostępne zasoby.|Znajdź pierwszy plik. Wywołaj [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile) dopóki zwróci wartość FALSE.|
|Otwórz plik FTP.|Ustanawianie połączenia FTP. Wywołaj [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile) do tworzenia i otwierania [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu.|
|Odczytywanie pliku FTP.|Otwórz plik FTP z dostępem do odczytu. Wywołaj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Zapis plików FTP.|Otwórz plik FTP z dostępem do zapisu. Wywołaj [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|
|Zmień katalog klienta na serwerze.|Ustanawianie połączenia FTP. Wywołaj [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|
|Pobierz klienta bieżącego katalogu na serwerze.|Ustanawianie połączenia FTP. Wywołaj [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Nawiązać połączenie HTTP.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołaj [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection) utworzyć [CHttpConnection](../mfc/reference/chttpconnection-class.md) obiektu.|
|Otwórz plik HTTP.|Nawiązać połączenie HTTP. Wywołaj [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) utworzyć [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu. Wywołaj [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders). Wywołaj [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|
|Odczytywanie pliku HTTP.|Otwórz plik HTTP. Wywołaj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|
|Uzyskaj informacje o żądaniu HTTP.|Nawiązać połączenie HTTP. Wywołaj [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) utworzyć [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu. Wywołaj [CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>Gopher

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Nawiąż połączenie gopher.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołaj [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection) utworzyć [CGopherConnection](../mfc/reference/cgopherconnection-class.md).|
|Znajdź pierwszy plik w bieżącym katalogu.|Nawiąż połączenie gopher. Tworzenie [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) obiektu. Wywołaj [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) utworzyć [CGopherLocator](../mfc/reference/cgopherlocator-class.md) obiektu. Lokalizator, aby przekazać [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile). Wywołaj [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator) można pobrać Lokalizator pliku, jeśli będą potrzebne później.|
|Wyliczanie wszystkich dostępnych plików.|Znajdź pierwszy plik. Wywołaj [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile) dopóki zwróci wartość FALSE.|
|Otwórz plik gopher.|Nawiąż połączenie gopher. Tworzenie lokalizatora gopher z [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) lub znaleźć lokalizatora z [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Wywołaj [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|
|Odczytywanie pliku gopher.|Otwórz plik gopher. Użyj [CGopherFile](../mfc/reference/cgopherfile-class.md).|

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Klasy MFC do tworzenia klienckich aplikacji internetowych](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
