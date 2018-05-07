---
title: Testowanie aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61ffc5b11783806555b210b8561cbe6cdd2878ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="testing-internet-applications"></a>Testowanie aplikacji internetowych
Brak niektórych wyjątkowe wyzwanie testowania w Internecie, szczególnie w przypadku aplikacji uruchomionych na serwerze sieci Web. Testowanie początkowej prawdopodobnie będzie można wykonać za pomocą klienta pojedynczego użytkownika, nawiązania połączenia z serwerem testu. Będzie to przydatne w przypadku debugowania kodu.  
  
 Należy również przetestować w rzeczywistych warunkach: z wielu klientów połączonych za pośrednictwem szybkich połączeń, a także małej szybkości linii szeregowych, łącznie z połączeniami modemu. Może być trudne do symulowania rzeczywistych warunkach, ale warto pewnością wydatków czasu projektowania możliwe scenariusze i ich wykonywania. Jeśli to możliwe również można użyć narzędzia pojemności i testy obciążenia. Niektóre klasy błędów, takich jak błędy czasu są trudne do znalezienia i do odtworzenia.  
  
 Jednym z wyzwań związanych z programowaniem Internetu jest jej widoczność. Wiele operacji uzyskania dostępu do witryny może spowalniać działanie serwera. Chcesz, aby serwer zmniejszenie bezpiecznie zamknąć. Chcesz uniemożliwić wszystko, co może być destrukcyjnego na komputerze użytkownika, jeśli aplikacja nie powiedzie się (np. uszkodzenie danych podczas zapisywania w rejestrze lub podczas zapisywania plików cookie na komputerze klienckim).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

