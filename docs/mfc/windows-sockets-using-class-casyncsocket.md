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
ms.openlocfilehash: 6a3b3469b908eaf6f8062b8db7fc4287606b7f02
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228508"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: używanie klasy CAsyncSocket

W tym artykule wyjaśniono, jak używać klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Należy pamiętać, że ta klasa hermetyzuje interfejs API Windows Sockets na bardzo niskim poziomie. `CAsyncSocket`jest przeznaczony dla programistów, którzy znają informacje o komunikacji sieciowej, ale chcą korzystać z funkcji wywołania zwrotnego do powiadamiania o zdarzeniach sieciowych. W oparciu o to założenie, ten artykuł zawiera tylko podstawową instrukcję. Należy rozważyć użycie, `CAsyncSocket` Jeśli chcesz, aby system Windows Sockets ułatwiał zajmowanie się wieloma protokołami sieciowymi w aplikacji MFC, ale nie chcesz wymusić elastyczności. Możesz również zastanowić się, że możesz uzyskać lepszą wydajność przez bezpośrednie programowanie komunikacji, niż można użyć bardziej ogólnego, alternatywnego modelu klasy `CSocket` .

`CAsyncSocket`opisano w dokumentacji *MFC*. Visual C++ również dostarcza specyfikację Windows Sockets, która znajduje się w Windows SDK. Szczegóły są pozostały do Ciebie. Visual C++ nie dostarcza przykładowej aplikacji dla programu `CAsyncSocket` .

Jeśli nie masz wysoce znajomości komunikacji sieciowej i potrzebujesz prostego rozwiązania, użyj klasy [CSocket](../mfc/reference/csocket-class.md) z `CArchive` obiektem. Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) .

W tym artykule omówiono następujące zagadnienia:

- Tworzenie i używanie `CAsyncSocket` obiektu.

- [Twoje obowiązki z CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Tworzenie i używanie obiektu CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Aby użyć CAsyncSocket

1. Skonstruuj obiekt [CAsyncSocket](../mfc/reference/casyncsocket-class.md) i użyj obiektu, aby utworzyć podstawowy uchwyt **gniazda** .

   Tworzenie gniazda następuje po wzorcu MFC konstruowania dwuetapowego.

   Na przykład:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -lub-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Pierwszy Konstruktor powyżej tworzy `CAsyncSocket` obiekt na stosie. Drugi Konstruktor tworzy `CAsyncSocket` na stercie. Pierwsze wywołanie [Create](../mfc/reference/casyncsocket-class.md#create) powyżej używa domyślnych parametrów do utworzenia gniazda strumienia. Drugie `Create` wywołanie tworzy gniazdo datagrama z określonym portem i adresem. (Można użyć dowolnej `Create` wersji z dowolną metodą konstrukcyjną).

   Parametry do `Create` są:

   - "Port": krótka liczba całkowita.

      Dla gniazda serwera należy określić port. Dla gniazda klienta zazwyczaj przyjmuje się wartość domyślną dla tego parametru, co umożliwia usłudze Windows Sockets wybranie portu.

   - Typ gniazda: **SOCK_STREAM** (wartość domyślna) lub **SOCK_DGRAM**.

   - Gniazdo "Address", takie jak "ftp.microsoft.com" lub "128.56.22.8".

      Jest to adres IP w sieci. Prawdopodobnie będzie można zawsze polegać na wartości domyślnej dla tego parametru.

   Warunki "Port" i "adres gniazda" objaśniono w [systemie Windows Sockets: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Jeśli gniazdo jest klientem, połącz obiekt gniazda z gniazdem serwera przy użyciu [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).

     -lub-

   Jeśli gniazdo jest serwerem, ustaw opcję Rozpocznij nasłuchiwanie (z [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)) w przypadku prób nawiązania połączenia z poziomu klienta. Po odebraniu żądania połączenia zaakceptuj je za pomocą [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Po zaakceptowaniu połączenia można wykonać takie zadania jak Walidacja haseł.

    > [!NOTE]
    >  `Accept`Funkcja członkowska przyjmuje odwołanie do nowego, pustego `CSocket` obiektu jako jego parametru. Należy skonstruować ten obiekt przed wywołaniem `Accept` . Jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie wywołuj `Create` dla tego nowego obiektu gniazda. Aby zapoznać się z przykładem, zobacz artykuł [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).

1. Przeprowadzenie komunikacji z innymi gniazdami przez wywołanie `CAsyncSocket` funkcji elementów członkowskich obiektu, które hermetyzują funkcje interfejsu API usługi Windows Sockets.

   Zobacz specyfikację Windows Sockets i Class [CAsyncSocket](../mfc/reference/casyncsocket-class.md) w *dokumentacji MFC*.

1. Zniszcz `CAsyncSocket` obiekt.

   Jeśli obiekt gniazda został utworzony na stosie, jego destruktor jest wywoływany, gdy funkcja zawierająca znajdzie się poza zakresem. Jeśli obiekt gniazda został utworzony na stercie przy użyciu **`new`** operatora, użytkownik jest odpowiedzialny za użycie **`delete`** operatora w celu zniszczenia obiektu.

   Destruktor wywołuje funkcję [zamykającego](../mfc/reference/casyncsocket-class.md#close) elementu członkowskiego obiektu przed zniszczeniem obiektu.

Przykład tej sekwencji w kodzie (rzeczywiście dla `CSocket` obiektu) można znaleźć w temacie [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Twoje obowiązki z CAsyncSocket

Podczas tworzenia obiektu klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), obiekt hermetyzuje uchwyt **gniazda** systemu Windows i dostarcza operacje na tym obsłudze. W przypadku korzystania `CAsyncSocket` z programu należy zaradzić sobie ze wszystkimi problemami, które mogą wystąpić, jeśli używasz interfejsu API bezpośrednio. Na przykład:

- Scenariusze "Blokowanie".

- Różnice między kolejnością bajtów między maszynami wysyłającymi i otrzymującymi.

- Konwersja między ciągami Unicode i wielobajtowym zestawem znaków (MBCS).

Aby zapoznać się z definicjami tych warunków i dodatkowych informacji, zobacz [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md), [Windows Sockets: porządkowanie bajtów](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).

Pomimo tych problemów, Klasa `CAsycnSocket` może być właściwym wyborem w przypadku, gdy aplikacja wymaga całej elastyczności i kontroli, którą można uzyskać. W przeciwnym razie należy rozważyć użycie klasy `CSocket` . `CSocket`ukrywa wiele szczegółów: kieruje komunikatami systemu Windows podczas blokowania wywołań i daje dostęp do `CArchive` , który zarządza różnicami w kolejności bajtów i konwersją ciągów.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Tło](../mfc/windows-sockets-background.md)

- [Windows Sockets: gniazda strumienia](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: gniazda datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)
