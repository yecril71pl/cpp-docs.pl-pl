---
title: 'Windows Sockets: powiadomienia dotyczące gniazd'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167774"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: powiadomienia dotyczące gniazd

W tym artykule opisano funkcje powiadomień w klasach gniazd. Te funkcje członkowskie są funkcjami wywołania zwrotnego, które są wywoływane przez platformę w celu powiadomienia obiektu gniazda ważnych zdarzeń. Funkcje powiadomień są następujące:

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): powiadamia to gniazdo, że w buforze znajdują się dane do pobrania przez wywołanie metody [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): powiadamia to gniazdo, że może teraz wysyłać dane przez wywołanie metody [send](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): powiadamia gniazdo nasłuchiwania, które może akceptować oczekujące żądania połączenia przez wywołanie metody [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): powiadamia to gniazdo łączące, że próba połączenia została zakończona: być może pomyślnie lub prawdopodobnie wystąpił błąd.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): powiadamia to gniazdo o zamknięciu gniazda, z którym jest ono połączone.

    > [!NOTE]
    >  Dodatkowa funkcja powiadomień to [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). To powiadomienie informuje gniazdo odbiorcze, że wysyła gniazdo wysyłające dane poza pasmem. Dane poza pasmem są logicznie niezależnym kanałem skojarzonym z każdą parą podłączonych gniazd strumienia. Kanał poza pasmem jest zazwyczaj używany do wysyłania "pilnych" danych. MFC obsługuje dane poza pasmem. Zaawansowani użytkownicy pracujący z klasą [CAsyncSocket](../mfc/reference/casyncsocket-class.md) mogą potrzebować korzystania ze kanału poza pasmem, ale nie są zalecane dla użytkowników klasy [CSocket](../mfc/reference/csocket-class.md) . Łatwiejszym sposobem, aby utworzyć drugie gniazdo do przekazywania takich danych. Aby uzyskać więcej informacji na temat danych poza pasmem, zobacz specyfikację Windows Sockets dostępną w Windows SDK.

Jeśli pochodzi z klasy `CAsyncSocket`, musisz zastąpić funkcje powiadomień dla tych zdarzeń sieci, które są interesujące dla aplikacji. Jeśli klasa jest pochodną klasy z `CSocket`, jest to wybór, czy należy zastąpić interesujące funkcje powiadomień. Można również użyć samego `CSocket`, w którym to przypadku funkcje powiadomień domyślnie nie robią żadnych operacji.

Te funkcje są wykorzystanymi funkcjami wywołania zwrotnego. `CAsyncSocket` i `CSocket` konwersji komunikatów do powiadomień, ale musisz zaimplementować sposób reagowania funkcji powiadomień, jeśli chcesz ich używać. Funkcje powiadamiania są wywoływane w chwili, gdy gniazdo zostanie powiadomione o zdarzeniu, na przykład o obecności danych do odczytu.

MFC wywołuje funkcje powiadomień, aby umożliwić dostosowanie zachowania gniazda w momencie powiadomienia. Można na przykład wywoływać `Receive` z funkcji powiadomień `OnReceive`, czyli powiadomienia o tym, że dane są odczytywane, należy wywołać `Receive`, aby go odczytać. Takie podejście nie jest konieczne, ale jest prawidłowym scenariuszem. Alternatywnie możesz użyć funkcji powiadomień do śledzenia postępu, drukowania komunikatów **śledzenia** i tak dalej.

Aby skorzystać z tych powiadomień, można zastępowanie funkcji powiadomień w pochodnej klasie gniazd i zapewnić implementację.

Podczas operacji, takiej jak otrzymywanie lub wysyłanie danych, obiekt `CSocket` zostanie synchronicznie. Podczas synchronicznego stanu wszystkie powiadomienia przeznaczone dla innych gniazd są umieszczane w kolejce, gdy bieżące gniazdo oczekuje na powiadomienie. (Na przykład podczas wywołania `Receive` gniazdo chce, aby powiadomienie było odczytywane.) Gdy gniazdo ukończy operację synchroniczną i przestanie być asynchroniczne, inne gniazda mogą zacząć odbierać powiadomienia znajdujące się w kolejce.

> [!NOTE]
> W `CSocket`Funkcja powiadomień `OnConnect` nigdy nie jest wywoływana. W przypadku połączeń należy wywołać `Connect`, co spowoduje zwrócenie po zakończeniu połączenia (pomyślnie lub w przypadku błędu). Sposób obsługi powiadomień o połączeniach to szczegóły implementacji MFC.

Aby uzyskać szczegółowe informacje na temat każdej funkcji powiadomień, zobacz Funkcja w obszarze Klasa `CAsyncSocket` w *Kompendium MFC*. Aby uzyskać kod źródłowy i informacje o przykładach MFC, zobacz [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Gniazda systemu Windows: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Gniazda systemu Windows: jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Gniazda systemu Windows: blokowanie](../mfc/windows-sockets-blocking.md)

- [Gniazda systemu Windows: określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md)

- [Gniazda systemu Windows: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
