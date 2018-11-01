---
title: 'Windows Sockets: blokowanie'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 7b41f034e08570e418bf24d9d720795eafc37932
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610577"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: blokowanie

W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule opisano blokowania. Inne problemy zostały omówione w artykułach: [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md) i [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).

Jeśli używasz lub pochodzić od klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli używasz lub pochodzić od klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza je dla Ciebie.

## <a name="blocking"></a>Blokowanie

Gniazda mogą znajdować się w "trybie blokowania" lub "Tryb nieblokujących". Funkcje gniazda w trybie blokowania (lub synchronicznego) nie zwracają do momentu ich zakończeniu ich działania. Jest to, blokowanie, ponieważ nie można nic robić gniazda, w których funkcja została wywołana — jest zablokowany — dopóki to wywołanie zwraca. Wywołanie `Receive` funkcja elementu członkowskiego, na przykład, może potrwać długi czas trwania jako czeka aplikacji wysyłającej wysyłanie (jest to, jeśli używasz `CSocket`, lub za pomocą `CAsyncSocket` z blokowaniem). Jeśli `CAsyncSocket` obiekt jest w trybie nieblokujących (działają asynchronicznie), to wywołanie zwraca niezwłocznie i bieżącego kodu błędu, możliwe do pobierania z [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) funkcja członkowska jest **WSAEWOULDBLOCK**, wskazującą, czy zablokowały wywołanie go nie jest zwracana, od razu ze względu na tryb obejmował. (`CSocket` nigdy nie zwraca **WSAEWOULDBLOCK**. Klasa zarządza blokowania dla Ciebie.)

Zachowanie sockets różni się w 32-bitowych i 64-bitowych systemach operacyjnych (na przykład Windows 95 lub Windows 98) niż w obszarze 16-bitowych systemach operacyjnych (na przykład Windows 3.1). W przeciwieństwie do 16-bitowych systemach operacyjnych systemy operacyjne 32-bitowych i 64-bitowych Użyj preemptive wielozadaniowość i zapewniają wielowątkowości. W 32-bitowych i 64-bitowych systemach operacyjnych można umieścić swoje gniazda w oddzielnych wątkach roboczych. Gniazda w wątku można zablokować, bez zakłócania innych działań w aplikacji i bez poświęcania czasu obliczeń na blokowanie. Aby uzyskać informacje dotyczące programowania wielowątkowe, zobacz artykuł [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
>  W aplikacjach wielowątkowych, można użyć blokowania charakter `CSocket` do uproszczenia projektu programu bez wywierania wpływu na czas odpowiedzi interfejsu użytkownika. Dzięki obsłudze interakcje użytkownika w głównym wątku i `CSocket` przetwarzania alternatywne wątki, można oddzielić te operacje logiczne. W aplikacji, która nie jest wielowątkowych, te dwa działania musi być połączone i obsługiwane jako pojedynczego wątku, co zwykle oznacza przy użyciu `CAsyncSocket` aby można było obsłużyć żądań komunikacji na żądanie lub zastępowanie `CSocket::OnMessagePending` do obsługi akcji użytkownika podczas długich działanie synchroniczne.

Pozostała część tej dyskusji, jest dla programistów, przeznaczone dla 16-bitowych systemach operacyjnych:

Normalnie Jeśli używasz `CAsyncSocket`, należy unikać blokowania operacji i działają asynchronicznie, zamiast tego. W operacji asynchronicznych, od punktu, w którym pojawi się **WSAEWOULDBLOCK** kod błędu: po wywołaniu `Receive`, na przykład czekać do momentu swojej `OnReceive` funkcja członkowska jest wywoływana, aby otrzymywać powiadomienia, że może odczytać ponownie. Wywołania asynchroniczne zostały wprowadzone, wywołując ponownie swoje gniazda odpowiednią funkcję wywołania zwrotnego powiadomień, takie jak [zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

W obszarze Windows wywołania blokowania są traktowane jako złym zwyczajem. Domyślnie [CAsyncSocket](../mfc/reference/casyncsocket-class.md) obsługuje wywołania asynchroniczne, a musi zarządzać, blokowanie, samodzielnie za pomocą powiadomień wywołania zwrotnego. Klasa [CSocket](../mfc/reference/csocket-class.md), z drugiej strony, jest synchroniczne. On pompy komunikatów Windows i zarządza blokowania dla Ciebie.

Aby uzyskać więcej informacji na temat blokowania zobacz specyfikację Windows Sockets. Aby uzyskać więcej informacji na temat "funkcji włączone", zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../mfc/windows-sockets-socket-notifications.md) i [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)

