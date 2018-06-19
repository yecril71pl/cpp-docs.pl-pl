---
title: Kroki w typowej aplikacji klienckiej Gopher | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6ebb97d7cb5cbf2e2ed9ac7ae5287b2261990f2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381114"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej Gopher
W poniższej tabeli przedstawiono kroki, które mogą wykonywać w typowej aplikacji klienckiej gopher.  
  
|Poznasz|Czynności|Efekty|  
|---------------|----------------------|-------------|  
|Rozpocznij sesję gopher.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|  
|Połączenie z serwerem gopher.|Użyj [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Zwraca [CGopherConnection](../mfc/reference/cgopherconnection-class.md) obiektu.|  
|Znajdź pierwszy zasób w gopher.|Użyj [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Znajduje pierwszy plik. Zwraca wartość FAŁSZ, jeśli nie są można odnaleźć plików.|  
|Znajdź następny zasobów w gopher.|Użyj [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Znajduje następny plik. Zwraca wartość FAŁSZ, jeśli plik nie został znaleziony.|  
|Otwórz plik został znaleziony przez klasę **FindFile** lub `FindNextFile` do odczytu.|Pobierz za pomocą lokalizatora gopher [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Użyj [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otwiera plik określony przez lokalizator. `OpenFile` Zwraca [cgopherfile —](../mfc/reference/cgopherfile-class.md) obiektu.|  
|Otwórz plik za pomocą lokalizatora gopher podane.|Utwórz Lokalizator gopher przy użyciu [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Użyj [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Otwiera plik określony przez lokalizator. `OpenFile` Zwraca [cgopherfile —](../mfc/reference/cgopherfile-class.md) obiektu.|  
|Odczytane z pliku.|Użyj [cgopherfile —](../mfc/reference/cgopherfile-class.md).|Odczytuje określoną liczbę bajtów, przy użyciu podanego buforu.|  
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|  
|Kończenie sesji gopher.|Usuwa [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza dojścia do plików Otwórz i połączeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
