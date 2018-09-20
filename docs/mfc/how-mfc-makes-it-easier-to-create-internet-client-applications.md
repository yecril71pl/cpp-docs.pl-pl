---
title: Jak MFC ułatwia tworzenie klienckich aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26380dc7e01449e4700ddf403c7395714287ed38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407169"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Jak MFC ułatwia tworzenie klienckich aplikacji internetowych

Microsoft Foundation Classes hermetyzacji funkcji rozszerzenia internetowe Win32 (WinInet) w taki sposób, który zapewnia znanych kontekst dla programistów MFC. Biblioteka MFC zawiera trzy klasy pliku Internet ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), i [CGopherFile](../mfc/reference/cgopherfile-class.md)) pochodzące z [CStdioFile](../mfc/reference/cstdiofile-class.md) klasy . Nie tylko tych klas należy podczas pobierania danych i manipulowania nimi Internet znanych dla programistów, którzy korzystali z `CStdioFile` plików lokalnych, ale z tych klas w sposób spójny, przejrzyste może obsługiwać lokalnych plików i plików internetowych.

Klas MFC WinInet zapewniają taką samą funkcjonalność jak `CStdioFile` dla danych przesyłanych przez Internet. Te klasy abstrakcyjnej protokołów internetowych dla protokołu HTTP, FTP i gopher do aplikacji wysokiego poziomu interfejs programowania, zapewniając szybki i prosty ścieżki do tworzenia aplikacji obsługujących Internet. Na przykład nadal połączenie z serwerem FTP wymaga podjęcia kilku czynności na niskim poziomie, ale jako deweloper w MFC, wystarczy utworzyć jedno wywołanie `CInternetSession::GetFTPConnection` do utworzenia tego połączenia.

Ponadto klas MFC WinInet zapewniają następujące korzyści:

- Buforowanego wejścia/wyjścia

- Bezpieczne dojścia dla swoich danych

- Domyślne parametry dla wielu funkcji

- Obsługa dla typowych błędów Internet wyjątków

- Automatyczne oczyszczanie otwarte dojścia i połączeń

## <a name="see-also"></a>Zobacz też

[Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)

