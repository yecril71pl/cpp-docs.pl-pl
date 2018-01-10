---
title: Kroki w typowej klienckiej aplikacji internetowej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ce4f5b91ebd68f13510f887c65927dbe5f84133
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-internet-client-application"></a>Kroki wykonywane w typowej klienckiej aplikacji internetowej
W poniższej tabeli przedstawiono kroki, które mogą wykonywać w typowej klienckiej aplikacji internetowej.  
  
|Poznasz|Czynności|Efekty|  
|---------------|----------------------|-------------|  
|Rozpocznij sesję Internet.|Utwórz [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|  
|Ustaw opcję zapytania Internet (limit czasu lub liczbę ponownych prób, na przykład).|Użyj [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Zwraca wartość FAŁSZ, jeśli operacja nie powiodła się.|  
|Ustanów funkcję wywołania zwrotnego do monitorowania stanu sesji.|Użyj [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Ustanawia wywołania zwrotnego do [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Zastąpienie `OnStatusCallback` do tworzenia własnych procedura wywołania zwrotnego.|  
|Łączenie z serwerem Internet, intranetowego serwera lub pliku lokalnego.|Użyj [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analizuje adres URL i otwiera połączenie z określonym serwerem. Zwraca [CStdioFile](../mfc/reference/cstdiofile-class.md) (w przypadku przekazania `OpenURL` nazwę pliku lokalnego). Jest to obiekt, którego uzyskiwany jest dostęp dane pobrane z serwera lub pliku.|  
|Odczytane z pliku.|Użyj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|Odczytuje określoną liczbę bajtów, przy użyciu podanego buforu.|  
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|  
|Kończenie sesji Internet.|Usuwa [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza dojścia do plików Otwórz i połączeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)   
 [Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
