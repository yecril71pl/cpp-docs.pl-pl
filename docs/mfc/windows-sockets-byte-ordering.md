---
title: 'Windows Sockets: określanie kolejności bajtów'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: f00936f3de07df8c1e4d9df1c678b2cfd5f3e3ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226805"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: określanie kolejności bajtów

Ten artykuł i dwa artykuły towarzyszące wyjaśniają kilka problemów dotyczących programowania Windows Sockets. W tym artykule omówiono porządkowanie bajtów. Inne problemy zostały omówione w artykułach: [Windows Sockets: blokowanie](../mfc/windows-sockets-blocking.md) i [Windows Sockets: konwertowanie ciągów](../mfc/windows-sockets-converting-strings.md).

Jeśli używasz lub pochodzi z klasy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzać tymi problemami. Jeśli używasz lub dziedziczysz z klasy [CSocket](../mfc/reference/csocket-class.md), MFC zarządza nimi.

## <a name="byte-ordering"></a>określanie kolejności bajtów

Różne architektury maszyn czasami przechowują dane przy użyciu różnych kolejności bajtów. Na przykład maszyny oparte na architekturze Intel przechowują dane w odwrotnej kolejności komputerów Macintosh. Kolejność bajtów Intel o nazwie "Little-Endian" jest również odwrotną kolejnością standardowego "Big-Endian" sieci. W poniższej tabeli opisano te warunki.

### <a name="big--and-little-endian-byte-ordering"></a>Porządkowanie bajtów big-i little-endian

|określanie kolejności bajtów|Znaczenie|
|-------------------|-------------|
|Big-endian|Najbardziej znaczący bajt jest z lewej strony wyrazu.|
|Little-endian|Najbardziej znaczący bajt znajduje się po prawej stronie wyrazu.|

Zazwyczaj nie trzeba martwić się o konwersję kolejności bajtów dla danych wysyłanych i odbieranych przez sieć, ale istnieją sytuacje, w których należy przekonwertować zamówienia bajtów.

## <a name="when-you-must-convert-byte-orders"></a>Gdy konieczne jest przekonwertowanie zamówień bajtów

Należy przekonwertować kolejność bajtów w następujących sytuacjach:

- Przekazujesz informacje, które należy interpretować przez sieć, w przeciwieństwie do danych wysyłanych na inny komputer. Można na przykład przekazać porty i adresy, które Sieć musi zrozumieć.

- Aplikacja serwera, z którą komunikujesz się, nie jest aplikacją MFC (i nie masz dla niej kodu źródłowego). To wywołuje konwersje kolejności bajtów, jeśli dwie komputery nie mają tej samej kolejności bajtów.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Gdy nie musisz konwertować kolejności bajtów

Można uniknąć wykonywania konwersji kolejności bajtów w następujących sytuacjach:

- Komputery na obu końcach mogą wyrazić zgodę na nie zamienić bajtów, a oba komputery używają tego samego kolejności bajtów.

- Serwer, z którym nawiązujesz połączenie, jest aplikacją MFC.

- Masz kod źródłowy dla serwera, z którym nawiązujesz połączenie, aby można było jawnie określić, czy należy przekonwertować zamówienia bajtów.

- Serwer można przenieść do biblioteki MFC. Jest to dość proste, a wynikiem jest zazwyczaj mniejszy, szybszy kod.

