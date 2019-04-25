---
title: Kroki wykonywane w typowej aplikacji klienckiej HTTP
ms.date: 11/04/2016
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
ms.openlocfilehash: 59b585d3e6b8c9f13c585f5a712d33abd6123f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306967"
---
# <a name="steps-in-a-typical-http-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej HTTP

W poniższej tabeli przedstawiono kroki, które może wykonywać w typowej aplikacji klienckiej HTTP:

|Cel|Wykonania akcji|Efekty|
|---------------|----------------------|-------------|
|Rozpocznij sesję protokołu HTTP.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|
|Połącz z serwerem HTTP.|Użyj [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Zwraca [CHttpConnection](../mfc/reference/chttpconnection-class.md) obiektu.|
|Otwórz żądanie HTTP.|Użyj [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Zwraca [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu.|
|Wyślij żądanie HTTP.|Użyj [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) i [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Umożliwia znalezienie pliku. Zwraca wartość FALSE, jeśli plik nie zostanie znaleziony.|
|Odczytane z pliku.|Użyj [CHttpFile](../mfc/reference/chttpfile-class.md).|Odczytuje określoną liczbę bajtów przy użyciu buforu, który podasz.|
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|
|Kończenie sesji HTTP.|Usuwanie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza połączenia i uchwytów otwartego pliku.|

## <a name="see-also"></a>Zobacz także

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
