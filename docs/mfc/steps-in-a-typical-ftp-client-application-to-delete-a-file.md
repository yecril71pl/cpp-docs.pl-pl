---
title: Procedura usuwania pliku w typowej aplikacji klienckiej FTP
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 6d2a920d3053a920638dd20a23e1c2334745bbc3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326507"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Procedura usuwania pliku w typowej aplikacji klienckiej FTP

W poniższej tabeli przedstawiono kroki, które można wykonywać w typowej aplikacji klienckiej FTP, która usuwa plik.

|Cel|Wykonania akcji|Efekty|
|---------------|----------------------|-------------|
|Rozpocznij sesję FTP.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|
|Połącz z serwerem FTP.|Użyj [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Zwraca [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|
|Sprawdź, upewnij się, że znajdujesz się w prawidłowym katalogu na serwerze FTP.|Użyj [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) lub [CFtpConnection::GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Zwraca nazwę lub adres URL katalogu w którym użytkownik jest aktualnie połączony się na serwerze, w zależności od funkcji składowej wybrane.|
|Przejdź do nowego katalogu FTP na serwerze.|Użyj [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Zmienia katalog, w którym użytkownik jest aktualnie połączony się na serwerze.|
|Znajdź pierwszy plik w katalogu FTP.|Użyj [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Znajdzie pierwszy plik. Zwraca wartość FALSE, jeśli nie zostaną znalezione żadne pliki.|
|Znajdź następny plik w katalogu FTP.|Użyj [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Wyszukuje następny plik. Zwraca wartość FALSE, jeśli plik nie zostanie znaleziony.|
|Usuń plik znalezione przez `FindFile` lub `FindNextFile`.|Użyj [CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove), przy użyciu nazwy pliku zwrócone przez `FindFile` lub `FindNextFile`.|Usuwa plik na serwerze do odczytu lub zapisu.|
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|
|Kończy sesję FTP.|Usuwanie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza połączenia i uchwytów otwartego pliku.|

## <a name="see-also"></a>Zobacz także

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
