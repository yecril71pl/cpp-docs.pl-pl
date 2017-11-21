---
title: Kroki w typowej aplikacji klienckiej HTTP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ff67aa933e129d73747439f469140ae88be1778
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="steps-in-a-typical-http-client-application"></a>Kroki wykonywane w typowej aplikacji klienckiej HTTP
W poniższej tabeli przedstawiono kroki, które mogą wykonywać w typowej aplikacji klienckiej HTTP:  
  
|Poznasz|Czynności|Efekty|  
|---------------|----------------------|-------------|  
|Rozpoczęcie sesji HTTP.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|  
|Połącz się z serwerem HTTP.|Użyj [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Zwraca [CHttpConnection](../mfc/reference/chttpconnection-class.md) obiektu.|  
|Otwórz żądania HTTP.|Użyj [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Zwraca [CHttpFile](../mfc/reference/chttpfile-class.md) obiektu.|  
|Wyślij żądanie HTTP.|Użyj [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) i [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Znajduje plik. Zwraca wartość FAŁSZ, jeśli plik nie został znaleziony.|  
|Odczytane z pliku.|Użyj [CHttpFile](../mfc/reference/chttpfile-class.md).|Odczytuje określoną liczbę bajtów, przy użyciu podanego buforu.|  
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|  
|Kończenie sesji HTTP.|Usuwa [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza dojścia do plików Otwórz i połączeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
