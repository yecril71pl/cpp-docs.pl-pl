---
title: Kroki opisane w typowej klienckiej aplikacji internetowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd3dde01d87fccd1d19d947a1069fa92675e6053
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390345"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Kroki wykonywane w typowej klienckiej aplikacji internetowej

W poniższej tabeli przedstawiono kroki, które może wykonywać w typowej klienckiej aplikacji internetowej.

|Cel|Wykonania akcji|Efekty|
|---------------|----------------------|-------------|
|Rozpocznij sesję Internet.|Tworzenie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Inicjuje WinInet i łączy się z serwerem.|
|Ustaw opcję Internet zapytania (limit czasu lub liczbę ponownych prób, na przykład).|Użyj [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Zwraca wartość FALSE, jeśli operacja nie powiodła się.|
|Ustanów funkcję wywołania zwrotnego do monitorowania stanu sesji.|Użyj [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Określa wywołanie zwrotne w celu [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Zastąp `OnStatusCallback` do tworzenia własnych procedura wywołania zwrotnego.|
|Podłącz do serwera internetowego, serwer intranetowych lub pliku lokalnego.|Użyj [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analizuje adres URL i otwiera połączenie z określonym serwerem. Zwraca [CStdioFile](../mfc/reference/cstdiofile-class.md) (w przypadku przekazania `OpenURL` nazwę pliku lokalnego). Jest to obiekt, za pomocą którego uzyskujesz dostęp do danych, o których pobierane z serwera lub pliku.|
|Odczytane z pliku.|Użyj [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|Odczytuje określoną liczbę bajtów przy użyciu buforu, który podasz.|
|Obsługa wyjątków.|Użyj [CInternetException](../mfc/reference/cinternetexception-class.md) klasy.|Obsługuje wszystkie popularne typy wyjątków Internet.|
|Zakończenie sesji internetowej.|Usuwanie [CInternetSession](../mfc/reference/cinternetsession-class.md) obiektu.|Automatycznie oczyszcza połączenia i uchwytów otwartego pliku.|

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Wymagania wstępne dotyczące klas klientów internetowych](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Pisanie klienckich aplikacji internetowych przy użyciu klas MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
