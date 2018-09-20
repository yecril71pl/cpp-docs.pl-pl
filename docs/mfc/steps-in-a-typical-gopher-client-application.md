---
title: Kroki opisane w typowej aplikacji klienckiej Gopher | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c547d5b2a0bc9755fdf968fc1c42643e96e6fa6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392414"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej Gopher

W poniższej tabeli przedstawiono kroki, które może wykonywać w typowej aplikacji klienckiej gopher.

|Cel|Wykonania akcji|Efekty|
|---------------|----------------------|-------------|
|Rozpocznij sesję gopher.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|
|Łączenie z serwerem gopher.|Użyj [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Zwraca [CGopherConnection](../mfc/reference/cgopherconnection-class.md) obiektu.|
|Znajdź pierwszy zasób w gopher.|Użyj [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Znajdzie pierwszy plik. Zwraca wartość FALSE, jeśli nie zostaną znalezione żadne pliki.|
|Znajdź następny zasobów gopher.|Użyj [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Wyszukuje następny plik. Zwraca wartość FALSE, jeśli plik nie zostanie znaleziony.|
|Otwórz plik znalezione przez `FindFile` lub `FindNextFile` do odczytu.|Pobierz lokalizatora gopher przy użyciu [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Użyj [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otwiera plik określony przez lokalizatora. `OpenFile` Zwraca [CGopherFile](../mfc/reference/cgopherfile-class.md) obiektu.|
|Otwórz plik przy użyciu dostraczone lokalizatora gopher.|Tworzenie lokalizatora gopher przy użyciu [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Użyj [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otwiera plik określony przez lokalizatora. `OpenFile` Zwraca [CGopherFile](../mfc/reference/cgopherfile-class.md) obiektu.|
|Odczytane z pliku.|Użyj [CGopherFile](../mfc/reference/cgopherfile-class.md).|Odczytuje określoną liczbę bajtów, przy użyciu buforu, który podasz.|
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|
|Kończenie sesji gopher.|Usuwanie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza połączenia i uchwytów otwartego pliku.|

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
