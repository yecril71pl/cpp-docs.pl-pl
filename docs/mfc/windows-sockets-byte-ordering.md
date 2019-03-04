---
title: 'Windows Sockets: Określanie kolejności bajtów'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: ca572ad32a9a46756cacf0221d80b2953b710723
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278096"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Określanie kolejności bajtów

W tym artykule i dwa artykuły pomocnika opisano kilka problemów w programowaniu Windows Sockets. W tym artykule opisano, określanie kolejności bajtów. Inne problemy zostały omówione w artykułach: [Windows Sockets: Blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: Konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).

Jeśli używasz lub pochodzić od klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzania tymi problemami. Jeśli używasz lub pochodzić od klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza je dla Ciebie.

## <a name="byte-ordering"></a>Określanie kolejności bajtów

Architektury innej maszyny są przechowywane dane przy użyciu różnych bajtów zamówienia. Na przykład maszyn opartych na Intel przechowywać dane w kolejności odwrotnej do komputerów Macintosh (Motorola). Kolejność bajtów firmy Intel, o nazwie "little-Endian," jest również odwrotna kolejność "big-Endian" Standardowa sieci. W poniższej tabeli opisano te warunki.

### <a name="big--and-little-endian-byte-ordering"></a>Określanie kolejności bajtów big - i -Endian

|Określanie kolejności bajtów|Znaczenie|
|-------------------|-------------|
|Big-Endian|Najbardziej znaczący bajt znajduje się na końcu po lewej stronie słowa.|
|Little-Endian|Najbardziej znaczący bajt znajduje się na prawym końcu wyrazu.|

Zazwyczaj nie trzeba martwić o kolejność bajtów konwersji danych wysyłanych i odbieranych przez sieć, ale istnieją sytuacje, w których należy przekonwertować zamówienia bajtów.

## <a name="when-you-must-convert-byte-orders"></a>Kiedy należy przekonwertować zamówienia bajtów

Musisz przekonwertować zamówień bajtów w następujących sytuacjach:

- Kończy się sukcesem informacje, które musi być interpretowany przez sieć, a nie dane, które są wysyłane na inny komputer. Na przykład może zostać przekazany portów i adresów, które należy zrozumieć sieci.

- Aplikacja serwera za pomocą którego zachodzi komunikacja nie jest aplikacji MFC (i nie masz kodu źródłowego dla niego). To wywołanie podczas konwersji kolejności bajtów, jeśli dwa komputery nie mają taką samą kolejnością bajtów.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Jeśli nie masz do przekonwertowania zamówienia bajtów

Można uniknąć pracy Konwertowanie zamówień bajtów w następujących sytuacjach:

- Maszyny na obu końcach można zaakceptować nie zamienić bajtów i obie maszyny, użyj takiej samej kolejności bajtów.

- Serwer, który komunikują się z to aplikację MFC.

- Masz kod źródłowy dla serwera, który jest komunikacji, dzięki czemu można sprawdzić jawnie czy należy przekonwertować zamówienia bajtów, czy nie.

- Można portu serwera z MFC. Jest to dość łatwe, a wynik jest zazwyczaj mniejszy, szybszy kod.

Praca z [CAsyncSocket](../mfc/reference/casyncsocket-class.md), wszystkie konwersje niezbędne kolejności bajtów musi zarządzać samodzielnie. Windows Sockets standaryzuje modelu kolejności bajtów "big-Endian" i udostępnia funkcje do konwersji między to zamówienie i innych. [CArchive](../mfc/reference/carchive-class.md), jednak używane z [CSocket](../mfc/reference/csocket-class.md), używa kolejności przeciwnej ("little-Endian"), ale `CArchive` dba o szczegółowe informacje o konwersji kolejności bajtów dla Ciebie. Za pomocą tego standardowego kolejność w swoich aplikacjach, lub przy użyciu funkcji konwersji kolejności bajtów Windows Sockets, można wprowadzić kod bardziej przenośny.

