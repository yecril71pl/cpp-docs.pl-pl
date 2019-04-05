---
title: 'Windows Sockets: Powiadomienia dotyczące gniazd'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: df7bfe8a95221682d0f7f4ebb123bd15b79144d5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774337"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Powiadomienia dotyczące gniazd

W tym artykule opisano funkcje powiadomień z klas gniazd. Te funkcje elementów członkowskich są funkcji wywołania zwrotnego, które struktura wywołuje w celu powiadomienia o ważnych zdarzeniach, obiekt gniazda. Dostępne są następujące funkcje powiadomień:

- [Zdarzenia OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): Powiadamia tego gniazda, że ma danych w buforze na jej do pobrania przez wywołanie metody [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): Powiadamia tego gniazda, że teraz przesyłania danych przez wywołanie metody [wysyłania](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): Powiadamia o tym nasłuchiwania gniazda, który może akceptować oczekujące żądania połączenia, wywołując [Akceptuj](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): Powiadamia o tym nawiązywania połączenia z gniazdem zakończenia jego próba połączenia: być może pomyślnie, lub może być błąd.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): Powiadamia tego zamknął gniazda, który jest połączony gniazda.

    > [!NOTE]
    >  Funkcja dodatkowych powiadomień jest [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). To powiadomienie informuje gniazda odbierania, że wysyłania gniazda ma "out-of-band" dane do wysłania. Out-of-band dane są logicznie niezależny od kanału skojarzone z każdej pary gniazda strumieni połączonych. Kanał out-of-band zwykle jest używana do wysyłania danych "pilne". Biblioteka MFC obsługuje dane poza pasmem. Zaawansowani użytkownicy pracy przy użyciu klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md) może być konieczne użycie kanału poza pasmem, ale użytkownicy klasy [CSocket](../mfc/reference/csocket-class.md) są odradzane korzystanie z niego. Jest łatwiejszy sposób utworzyć drugi gniazda przekazywania tych danych. Aby uzyskać więcej informacji o danych poza pasmem zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.

Jeśli pochodzi od klasy `CAsyncSocket`, konieczne jest przesłonięcie funkcje powiadomień dla tych sieci zdarzenia płynących ze swojej aplikacji. Jeśli wyprowadzić klasę z klasy `CSocket`, jest wybór, czy mają być zastępowane funkcje powiadomień zainteresowania. Można również użyć `CSocket` , w którym to przypadku powiadomienie funkcje domyślne czynności.

Te funkcje są funkcji wywołania zwrotnego w możliwym do zastąpienia. `CAsyncSocket` i `CSocket` convert komunikaty powiadomień, ale musi implementować, jak powiadomienia funkcje odpowiadać, jeśli chcesz umożliwić ich używanie. Funkcje powiadomień są wywoływane w czasie Twojej gniazda jest powiadamiany o zdarzenia interesujące, takie jak obecności danych do odczytu.

MFC wywołuje funkcje powiadomień, co pozwala dostosować swoje gniazda zachowanie w czasie, który jest powiadamiany o. Na przykład może wywołać `Receive` z Twojej `OnReceive` funkcję powiadomień, oznacza to, na czym powiadomiony, że ma danych do odczytu, należy wywołać `Receive` do jego odczytu. To podejście nie jest konieczne, ale jest nieprawidłowy. Alternatywnie, można użyć funkcji powiadomień umożliwiają śledzenie postępów, wydrukować **śledzenia** wiadomości i tak dalej.

Korzystać z zalet tych powiadomień, zastępowanie funkcji powiadomień w klasie pochodnej gniazda i podając implementację.

Podczas operacji takich jak odbierania lub wysyłania danych `CSocket` obiekt staje się synchroniczne. W stanie synchronicznym wszelkie powiadomienia przeznaczone dla innych gniazda są umieszczane w kolejce podczas bieżącej gniazda czeka na powiadomienie, które należy utworzyć. (Na przykład podczas `Receive` wywołania gniazda chce, aby powiadomienie do odczytu.) Po gniazda zakończy operację synchroniczne i asynchroniczne zostanie ponownie, inne gniazda można rozpocząć odbieranie powiadomień w kolejce.

> [!NOTE]
>  W `CSocket`, `OnConnect` nigdy nie jest wywoływana funkcja powiadamiania. W przypadku połączeń Wywołaj `Connect`, co spowoduje zwrócenie zakończeniu połączenie (pomyślnie lub w wyniku błędu). Sposób obsługi powiadomień połączenia jest szczegółowo opisuje implementacja MFC.

Aby uzyskać szczegółowe informacje o każdej z nich powiadomień, zobacz opis funkcji w ramach klasy `CAsyncSocket` w *odwołanie MFC*. Kod źródłowy i informacje o próbki MFC, zobacz [próbki MFC](../overview/visual-cpp-samples.md).

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Zobacz także

[Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)
