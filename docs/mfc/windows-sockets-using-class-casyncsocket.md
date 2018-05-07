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
ms.openlocfilehash: a96ccdd4ce5c49f18c12aa85060954fc97a3408b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: używanie klasy CAsyncSocket
W tym artykule opisano sposób użycia klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Należy pamiętać, że ta klasa hermetyzuje API systemu Windows Sockets na bardzo niskim poziomie. `CAsyncSocket` jest przeznaczona dla programistów, którzy znasz komunikacji sieciowej szczegółowo, ale mają wygodę wywołań zwrotnych dla powiadomień o zdarzeniach w sieci. W oparciu o ten założeń, w tym artykule przedstawiono tylko podstawowe instrukcji. Prawdopodobnie należy rozważyć użycie `CAsyncSocket` łatwość zajmowanie się wiele protokołów sieciowych w aplikacji MFC Windows Sockets ale nie chcesz pochodzących z elastyczność. Może również uznać, że można uzyskać lepszą wydajność programowania więcej łączności bezpośrednio można samodzielnie niż przy użyciu bardziej ogólne modelu alternatywnych klasy `CSocket`.  
  
 `CAsyncSocket` opisano w *odwołania MFC*. Visual C++ udostępnia również specyfikację Windows Sockets znajduje się w zestawie Windows SDK. Szczegóły pozostało do Ciebie. Visual C++ nie dostarcza Przykładowa aplikacja dla `CAsyncSocket`.  
  
 Jeśli nie są wysoce wiedzę o komunikacji sieciowej i proste rozwiązanie, należy użyć klasy [CSocket —](../mfc/reference/csocket-class.md) z `CArchive` obiektu. Zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md) Aby uzyskać więcej informacji.  
  
 W tym artykule omówiono:  
  
-   Tworzenie i używanie `CAsyncSocket` obiektu.  
  
-   [Twoje obowiązki z CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Tworzenie i używanie obiektu CAsyncSocket  
  
#### <a name="to-use-casyncsocket"></a>Aby użyć CAsyncSocket  
  
1.  Utworzyć [CAsyncSocket](../mfc/reference/casyncsocket-class.md) obiektu i obiekt używany do tworzenia podstawowych **GNIAZDA** obsługi.  
  
     Tworzenie gniazda jest zgodny ze wzorcem MFC dwuetapowa konstrukcji.  
  
     Na przykład:  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     —lub—  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     Tworzy konstruktora pierwszy powyżej `CAsyncSocket` obiektu na stosie. Tworzy drugi Konstruktor `CAsyncSocket` na stosie. Pierwszy [Utwórz](../mfc/reference/casyncsocket-class.md#create) wywołania powyżej korzysta z domyślnych parametrów można utworzyć gniazda strumienia. Drugi **Utwórz** wywołanie tworzy gniazdo datagramu z określonego portu i adres. (Możesz użyć dowolnej **Utwórz** wersję za pomocą jednej z metod konstrukcji.)  
  
     Parametry **Utwórz** są:  
  
    -   "port": krótki liczby całkowitej.  
  
         Dla serwera gniazda należy określić port. Dla gniazda klienta zwykle zaakceptuj wartość domyślną dla tego parametru, który pozwala wybrać port usługi Windows Sockets.  
  
    -   Typ gniazda: **SOCK_STREAM** (ustawienie domyślne) lub **SOCK_DGRAM**.  
  
    -   Gniazdo "address" takie jak "pod adresem" lub "128.56.22.8".  
  
         Jest to adres protokołu internetowego (IP) w sieci. Prawdopodobnie zawsze będzie używana wartość domyślna dla tego parametru.  
  
     Warunki "port" i "adres gniazda" opisano szczegółowo w [Windows Sockets: porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Jeśli klient jest gniazda, obiekt gniazda nawiązują połączenie z serwerem gniazda, za pomocą [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).  
  
     —lub—  
  
     Jeśli gniazda jest serwer, ustaw wartość gniazda rozpoczęcie nasłuchiwania (z [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) prób połączenia z klientem. Po odebraniu żądania połączenia, zaakceptuj ją z [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
     Po zaakceptowaniu połączenia, można wykonywać zadania, takie jak sprawdzanie poprawności hasła.  
  
    > [!NOTE]
    >  **Akceptuj** funkcji członkowskiej przyjmuje odwołanie do nowy, pusty `CSocket` obiektu jako jego parametr. Należy utworzyć ten obiekt przed wywołaniem **Akceptuj**. Jeśli ten obiekt gniazda odbędzie się poza zakresem, zamyka połączenie. Nie wywołuj **Utwórz** dla tego nowego obiektu gniazda. Na przykład, zobacz artykuł [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).  
  
3.  Przeprowadzać komunikacji z innymi sockets przez wywołanie metody `CAsyncSocket` obiektu funkcji elementów członkowskich, które zapewniają funkcje interfejsu API systemu Windows Sockets.  
  
     Zobacz specyfikację Windows Sockets i klasa [CAsyncSocket](../mfc/reference/casyncsocket-class.md) w *odwołania MFC*.  
  
4.  Destroy `CAsyncSocket` obiektu.  
  
     Jeśli utworzono obiekt gniazda na stosie, jego destruktora jest wywoływane, gdy funkcja zawierającego wykracza poza zakres. Obiekt gniazda został utworzony na stosie, za pomocą **nowe** operatora, użytkownik jest odpowiedzialny za pomocą **usunąć** operator do zniszczenia obiektu.  
  
     Destruktor wywołuje metodę obiektu [Zamknij](../mfc/reference/casyncsocket-class.md#close) funkcji członkowskiej przed zniszczenia obiektu.  
  
 Na przykład ta sekwencja w kodzie (faktycznie dla `CSocket` obiektu), zobacz [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Twoje obowiązki z CAsyncSocket  
 Podczas tworzenia obiektu klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), obiekt hermetyzuje Windows **GNIAZDA** obsługi i dostarcza operacji na tym uchwycie. Jeśli używasz `CAsyncSocket`, muszą dotyczyć wszystkich problemów może sprostać Jeśli bezpośrednio za pomocą interfejsu API. Na przykład:  
  
-   Scenariusze "Blokowanie".  
  
-   Bajt kolejności różnice między wysyłanie i odbieranie maszyny.  
  
-   Konwertowanie pomiędzy Unicode i znaków wielobajtowych ustawić ciągi znaków (MBCS).  
  
 Definicje tych warunków i dodatkowe informacje, zobacz [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md), [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md) .  
  
 Pomimo tych problemów klasy **CAsycnSocket** może być odpowiednie opcje dla Ciebie, jeśli aplikacja wymaga elastyczność i sterowania można uzyskać. Jeśli nie, należy rozważyć użycie klasy `CSocket` zamiast tego. `CSocket` ukrywa wiele szczegółowych od Ciebie: it pomp Windows komunikaty podczas blokowania połączeń i umożliwia dostęp do `CArchive`, która zarządza różnice kolejności bajtów i Konwersja ciągu dla Ciebie.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Gniazda systemu Windows: podstawy](../mfc/windows-sockets-background.md)  
  
-   [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)