W idealnym rozwiązaniem w przypadku używanie gniazd MFC jest pisanego obu końcach komunikacji: używanie MFC na obu końcach. Jeśli piszesz aplikację, która będzie komunikować się z aplikacji innych niż MFC, takich jak serwer FTP, prawdopodobnie musisz zarządzać wymienianie bajtów samodzielnie przed przekazywanie danych do obiektu archiwum, przy użyciu procedur konwersji Windows Sockets **ntohs**, **ntohl**, **htons**, i **htonl**. Te funkcje używane podczas komunikacji z aplikacją innego typu niż MFC jest wyświetlany w dalszej części tego artykułu.

> [!NOTE]
>  Po drugiej stronie komunikacja nie jest aplikacja MFC, musisz również unikać przesyłania strumieniowego obiektów C++ pochodzących od `CObject` do archiwum ponieważ odbiornik nie będzie mógł je obsłużyć. Zobacz uwagi w [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md).

Aby uzyskać więcej informacji o zamówieniach bajtów zobacz specyfikację Windows Sockets, dostępne w zestawie Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Przykład konwersji kolejności bajtów

W poniższym przykładzie pokazano funkcję serializacji dla `CSocket` obiektu, który używa archiwum. Ilustruje też, przy użyciu funkcji konwersji kolejność bajtów w interfejsie API Windows Sockets.

W tym przykładzie przedstawiono scenariusz, w którym piszesz klienta, który komunikuje się z innego typu niż MFC aplikacji serwera, dla którego nie masz dostępu do kodu źródłowego. W tym scenariuszu należy zakładać, że serwer innego typu niż MFC używa kolejności bajtów standardowej sieci. Z kolei używa aplikacji klienckiej MFC `CArchive` obiekt z `CSocket` obiektu, a `CArchive` używa kolejności bajtów "little-Endian", to odwrotność wzorca sieci standard.

Załóżmy, że serwer innego typu niż MFC, za pomocą którego planujesz komunikacji ma ustanowionych protokół pakietu komunikatu, jak pokazano poniżej:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

W warunkach MFC to może być wyrażona w następujący sposób:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

W języku C++ **struktury** jest zasadniczo tak samo jak klasy. `Message` Struktura może mieć funkcje Członkowskie, takich jak `Serialize` funkcji składowej zadeklarowanej powyżej. `Serialize` Funkcji składowej może wyglądać następująco:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Ten przykład wywołuje podczas konwersji kolejności bajtów danych, ponieważ wystąpiła niezgodność wyczyść między kolejność bajtów aplikacji serwera innego typu niż MFC na jednym końcu i `CArchive` używane w aplikacji klienckiej MFC na drugim końcu. W przykładzie pokazano kilka funkcji konwersji kolejności bajtów, które dostarcza Windows Sockets. W poniższej tabeli opisano te funkcje.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets funkcje konwersji kolejności bajtów

|Funkcja|Cel|
|--------------|-------------|
|**ntohs**|Konwertuj ilość 16-bitowych w kolejności bajtów sieci na hosta kolejności bajtów (big-Endian do little-Endian).|
|**ntohl**|Konwertować ilość 32-bitowy z kolejności bajtów sieci na hoście kolejności bajtów (big-Endian do little-Endian).|
|**Htons**|Konwertuj ilość 16-bitowych w kolejności bajtów hosta na kolejności bajtów sieci (little-Endian do big-Endian).|
|**Htonl**|Przekonwertować ilość 32-bitowych w kolejności bajtów hosta sieci kolejności bajtów (little-Endian do big-Endian).|

Innego punktu w tym przykładzie jest to, gdy aplikacja gniazda na drugim końcu komunikacji znajduje się aplikacja innego typu niż MFC, należy unikać wykonywania podobny do poniższego:

`ar << pMsg;`

gdzie `pMsg` jest wskaźnikiem do obiektu języka C++, pochodzi z klasy `CObject`. To będzie wysyłać informacje dodatkowe MFC związane z obiektami i serwer nie rozumieją, jak gdyby była aplikacji MFC.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Tło](../mfc/windows-sockets-background.md)

- [Windows Sockets: Gniazda Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)
