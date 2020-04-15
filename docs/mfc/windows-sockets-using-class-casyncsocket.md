---
title: 'Windows Sockets: używanie klasy CAsyncSocket'
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371969"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: używanie klasy CAsyncSocket

W tym artykule wyjaśniono, jak używać klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Należy pamiętać, że ta klasa hermetyzuje interfejsu API windows sockets na bardzo niskim poziomie. `CAsyncSocket`jest używany przez programistów, którzy znają komunikację sieciową w szczegółach, ale chcą wygody wywołania zwrotnego w celu powiadamiania o zdarzeniach sieciowych. Na podstawie tego założenia ten artykuł zawiera tylko podstawowe instrukcje. Prawdopodobnie należy rozważyć `CAsyncSocket` użycie, jeśli chcesz, aby gniazda systemu Windows łatwości radzenia sobie z wieloma protokołami sieciowymi w aplikacji MFC, ale nie chcesz poświęcić elastyczność. Możesz również poczuć, że możesz uzyskać lepszą wydajność, programowanie komunikacji bardziej bezpośrednio samodzielnie, niż `CSocket`można by użyć bardziej ogólnego alternatywnego modelu klasy.

`CAsyncSocket`jest udokumentowana w *odwołaniu MFC*. Visual C++ dostarcza również specyfikację windows sockets, znajdującą się w zestaw windows SDK. Szczegóły pozostają ci w pos. Visual C++ nie dostarcza przykładowej aplikacji dla `CAsyncSocket`.

Jeśli nie masz wysokiej wiedzy na temat komunikacji sieciowej i potrzebujesz prostego `CArchive` rozwiązania, użyj klasy [CSocket](../mfc/reference/csocket-class.md) z obiektem. Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami.](../mfc/windows-sockets-using-sockets-with-archives.md)

Ten artykuł obejmuje:

- Tworzenie i używanie `CAsyncSocket` obiektu.

- [Twoje obowiązki z CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Tworzenie i używanie obiektu CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Aby użyć CAsyncSocket

1. Konstruuj [obiekt CAsyncSocket](../mfc/reference/casyncsocket-class.md) i użyj obiektu do utworzenia dojścia **socket.**

   Tworzenie gniazda następuje wzór MFC konstrukcji dwuetapowej.

   Przykład:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     — lub —

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Pierwszy konstruktor powyżej `CAsyncSocket` tworzy obiekt na stosie. Drugi konstruktor `CAsyncSocket` tworzy na stercie. Pierwsze [wywołanie Create](../mfc/reference/casyncsocket-class.md#create) powyżej używa parametrów domyślnych do utworzenia gniazda strumienia. Drugie `Create` wywołanie tworzy gniazdo datagramu z określonym portem i adresem. (Można użyć jednej `Create` wersji z obu metod konstrukcji.)

   Parametry `Create` to:

   - "Port": krótka ćwiat całkowita.

      W przypadku gniazda serwera należy określić port. W przypadku gniazda klienta zazwyczaj akceptujesz wartość domyślną dla tego parametru, która umożliwia gniazdom systemu Windows wybranie portu.

   - Typ gniazda: **SOCK_STREAM** (domyślnie) lub **SOCK_DGRAM**.

   - Gniazdo "adres", takie jak "ftp.microsoft.com" lub "128.56.22.8".

      Jest to adres IP w sieci. Prawdopodobnie zawsze będziesz polegać na wartości domyślnej dla tego parametru.

   Terminy "port" i "adres gniazda" są wyjaśnione w [gniazdach systemu Windows: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Jeśli gniazdo jest klientem, podłącz obiekt gniazda do gniazda serwera, używając [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     — lub —

   Jeśli gniazdo jest serwerem, ustaw gniazdo, aby rozpocząć nasłuchiwanie (z [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) dla prób połączenia z klienta. Po otrzymaniu żądania połączenia, zaakceptuj go z [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Po zaakceptowaniu połączenia można wykonywać takie zadania, jak sprawdzanie poprawności haseł.

    > [!NOTE]
    >  Funkcja `Accept` elementu członkowskiego przyjmuje odwołanie do `CSocket` nowego, pustego obiektu jako parametru. Należy skonstruować ten obiekt `Accept`przed wywołaniem . Jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie należy `Create` wywoływać tego nowego obiektu gniazda. Na przykład zobacz artykuł [Gniazda systemu Windows: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).

1. Należy wykonywać komunikację z innymi `CAsyncSocket` gniazdami, wywołując funkcje członkowskie obiektu, które hermetyzują funkcje interfejsu API windows sockets.

   Zobacz specyfikację windows sockets i klasę [CAsyncSocket](../mfc/reference/casyncsocket-class.md) w *odwołaniu MFC*.

1. Zniszcz `CAsyncSocket` obiekt.

   Jeśli utworzono obiekt gniazda na stosie, jego destruktor jest wywoływana, gdy funkcja zawierająca wykracza poza zakres. Jeśli utworzono obiekt gniazda na stercie, przy użyciu **nowego** operatora, jesteś odpowiedzialny za użycie **delete** operator zniszczyć obiekt.

   Destruktor wywołuje funkcję [Zamknij](../mfc/reference/casyncsocket-class.md#close) element członkowski obiektu przed zniszczeniem obiektu.

Na przykład tej sekwencji w kodzie (faktycznie dla `CSocket` obiektu), zobacz Windows [Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Twoje obowiązki z CAsyncSocket

Podczas tworzenia obiektu klasy [CAsyncSocket,](../mfc/reference/casyncsocket-class.md)obiekt hermetyzuje uchwyt **gniazda** systemu Windows i dostarcza operacje na tym dojściu. Podczas korzystania `CAsyncSocket`z programu należy rozwiązać wszystkie problemy, które mogą napotkać, jeśli bezpośrednio przy użyciu interfejsu API. Przykład:

- scenariuszy "Blokowanie".

- Różnice w kolejności bajtów między maszynami wysyłającymi i odbierającymi.

- Konwersja między ciągami znaków Unicode i wielobajtowego zestawu znaków (MBCS).

Aby uzyskać definicje tych terminów i dodatkowych informacji, zobacz [Gniazda systemu Windows: Blokowanie](../mfc/windows-sockets-blocking.md), Gniazda systemu [Windows: Zamawianie bajtów](../mfc/windows-sockets-byte-ordering.md), [Gniazda systemu Windows: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).

Pomimo tych problemów `CAsycnSocket` klasa może być właściwym wyborem dla Ciebie, jeśli aplikacja wymaga całej elastyczności i kontroli, które można uzyskać. Jeśli nie, należy rozważyć `CSocket` użycie klasy zamiast. `CSocket`ukrywa wiele szczegółów przed tobą: pompuje wiadomości systemu Windows podczas `CArchive`blokowania połączeń i daje dostęp do , który zarządza różnicami w kolejności bajtów i konwersji ciągów dla Ciebie.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