Pracując z [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musisz samodzielnie zarządzać wszelkimi niezbędnymi konwersjami kolejności bajtów. Windows Sockets ma ustandaryzowany model kolejności bajtów "Big-Endian" i oferuje funkcje do konwersji między tą kolejnością i innymi. [CArchive](../mfc/reference/carchive-class.md), jednak używany z [CSocket](../mfc/reference/csocket-class.md), używa przeciwległej kolejności ("Little-Endian"), ale należy `CArchive` pamiętać o szczegółach konwersji kolejności bajtów. Używając tej standardowej kolejności w aplikacjach lub korzystając z funkcji konwersji kolejności bajtów Windows Sockets, można sprawić, że kod będzie bardziej przenośny.

Idealnym przypadkiem korzystania z funkcji MFC Sockets jest zapisanie obu punktów końcowych komunikacji: przy użyciu MFC w obu końcach. Jeśli piszesz aplikację, która będzie komunikować się z aplikacjami nienależącymi do MFC, takimi jak serwer FTP, prawdopodobnie trzeba będzie zarządzać zamienianiem bajtów samodzielnie przed przekazaniem danych do obiektu archiwum przy użyciu procedur konwersji Windows Sockets **ntohs**, **ntohl**, **htons**i **htonl**. Przykład tych funkcji używanych podczas komunikacji z aplikacją niebędącą MFC jest wyświetlany w dalszej części tego artykułu.

> [!NOTE]
> Gdy inne zakończenie komunikacji nie jest aplikacją MFC, należy również unikać przesyłania strumieniowego obiektów C++ pochodzących z `CObject` do archiwum, ponieważ odbiornik nie będzie mógł ich obsłużyć. Zapoznaj się z uwagą w [systemie Windows Sockets: używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md).

Aby uzyskać więcej informacji na temat zamówień bajtów, zobacz specyfikację Windows Sockets dostępną w Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Przykład konwersji z kolejnością bajtów

Poniższy przykład pokazuje funkcję serializacji dla `CSocket` obiektu, który używa archiwum. Ilustruje także użycie funkcji konwersji kolejności bajtów w interfejsie API Windows Sockets.

W tym przykładzie przedstawiono scenariusz, w którym piszesz klienta, który komunikuje się z aplikacją serwera innej niż MFC, dla której nie masz dostępu do kodu źródłowego. W tym scenariuszu należy założyć, że serwer inny niż MFC używa standardowej kolejności bajtów sieciowych. W przeciwieństwie do aplikacji klienckiej MFC używa `CArchive` obiektu z `CSocket` obiektem i `CArchive` używa kolejności bajtów "Little-Endian", przeciwieństwem standardu sieci.

Załóżmy, że serwer spoza MFC, z którym planujesz się komunikować, ma ustanowiony protokół dla pakietu komunikatów, podobny do następującego:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

W terminologii MFC można ją wyrazić w następujący sposób:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

W języku C++, **`struct`** jest zasadniczo taka sama jak Klasa. `Message`Struktura może mieć funkcje członkowskie, takie jak `Serialize` funkcja członkowska zadeklarowana powyżej. `Serialize`Funkcja członkowska może wyglądać następująco:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Ten przykład wywołuje konwersję kolejności bajtów danych, ponieważ istnieje wyraźna niezgodność między kolejnością bajtów aplikacji serwera innego niż MFC na jednym końcu i `CArchive` używanej w aplikacji klienckiej MFC na drugim końcu. Przykład ilustruje kilka funkcji konwersji kolejności bajtów dostarczanych przez gniazda Windows Sockets. W poniższej tabeli opisano te funkcje.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Funkcje konwersji kolejności bajtów Windows Sockets

|Funkcja|Przeznaczenie|
|--------------|-------------|
|**ntohs**|Przekonwertuj liczbę 16-bitową z kolejności bajtów sieciowych na hostowanie kolejności bajtów (big-endian do little-endian).|
|**ntohl**|Przekonwertuj liczbę 32-bitową z kolejności bajtów sieciowych na hostowanie kolejności bajtów (big-endian do little-endian).|
|**Htons**|Przekonwertuj liczbę 16-bitową z kolejności bajtów hosta na kolejność bajtów sieci (little-endian do big-endian).|
|**Htonl**|Przekonwertuj liczbę 32-bitową z kolejności bajtów hosta na kolejność bajtów sieci (little-endian do big-endian).|

Innym punktem tego przykładu jest to, że gdy aplikacja gniazda na drugiej stronie komunikacji nie jest aplikacją MFC, należy unikać wykonywania następujących czynności:

`ar << pMsg;`

gdzie `pMsg` jest wskaźnikiem do obiektu języka C++ pochodnego od klasy `CObject` . Spowoduje to wysłanie dodatkowych informacji MFC skojarzonych z obiektami, które nie będą zrozumiałe dla serwera, ponieważ będzie to miało zastosowanie do aplikacji MFC.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Tło](../mfc/windows-sockets-background.md)

- [Windows Sockets: gniazda strumienia](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: gniazda datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)
