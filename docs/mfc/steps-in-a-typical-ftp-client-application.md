---
title: Kroki wykonywane w typowej aplikacji klienckiej FTP
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: d08edf704e748767f3b566252ad328baf40b55ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307021"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej FTP

Tworzy w typowej aplikacji klienckiej FTP [CInternetSession](../mfc/reference/cinternetsession-class.md) i [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu. Należy pamiętać, że tych klas MFC WinInet faktycznie kontroluje ustawienia serwera proxy typu; Wykonuje usług IIS.

W poniższej tabeli przedstawiono kroki, które może wykonywać w typowej aplikacji klienckiej FTP.

|Cel|Wykonania akcji|Efekty|
|---------------|----------------------|-------------|
|Rozpocznij sesję FTP.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|
|Połącz z serwerem FTP.|Użyj [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Zwraca [CFtpConnection](../mfc/reference/cftpconnection-class.md) obiektu.|
|Przejdź do nowego katalogu FTP na serwerze.|Użyj [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Zmienia katalog, w którym użytkownik jest aktualnie połączony się na serwerze.|
|Znajdź pierwszy plik w katalogu FTP.|Użyj [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Znajdzie pierwszy plik. Zwraca wartość FALSE, jeśli nie zostaną znalezione żadne pliki.|
|Znajdź następny plik w katalogu FTP.|Użyj [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Wyszukuje następny plik. Zwraca wartość FALSE, jeśli plik nie zostanie znaleziony.|
|Otwórz plik znalezione przez `FindFile` lub `FindNextFile` do odczytu lub zapisu.|Użyj [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), przy użyciu nazwy pliku zwrócone przez [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) lub [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Otwiera plik na serwerze do odczytu lub zapisu. Zwraca [CInternetFile](../mfc/reference/cinternetfile-class.md) obiektu.|
|Odczytać lub zapisać do pliku.|Użyj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) lub [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Operacja odczytu lub zapisu określoną liczbę bajtów, przy użyciu buforu, który podasz.|
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|
|Kończy sesję FTP.|Usuwanie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza połączenia i uchwytów otwartego pliku.|

## <a name="see-also"></a>Zobacz także

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
