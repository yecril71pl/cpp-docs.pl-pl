---
title: 'Windows Sockets: Używanie klasy CAsyncSocket | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49e5df8e88124d1d94869618a94525e224d32495
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424679"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: używanie klasy CAsyncSocket

W tym artykule opisano sposób użycia klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Należy pamiętać, że ta klasa hermetyzuje interfejsu API Windows Sockets w bardzo niskim poziomie. `CAsyncSocket` jest przeznaczona do użytku przez programistów, którzy znają komunikacji sieciowej szczegółowo, ale mają wygody wywołania zwrotne dla powiadomień o zdarzeniach w sieci. Oparte na tym założeń, ten artykuł zawiera tylko podstawowe instrukcji. Prawdopodobnie należy rozważyć użycie `CAsyncSocket` Jeśli chcesz, aby łatwo Windows Sockets związanych z wielu protokołów sieciowych w aplikacji MFC, ale nie chcesz poświęcać elastyczność. Może również możesz uzyskać lepszą wydajność Programując więcej komunikacji bezpośrednio samodzielnie niż może przy użyciu bardziej ogólny model alternatywnych klasy `CSocket`.

`CAsyncSocket` jest udokumentowany w *odwołanie MFC*. Visual C++ dostarcza również specyfikacji Windows Sockets, znajduje się w zestawie Windows SDK. Szczegółowe informacje są pozostawiane do Ciebie. Visual C++ nie dostarcza Przykładowa aplikacja dla `CAsyncSocket`.

Jeśli nie są wysoce odpowiednią wiedzę na temat komunikacji sieciowej i ma proste rozwiązanie, należy użyć klasy [CSocket](../mfc/reference/csocket-class.md) z `CArchive` obiektu. Zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) Aby uzyskać więcej informacji.

W tym artykule omówiono:

- Tworzenie i używanie `CAsyncSocket` obiektu.

- [Twoje obowiązki z CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Tworzenie i używanie obiektu CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Aby użyć CAsyncSocket

1. Konstruowania [CAsyncSocket](../mfc/reference/casyncsocket-class.md) obiektu i obiekt używany do tworzenia podstawowych **GNIAZDA** obsługi.

     Tworzenie gniazdo jest zgodny ze wzorcem MFC konstrukcji dwuetapowego.

     Na przykład:

     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     —lub—

     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

     Pierwszy Konstruktor powyżej tworzy `CAsyncSocket` obiektów na stosie. Drugi Konstruktor tworzy `CAsyncSocket` na stosie. Pierwszy [Utwórz](../mfc/reference/casyncsocket-class.md#create) wywołanie powyższej używa domyślnych parametrów w celu utworzenia gniazda strumieni. Drugi `Create` wywołanie tworzy gniazdo datagram z określonego portu i adres. (Można użyć dowolnego `Create` wersji za pomocą jednej z metod konstrukcja.)

     Parametry `Create` są:

   - "port": krótka liczba całkowita.

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - Typ gniazda: **SOCK_STREAM** (ustawienie domyślne) lub **SOCK_DGRAM**.

   - Gniazda "address" takich jak "pod adresem" lub "128.56.22.8".

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

     Terminy "port" i "adres gniazda" są wyjaśnione w [Windows Sockets: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Jeśli klient znajduje się w gniazda, obiekt gniazda nawiązywania połączenia z serwerem gniazda, za pomocą [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     —lub—

     Jeśli gniazda jest serwerem, należy ustawić gniazda, aby rozpocząć nasłuchiwania (przy użyciu [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) podczas podejmowania prób połączenia od klienta. Po odebraniu żądania połączenia, zaakceptuj je za pomocą [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

     Po zaakceptowaniu połączenia, można wykonywać zadania, takie jak sprawdzanie poprawności hasła.

    > [!NOTE]
    >  `Accept` Funkcja elementu członkowskiego przyjmuje odwołanie do nowy, pusty `CSocket` obiekt jako parametr. Należy utworzyć ten obiekt przed wywołaniem `Accept`. Jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostaje zamknięte. Nie wywołuj `Create` dla tego nowego obiektu gniazda. Aby uzyskać przykład, zobacz artykuł [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).

1. Przeprowadzać komunikacji z innymi gniazda, wywołując `CAsyncSocket` funkcji elementów członkowskich obiektu, które hermetyzują funkcje interfejsu API programu Windows Sockets.

     Windows Sockets specyfikacji i klasa [CAsyncSocket](../mfc/reference/casyncsocket-class.md) w *odwołanie MFC*.

1. Zniszcz `CAsyncSocket` obiektu.

     Jeśli utworzono obiekt gniazda na stosie, jego destruktor jest wywoływana, gdy funkcja zawierającego wykracza poza zakres. Jeśli utworzono obiekt gniazda na stosie, za pomocą **nowe** operatora, użytkownik jest odpowiedzialny za pomocą **Usuń** operatora do zniszczenia obiektu.

     Destruktor wywołuje obiekt [Zamknij](../mfc/reference/casyncsocket-class.md#close) funkcji składowej przed zniszczenia obiektu.

Na przykład ta sekwencja w kodzie (faktycznie dla `CSocket` obiektu), zobacz [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Twoje obowiązki z CAsyncSocket

Po utworzeniu obiektu klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), hermetyzuje Windows **GNIAZDA** obsługi i dostarcza operacje na dojścia. Kiedy używasz `CAsyncSocket`, muszą radzić sobie z problemami, może być twarzy, jeśli bezpośrednio za pomocą interfejsu API. Na przykład:

- Scenariusze "Blokuje".

- Bajt kolejności różnice między wysyłanie i odbieranie maszyn.

- Konwertowanie pomiędzy Unicode i multibyte character ustawić ciągów (znaków MBCS).

Aby uzyskać definicje tych warunków i dodatkowe informacje, zobacz [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md), [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md) .

Pomimo tych problemów klasy `CAsycnSocket` może być właściwym wyborem dla Ciebie, jeśli aplikacja wymaga elastyczności i kontroli, możesz uzyskać. Jeśli nie, należy rozważyć użycie klasy `CSocket` zamiast tego. `CSocket` ukrywa wiele szczegółowych ze strony użytkownika: it pompy komunikatów podczas blokuje wywołania Windows i umożliwia dostęp do `CArchive`, która zarządza różnice kolejności bajtów i konwersji ciągów dla Ciebie.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

