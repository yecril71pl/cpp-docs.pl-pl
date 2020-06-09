---
title: Wymagania wstępne dotyczące klas klientów internetowych
ms.date: 11/04/2016
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
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619832"
---
# <a name="prerequisites-for-internet-client-classes"></a>Wymagania wstępne dotyczące klas klientów internetowych

Niektóre akcje podejmowane przez klienta internetowego (na przykład odczytujący plik) mają akcje wymagane wstępnie (w tym przypadku ustanawiają połączenie internetowe). W poniższych tabelach przedstawiono wymagania wstępne dotyczące niektórych akcji klienta programu.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Ogólny internetowy adres URL (FTP, gopher lub HTTP)

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Nawiąż połączenie.|Utwórz [CInternetSession](reference/cinternetsession-class.md) , aby ustalić podstawę internetowej aplikacji klienckiej.|
|Otwórz adres URL.|Nawiąż połączenie. Wywołanie [CInternetSession:: OpenURL](reference/cinternetsession-class.md#openurl). `OpenURL`Funkcja zwraca obiekt zasobów tylko do odczytu.|
|Odczytaj dane adresu URL.|Otwórz adres URL. Wywołanie [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Ustaw opcję Internet.|Nawiąż połączenie. Wywołanie [CInternetSession:: SetOption](reference/cinternetsession-class.md#setoption).|
|Ustaw funkcję, która ma zostać wywołana z informacjami o stanie.|Nawiąż połączenie. Wywołanie [CInternetSession:: EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback). Przesłoń [CInternetSession:: OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback) , aby obsługiwać wywołania.|

### <a name="ftp"></a>FTP

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Ustanów połączenie FTP.|Utwórz [CInternetSession](reference/cinternetsession-class.md) jako podstawę tej aplikacji klienckiej internetowej. Wywołanie [CInternetSession:: GetFtpConnection](reference/cinternetsession-class.md#getftpconnection) w celu utworzenia obiektu [CFtpConnection](reference/cftpconnection-class.md) .|
|Znajdź pierwszy zasób.|Ustanów połączenie FTP. Utwórz obiekt [CFtpFileFind](reference/cftpfilefind-class.md) . Wywołanie [CFtpFileFind:: FindFile —](reference/cftpfilefind-class.md#findfile).|
|Wylicz wszystkie dostępne zasoby.|Znajdź pierwszy plik. Wywołanie [CFtpFileFind:: FindNextFile](reference/cftpfilefind-class.md#findnextfile) , dopóki nie zwróci wartości false.|
|Otwórz plik FTP.|Ustanów połączenie FTP. Wywołaj [CFtpConnection:: OpenFile](reference/cftpconnection-class.md#openfile) , aby utworzyć i otworzyć obiekt [CInternetFile](reference/cinternetfile-class.md) .|
|Odczytaj plik FTP.|Otwórz plik FTP z dostępem do odczytu. Wywołanie [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Zapisz w pliku FTP.|Otwórz plik FTP z dostępem do zapisu. Call [CInternetFile:: Write](reference/cinternetfile-class.md#write).|
|Zmień katalog klienta na serwerze.|Ustanów połączenie FTP. Wywołanie [CFtpConnection:: SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory).|
|Pobierz bieżący katalog klienta na serwerze.|Ustanów połączenie FTP. Wywołanie [CFtpConnection:: GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Nawiąż połączenie HTTP.|Utwórz [CInternetSession](reference/cinternetsession-class.md) jako podstawę tej aplikacji klienckiej internetowej. Wywołanie [CInternetSession:: GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection) w celu utworzenia obiektu [CHttpConnection](reference/chttpconnection-class.md) .|
|Otwórz plik HTTP.|Nawiąż połączenie HTTP. Wywołanie [CHttpConnection:: OpenRequest](reference/chttpconnection-class.md#openrequest) w celu utworzenia obiektu [CHttpFile](reference/chttpfile-class.md) . Wywołanie [CHttpFile:: AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders). Wywołanie [CHttpFile:: SendRequest](reference/chttpfile-class.md#sendrequest).|
|Odczytaj plik HTTP.|Otwórz plik HTTP. Wywołanie [CInternetFile:: Read](reference/cinternetfile-class.md#read).|
|Pobierz informacje o żądaniu HTTP.|Nawiąż połączenie HTTP. Wywołanie [CHttpConnection:: OpenRequest](reference/chttpconnection-class.md#openrequest) w celu utworzenia obiektu [CHttpFile](reference/chttpfile-class.md) . Wywołanie [CHttpFile:: QueryInfo](reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>Gopher

|Akcja|Wymaganie wstępne|
|------------|------------------|
|Ustanów połączenie gopher.|Utwórz [CInternetSession](reference/cinternetsession-class.md) jako podstawę tej aplikacji klienckiej internetowej. Wywołanie [CInternetSession:: GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection) w celu utworzenia [CGopherConnection](reference/cgopherconnection-class.md).|
|Znajdź pierwszy plik w bieżącym katalogu.|Ustanów połączenie gopher. Utwórz obiekt [CGopherFileFind](reference/cgopherfilefind-class.md) . Wywołaj [CGopherConnection::](reference/cgopherconnection-class.md#createlocator) CGopherLocator, aby utworzyć obiekt [CGopherLocator](reference/cgopherlocator-class.md) . Przekaż lokalizator do [CGopherFileFind:: FindFile —](reference/cgopherfilefind-class.md#findfile). Zadzwoń do [CGopherFileFind:: Getlocatorer](reference/cgopherfilefind-class.md#getlocator) , aby uzyskać lokalizator pliku, jeśli będzie potrzebny później.|
|Wylicz wszystkie dostępne pliki.|Znajdź pierwszy plik. Wywołanie [CGopherFileFind:: FindNextFile](reference/cgopherfilefind-class.md#findnextfile) , dopóki nie zwróci wartości false.|
|Otwórz plik gopher.|Ustanów połączenie gopher. Utwórz lokalizator gopher z [CGopherConnection::](reference/cgopherconnection-class.md#createlocator) CGopherFileFind lub Znajdź lokalizator z [:: getlocatorer](reference/cgopherfilefind-class.md#getlocator). Wywołanie [CGopherConnection:: OpenFile](reference/cgopherconnection-class.md#openfile).|
|Odczytaj plik gopher.|Otwórz plik gopher. Użyj [CGopherFile](reference/cgopherfile-class.md).|

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Klasy MFC do tworzenia klienckich aplikacji internetowych](mfc-classes-for-creating-internet-client-applications.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](writing-an-internet-client-application-using-mfc-wininet-classes.md)
