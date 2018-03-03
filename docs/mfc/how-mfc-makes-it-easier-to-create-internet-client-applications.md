---
title: "Jak MFC ułatwia tworzenie klienckich aplikacji internetowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6270cdd3e64d24f1c2000acb9e8466f8c85edba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

