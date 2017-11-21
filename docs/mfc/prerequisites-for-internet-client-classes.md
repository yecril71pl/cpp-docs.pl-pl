---
title: "Wymagania wstępne dotyczące klas klientów internetowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d079edd919d54149b527330a7a3cb49fa496f676
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="prerequisites-for-internet-client-classes"></a>Wymagania wstępne dotyczące klas klientów internetowych
Niektóre akcje podejmowane przez klienta internetowego (odczytywania pliku, na przykład) mają akcje wymagań wstępnych (w tym przypadku ustanawiania połączenia z Internetem). W poniższej tabeli wymieniono wymagania wstępne dotyczące niektóre akcje klienta.  
  
### <a name="general-internet-url-ftp-gopher-or-http"></a>Ogólne internetowy adres URL (FTP, Gopher lub HTTP)  
  
|Akcja|Wymaganie wstępne|  
|------------|------------------|  
|Nawiąż połączenie.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) ustanowienie podstawę klienckich aplikacji internetowych.|  
|Otwórz adres URL.|Nawiąż połączenie. Wywołanie [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). `OpenURL` Funkcja zwraca obiekt zasobów tylko do odczytu.|  
|Adres URL odczytu danych.|Otwórz adres URL. Wywołanie [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Ustaw opcję Internet.|Nawiąż połączenie. Wywołanie [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|  
|Ustaw funkcję, która ma zostać wywołany z informacji o stanie.|Nawiąż połączenie. Wywołanie [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback). Zastąpienie [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) do obsługi połączeń.|  
  
### <a name="ftp"></a>FTP  
  
|Akcja|Wymaganie wstępne|  
|------------|------------------|  
|Nawiąż połączenie FTP.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołanie [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection) utworzyć [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|  
|Znajdź pierwszy zasób.|Nawiąż połączenie FTP. Utwórz [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) obiektu. Wywołanie [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|  
|Wyliczenie wszystkich dostępnych zasobów.|Znajdź pierwszy plik. Wywołanie [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile) dopóki zwraca wartość FALSE.|  
|Otwórz plik FTP.|Nawiąż połączenie FTP. Wywołanie [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile) do tworzenia i otwierania [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu.|  
|Przeczytaj plik FTP.|Otwórz plik FTP z dostępem do odczytu. Wywołanie [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Zapis plików FTP.|Otwórz plik FTP z prawem do zapisu. Wywołanie [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|  
|Zmień katalog klienta na serwerze.|Nawiąż połączenie FTP. Wywołanie [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|  
|Pobieranie bieżącego katalogu klienta na serwerze.|Nawiąż połączenie FTP. Wywołanie [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory).|  
  
### <a name="http"></a>HTTP  
  
|Akcja|Wymaganie wstępne|  
|------------|------------------|  
|Nawiąż połączenie HTTP.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołanie [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection) utworzyć [CHttpConnection](../mfc/reference/chttpconnection-class.md) obiektu.|  
|Otwórz plik HTTP.|Nawiąż połączenie HTTP. Wywołanie [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) utworzyć [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu. Wywołanie [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders). Wywołanie [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|  
|Przeczytaj plik HTTP.|Otwórz plik HTTP. Wywołanie [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|  
|Pobiera informacje o żądaniu HTTP.|Nawiąż połączenie HTTP. Wywołanie [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest) utworzyć [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu. Wywołanie [CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo).|  
  
### <a name="gopher"></a>Gopher  
  
|Akcja|Wymaganie wstępne|  
|------------|------------------|  
|Nawiąż połączenie gopher.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) jako podstawy tej klienckich aplikacji internetowych. Wywołanie [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection) utworzyć [CGopherConnection](../mfc/reference/cgopherconnection-class.md).|  
|Znajdź pierwszy plik w bieżącym katalogu.|Nawiąż połączenie gopher. Utwórz [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) obiektu. Wywołanie [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) utworzyć [CGopherLocator](../mfc/reference/cgopherlocator-class.md) obiektu. Przekaż lokalizatora do [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile). Wywołanie [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator) można pobrać lokalizacji pliku, jeśli będzie potrzebny później.|  
|Wyświetla wszystkie dostępne pliki.|Znajdź pierwszy plik. Wywołanie [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile) dopóki zwraca wartość FALSE.|  
|Otwórz plik gopher.|Nawiąż połączenie gopher. Utwórz Lokalizator gopher z [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator) lub znaleźć lokalizatora z [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Wywołanie [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|  
|Odczytaj plik gopher.|Otwórz plik gopher. Użyj [cgopherfile —](../mfc/reference/cgopherfile-class.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Klasy MFC do tworzenia klienckich aplikacji internetowych](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
