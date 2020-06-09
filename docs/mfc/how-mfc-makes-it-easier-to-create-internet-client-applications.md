---
title: Jak MFC ułatwia tworzenie klienckich aplikacji internetowych
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: 71b72a3079cd0d0c87289c1813c09a24d9f75c89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618558"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Jak MFC ułatwia tworzenie klienckich aplikacji internetowych

Microsoft Foundation Classes hermetyzuje funkcje rozszerzenia internetowego Win32 (WinInet) w sposób, który zapewnia znany kontekst dla programistów MFC. MFC udostępnia trzy klasy internetowych plików ([CInternetFile](reference/cinternetfile-class.md), [CHttpFile](reference/chttpfile-class.md)i [CGopherFile](reference/cgopherfile-class.md)) pochodzące z klasy [CStdioFile](reference/cstdiofile-class.md) . Te klasy nie tylko umożliwiają pobieranie i manipulowanie danymi internetowymi, które są znane dla programistów, którzy używali `CStdioFile` plików lokalnych, ale z tymi klasami można obsługiwać lokalne pliki i pliki internetowe w spójny, przejrzysty sposób.

Klasy MFC WinInet zapewniają takie same funkcje jak `CStdioFile` w przypadku danych przesyłanych przez Internet. Klasy te stanowią abstrakcyjne protokoły internetowe dla protokołów HTTP, FTP i gopher w interfejsie programowania aplikacji wysokiego poziomu, zapewniając szybką i prostą ścieżkę do tworzenia aplikacji internetowych. Na przykład połączenie z serwerem FTP nadal wymaga kilku kroków na niskim poziomie, ale jako deweloper MFC wystarczy wykonać jedno wywołanie, aby `CInternetSession::GetFTPConnection` utworzyć połączenie.

Ponadto klasy MFC WinInet zapewniają następujące korzyści:

- Buforowane we/wy

- Bezpieczne dla typu uchwyty dla danych

- Domyślne parametry dla wielu funkcji

- Obsługa wyjątków typowych błędów internetowych

- Automatyczne czyszczenie otwartych dojść i połączeń

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych](how-wininet-makes-it-easier-to-create-internet-client-applications.md)
