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
ms.openlocfilehash: 3d04a27a51645fc44296db7f5fd84bc2524804c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346116"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Jak MFC ułatwia tworzenie klienckich aplikacji internetowych
Biblioteka Microsoft Foundation Classes hermetyzować funkcje rozszerzenia internetowe Win32 (WinInet) w taki sposób, który zapewnia znanych kontekst dla programistów MFC. MFC udostępnia trzy klasy pliku Internet ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), i [cgopherfile —](../mfc/reference/cgopherfile-class.md)) pochodną [CStdioFile](../mfc/reference/cstdiofile-class.md) — klasa . Nie tylko tych klas wprowadzaj pobierania danych i operowanie nimi Internet znanych dla programistów, którzy użyli `CStdioFile` plików lokalnych, ale z tych klas w sposób spójny, przezroczysty może obsłużyć lokalnych plików i plików internetowych.  
  
 Klasy MFC WinInet zapewniają te same funkcje co `CStdioFile` danych przesyłanych przez Internet. Te klasy abstrakcyjnej protokołów internetowych dla protokołu HTTP, FTP i gopher do wysokiego poziomu application programming interface, podając ścieżkę szybkie i proste do tworzenia aplikacji obsługujących internetowe. Na przykład łączenie z serwerem FTP nadal wymaga podjęcia kilku czynności na niskim poziomie, ale Deweloper MFC, wystarczy utworzyć jedno wywołanie `CInternetSession::GetFTPConnection` do utworzenia tego połączenia.  
  
 Ponadto klas MFC WinInet zapewniają następujące korzyści:  
  
-   Buforowany we/wy  
  
-   Bezpiecznej obsługi danych  
  
-   Domyślne parametry dla funkcji  
  
-   Obsługa typowych błędów Internet wyjątków  
  
-   Automatyczne czyszczenie otwartych dojść i połączeń funkcji  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia internetowe Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Jak WinInet ułatwia tworzenie klienckich aplikacji internetowych](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)

