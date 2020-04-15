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
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359996"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: blokowanie

W tym artykule i dwóch artykułach towarzyszących wyjaśniono kilka problemów związanych z programowaniem w systemach Windows Sockets. W tym artykule opisano blokowanie. Inne problemy są omówione w artykułach: [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) i [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Jeśli używasz lub pochodzisz z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzać tymi problemami. Jeśli używasz lub pochodzisz z klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza nimi za Ciebie.

## <a name="blocking"></a>blokowanie

Gniazdo może być w "trybie blokowania" lub "trybie nieblokujący". Funkcje gniazd w trybie blokowania (lub synchroniczowego) nie wracają, dopóki nie będą mogły wykonać działania. Jest to nazywane blokowaniem, ponieważ gniazdo, którego funkcja została wywołana, nie może nic zrobić — jest zablokowane — dopóki wywołanie nie powróci. Wywołanie funkcji `Receive` elementu członkowskiego, na przykład, może potrwać dowolnie długo, aby zakończyć, ponieważ czeka `CSocket`na wysyłanie `CAsyncSocket` aplikacji do wysłania (jest to, jeśli używasz , lub przy użyciu z blokowaniem). Jeśli `CAsyncSocket` obiekt jest w trybie nonblocking (działa asynchronicznie), wywołanie zwraca natychmiast i bieżący kod błędu, można pobrać z funkcji elementu członkowskiego [GetLastError,](../mfc/reference/casyncsocket-class.md#getlasterror) jest **WSAEWOULDBLOCK**, wskazując, że wywołanie zostałoby zablokowane, gdyby nie zwrócone natychmiast z powodu trybu. (`CSocket` nigdy nie zwraca **WSAEWOULDBLOCK**. Klasa zarządza blokowaniem dla Ciebie.)

Zachowanie gniazd różni się w 32-bitowych i 64-bitowych systemach operacyjnych (takich jak Windows 95 lub Windows 98) niż w 16-bitowych systemach operacyjnych (takich jak Windows 3.1). W przeciwieństwie do 16-bitowych systemów operacyjnych 32-bitowe i 64-bitowe systemy operacyjne wykorzystują wywłaszczającą wielozadaniowość i zapewniają wielowątkowość. W 32-bitowych i 64-bitowych systemach operacyjnych można umieścić gniazda w oddzielnych wątkach roboczych. Gniazdo w wątku można zablokować bez zakłócania innych działań w aplikacji i bez poświęcania czasu obliczeniowego na blokowanie. Aby uzyskać informacje na temat programowania wielowątkowego, zobacz artykuł [Wielowątkowe](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> W aplikacjach wielowątkowych można użyć `CSocket` charakteru blokowania, aby uprościć projekt programu bez wpływu na responsywność interfejsu użytkownika. Obsługując interakcje użytkownika w wątku głównym i `CSocket` przetwarzania w wątkach alternatywnych, można oddzielić te operacje logiczne. W aplikacji, która nie jest wielowątkowa, te dwa działania muszą być połączone i `CAsyncSocket` obsługiwane jako pojedynczy wątek, co `CSocket::OnMessagePending` zwykle oznacza używanie, dzięki czemu można obsługiwać żądania komunikacji na żądanie lub zastępowanie do obsługi akcji użytkownika podczas długich działań synchronicznych.

Reszta tej dyskusji jest dla programistów skierowanych do 16-bitowych systemów operacyjnych:

Zwykle, jeśli używasz `CAsyncSocket`, należy unikać blokowania operacji i działać asynchronicznie zamiast. W operacjach asynchronicznych, od punktu, w którym otrzymasz kod błędu `Receive` **WSAEWOULDBLOCK** po wywołaniu , na przykład poczekaj, aż funkcja `OnReceive` elementu członkowskiego zostanie wywołana, aby powiadomić, że można odczytać ponownie. Wywołania asynchroniczne są wywoływane przez oddzwanianie odpowiedniej funkcji powiadomień o wywołaniu zwrotnym gniazda, takiej jak [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

W systemie Windows blokowanie połączeń jest uważane za złą praktykę. Domyślnie [CAsyncSocket](../mfc/reference/casyncsocket-class.md) obsługuje wywołania asynchroniczne i należy zarządzać blokowanie siebie za pomocą powiadomień wywołania zwrotnego. Klasa [CSocket](../mfc/reference/csocket-class.md), z drugiej strony, jest synchroniczowa. Pompuje wiadomości systemu Windows i zarządza blokowaniem dla Ciebie.

Aby uzyskać więcej informacji na temat blokowania, zobacz specyfikację windows sockets. Aby uzyskać więcej informacji na temat funkcji "Włączone", zobacz [Gniazda systemu Windows: Powiadomienia o gniazdach](../mfc/windows-sockets-socket-notifications.md) i [Gniazda systemu Windows: Pochodne z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
