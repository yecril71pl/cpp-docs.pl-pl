---
title: 'Windows Sockets: używanie gniazd z archiwami'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359949"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: używanie gniazd z archiwami

W tym artykule opisano [model programowania CSocket](#_core_the_csocket_programming_model). Klasa [CSocket](../mfc/reference/csocket-class.md) dostarcza obsługę gniazda na wyższym poziomie abstrakcji niż klasa [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`używa wersji protokołu serializacji MFC do przekazywania danych do i z obiektu gniazda za pośrednictwem obiektu MFC [CArchive.](../mfc/reference/carchive-class.md) `CSocket`zapewnia blokowanie (podczas zarządzania przetwarzaniem w tle `CArchive`wiadomości systemu Windows) i daje dostęp do , który zarządza wieloma `CAsyncSocket`aspektami komunikacji, które trzeba zrobić samodzielnie za pomocą surowego interfejsu API lub klasy .

> [!TIP]
> Można użyć `CSocket` klasy samodzielnie, jako wygodniejszej wersji `CAsyncSocket`programu , ale `CSocket` najprostszym `CArchive` modelem programowania jest użycie z obiektem.

Aby uzyskać więcej informacji o tym, jak działa implementacja gniazd z archiwami, zobacz [Gniazda systemu Windows: Jak działają gniazda z archiwami](../mfc/windows-sockets-how-sockets-with-archives-work.md). Na przykład kod, zobacz [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) i Windows [Sockets: Przykład gniazd przy użyciu archiwów](../mfc/windows-sockets-example-of-sockets-using-archives.md). Aby uzyskać informacje na temat niektórych funkcji, które można uzyskać, wyprowadzając własne klasy z klas gniazd, zobacz [Gniazda systemu Windows: Pochodne z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Jeśli piszesz program kliencki MFC do komunikowania się z ustalonymi serwerami (nie-MFC), nie wysyłaj obiektów C++ za pośrednictwem archiwum. Chyba że serwer jest aplikacją MFC, która rozumie rodzaje obiektów, które chcesz wysłać, nie będzie w stanie odbierać i deserializacji obiektów. Dla powiązanych materiałów na temat komunikowania się z aplikacjami innych niż MFC, zobacz także artykuł [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>Model programowania CSocket

Za `CSocket` pomocą obiektu obejmuje tworzenie i kojarzenie ze sobą kilka obiektów klasy MFC. W ogólnej procedurze poniżej każdy krok jest podejmowana przez gniazdo serwera i gniazdo klienta, z wyjątkiem kroku 3, w którym każdy typ gniazda wymaga innej akcji.

> [!TIP]
> W czasie wykonywania aplikacja serwera zwykle uruchamia się najpierw, aby być gotowym i "nasłuchiwaniem", gdy aplikacja kliencka szuka połączenia. Jeśli serwer nie jest gotowy, gdy klient próbuje się połączyć, zazwyczaj wymaga się, aby aplikacja użytkownika, aby spróbować połączyć się ponownie później.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Aby skonfigurować komunikację między gniazdem serwera a gniazdem klienta

1. Konstruuj [obiekt CSocket.](../mfc/reference/csocket-class.md)

1. Użyj obiektu, aby utworzyć podstawowy uchwyt **SOCKET.**

   W `CSocket` przypadku obiektu klienta zwykle należy używać parametrów domyślnych do [tworzenia](../mfc/reference/casyncsocket-class.md#create), chyba że potrzebne jest gniazdo datagramu. W `CSocket` przypadku obiektu serwera należy określić `Create` port w wywołaniu.

    > [!NOTE]
    >  `CArchive`nie działa z gniazdami datagramu. Jeśli chcesz użyć `CSocket` dla gniazda datagramu, należy użyć klasy, jak można użyć `CAsyncSocket`, to znaczy, bez archiwum. Ponieważ datagramy są zawodne (nie gwarantuje się dotrzeć i mogą być powtarzane lub poza kolejnością), nie są one zgodne z serializacji za pośrednictwem archiwum. Można oczekiwać, że operacja serializacji zakończyć niezawodnie i w sekwencji. Jeśli spróbujesz `CSocket` użyć `CArchive` obiektu dla datagramu, potwierdzenie MFC kończy się niepowodzeniem.

1. Jeśli gniazdo jest klientem, wywołaj [CAsyncSocket::Connect,](../mfc/reference/casyncsocket-class.md#connect) aby podłączyć obiekt gniazda do gniazda serwera.

     — lub —

   Jeśli gniazdo jest serwerem, wywołaj [CAsyncSocket::Listen,](../mfc/reference/casyncsocket-class.md#listen) aby rozpocząć nasłuchiwanie prób połączenia z klienta. Po otrzymaniu żądania połączenia, zaakceptuj go, dzwoniąc [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  Funkcja `Accept` elementu członkowskiego przyjmuje odwołanie do `CSocket` nowego, pustego obiektu jako parametru. Należy skonstruować ten obiekt `Accept`przed wywołaniem . Jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie należy `Create` wywoływać tego nowego obiektu gniazda.

1. Utwórz obiekt [CSocketFile,](../mfc/reference/csocketfile-class.md) `CSocket` kojarząc z nim obiekt.

1. Utwórz [CArchive](../mfc/reference/carchive-class.md) obiektu do ładowania (odbieranie) lub przechowywania (wysyłanie) danych. Archiwum jest skojarzone `CSocketFile` z obiektem.

   Należy pamiętać, `CArchive` że nie działa z gniazdami datagramu.

1. Obiekt `CArchive` służy do przekazywania danych między gniazdami klienta i serwera.

   Należy pamiętać, że `CArchive` dany obiekt przenosi dane tylko w jednym kierunku: do ładowania (odbierania) lub przechowywania (wysyłania). W niektórych przypadkach użyjesz dwóch `CArchive` obiektów: jednego do wysyłania danych, drugiego do odbierania potwierdzeń.

   Po zaakceptowaniu połączenia i skonfigurowaniu archiwum można wykonywać takie zadania, jak sprawdzanie poprawności haseł.

1. Zniszcz obiekty archiwum, pliku gniazda i gniazda.

    > [!NOTE]
    >  Klasa `CArchive` dostarcza `IsBufferEmpty` funkcję elementu członkowskiego specjalnie `CSocket`do użytku z klasą . Jeśli bufor zawiera wiele komunikatów danych, na przykład należy pętli, dopóki wszystkie z nich są odczytywane i bufor jest wyczyszczone. W przeciwnym razie następne powiadomienie, że istnieją dane do odebrania, może być bezterminowo opóźnione. Służy `IsBufferEmpty` do zapewnienia, że można pobrać wszystkie dane.

Artykuł [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) ilustruje obie strony tego procesu za pomocą przykładowego kodu.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Tworzenie](../mfc/reference/csocket-class.md#create)
