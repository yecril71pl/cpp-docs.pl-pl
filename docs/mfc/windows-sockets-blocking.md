---
title: 'Windows Sockets: Blokowanie | Dokumentacja firmy Microsoft'
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
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4b54b78034037e9f3b015d7c1f67bb33771248c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: blokowanie
W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule omówiono blokowania. Inne problemy zostały omówione w artykułach: [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md) i [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).  
  
 Jeśli jest używany lub pochodzi z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli jest używany lub pochodzi z klasy [CSocket —](../mfc/reference/csocket-class.md), MFC zarządza nimi automatycznie.  
  
## <a name="blocking"></a>Blokowanie  
 Gniazdo może być "Tryb blokowania" lub "Tryb nieblokujących". Funkcje gniazda w trybie blokowania (lub synchroniczne) zwraca aż do ich ukończenia tego działania. Ta metoda jest wywoływana blokuje ponieważ gniazda, w której funkcja została wywołana nie może wykonywać żadnych czynności — jest zablokowany — dopóki wywołanie zwraca. Wywołanie **Receive** funkcji członkowskiej, na przykład może potrwać arbitralnie długo jak oczekuje na aplikację wysyłającą do wysyłania (jest to, jeśli używasz `CSocket`, lub za pomocą `CAsyncSocket` z blokowaniem). Jeśli `CAsyncSocket` obiekt jest w trybie nieblokujących (asynchronicznie pracy), wywołanie zwraca natychmiast i bieżącego kodu błędu, pobieranie z [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) funkcja członkowska jest **WSAEWOULDBLOCK**, wskazującą, czy wywołanie może mieć zablokowane ma on nie zwrócił natychmiast z powodu tryb. (`CSocket` nigdy nie zwraca **WSAEWOULDBLOCK**. Klasa zarządza blokuje dla Ciebie.)  
  
 Zachowanie sockets różni się w 32-bitowych i 64-bitowych systemach operacyjnych (na przykład system Windows 95 lub Windows 98) niż w 16-bitowych systemach operacyjnych (na przykład Windows 3.1). W przeciwieństwie do 16-bitowe systemy operacyjne 32-bitowe i 64-bitowe systemy operacyjne Użyj wielozadaniowości cenią sobie wcześniejsze i podaj wielowątkowości. W 32-bitowych i 64-bitowych systemach operacyjnych możesz umieścić z gniazda w oddzielnych wątków. Gniazdo w wątku można zablokować, bez zakłócania innych działań w aplikacji i bez ponoszenia czasu obliczeniowego blokowania. Uzyskać informacji o programowanie wielowątkowe, zobacz artykuł [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
> [!NOTE]
>  W aplikacjach wielowątkowych, można użyć blokowania rodzaj `CSocket` uprościć projekt programu bez wpływu na czas odpowiedzi interfejsu użytkownika. Dzięki obsłudze interakcji użytkowników w głównym wątku i `CSocket` przetwarzania w wątkach alternatywne, można oddzielić te operacje logiczne. W aplikacji, która nie jest wielowątkowe, te dwa działania muszą być połączone i obsługiwane jako pojedynczego wątku, co zwykle oznacza przy użyciu `CAsyncSocket` aby mogły obsługiwać żądania komunikacji na żądanie lub zastępowanie `CSocket::OnMessagePending` do obsługi akcji użytkownika podczas długich działanie synchroniczne.  
  
 Pozostała część tego omówienia jest dla programistów przeznaczonych dla 16-bitowych systemach operacyjnych:  
  
 Zwykle Jeśli używasz `CAsyncSocket`, należy unikać blokowania operacji i obsługi zamiast asynchronicznie. W operacji asynchronicznych z punktu odbierania **WSAEWOULDBLOCK** kod błędu po wywołaniu **Receive**, na przykład czekać do Twojej `OnReceive` funkcja członkowska jest wywoływana w celu powiadomienia Użytkownik, który można odczytać ponownie. Wywołania asynchroniczne są wykonywane przez wywołań zwrotnych funkcja powiadomień odpowiednie wywołania zwrotnego z gniazda, takich jak [zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).  
  
 W systemie Windows blokowania połączeń są traktowane jako rozwiązaniem zły. Domyślnie [CAsyncSocket](../mfc/reference/casyncsocket-class.md) obsługuje wywołania asynchroniczne, a musi zarządzać blokuje samodzielnie przy użyciu powiadomienia wywołania zwrotnego. Klasa [CSocket —](../mfc/reference/csocket-class.md), z drugiej strony, jest synchroniczne. Pompy komunikatów systemu Windows, a zarządza blokuje dla Ciebie.  
  
 Aby uzyskać więcej informacji na temat blokowania zobacz specyfikację Windows Sockets. Aby uzyskać więcej informacji o "funkcji włączone", zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md) i [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)

