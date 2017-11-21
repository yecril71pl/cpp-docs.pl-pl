---
title: Testowanie aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d246c6951b397e2eb888483f8afcdf2a822fd56d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="testing-internet-applications"></a>Testowanie aplikacji internetowych
Brak niektórych wyjątkowe wyzwanie testowania w Internecie, szczególnie w przypadku aplikacji uruchomionych na serwerze sieci Web. Testowanie początkowej prawdopodobnie będzie można wykonać za pomocą klienta pojedynczego użytkownika, nawiązania połączenia z serwerem testu. Będzie to przydatne w przypadku debugowania kodu.  
  
 Należy również przetestować w rzeczywistych warunkach: z wielu klientów połączonych za pośrednictwem szybkich połączeń, a także małej szybkości linii szeregowych, łącznie z połączeniami modemu. Może być trudne do symulowania rzeczywistych warunkach, ale warto pewnością wydatków czasu projektowania możliwe scenariusze i ich wykonywania. Jeśli to możliwe również można użyć narzędzia pojemności i testy obciążenia. Niektóre klasy błędów, takich jak błędy czasu są trudne do znalezienia i do odtworzenia.  
  
 Jednym z wyzwań związanych z programowaniem Internetu jest jej widoczność. Wiele operacji uzyskania dostępu do witryny może spowalniać działanie serwera. Chcesz, aby serwer zmniejszenie bezpiecznie zamknąć. Chcesz uniemożliwić wszystko, co może być destrukcyjnego na komputerze użytkownika, jeśli aplikacja nie powiedzie się (np. uszkodzenie danych podczas zapisywania w rejestrze lub podczas zapisywania plików cookie na komputerze klienckim).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

