---
title: 'Windows Sockets: Używanie gniazd z archiwami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295077b474681cabeb1221052ae9e2c9ad5ed79a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053178"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: używanie gniazd z archiwami

W tym artykule opisano [model programowania CSocket](#_core_the_csocket_programming_model). Klasa [CSocket](../mfc/reference/csocket-class.md) dostarcza obsługę gniazda na wyższym poziomie abstrakcji, niż klasa [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` używa wersji protokołu serializacji MFC do przekazywania danych do i z obiektu gniazda za pomocą MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. `CSocket` zapewnia blokuje (podczas obsługi przetwarzania w tle Windows wiadomości) oraz dostęp do `CArchive`, która zarządza wieloma aspektami komunikacji, który będzie trzeba samodzielnie przy użyciu surowego interfejsu API lub klasy `CAsyncSocket`.

> [!TIP]
>  Można użyć klasy `CSocket` przez siebie jako nieco bardziej wygodne `CAsyncSocket`, ale najprostszym modelem programowania jest użycie `CSocket` z `CArchive` obiektu.

Aby uzyskać więcej informacji na temat sposobu działania wdrożenia gniazda z archiwami zobacz [Windows Sockets: jak gniazda z archiwów pracy](../mfc/windows-sockets-how-sockets-with-archives-work.md). Przykładowy kod, zobacz [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md) i [Windows Sockets: przykład z gniazda przy użyciu archiwa](../mfc/windows-sockets-example-of-sockets-using-archives.md). Aby uzyskać informacji na temat niektórych funkcji, aby uzyskać wyprowadzanie własnych klas z klas gniazd, zobacz [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
>  Jeśli piszesz program kliencki MFC do komunikacji z serwerami ustanowionych (inne niż MFC), nie będą wysyłane obiektów C++ w archiwum. Serwer nie działa aplikacji MFC, która rozumie rodzaje obiektów, które chcesz wysłać, nie będą mogą odbierać i deserializacji obiektów. Powiązane materiału na temat komunikowania się z aplikacji innych niż MFC, również znaleźć w artykule [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).

##  <a name="_core_the_csocket_programming_model"></a> Model programowania CSocket

Za pomocą `CSocket` obiektu obejmuje tworzenie i kojarzenie ze sobą kilka obiektów klas MFC. W poniższej procedurze ogólne każdy krok jest zajęta przez gniazdo serwera i gniazda klienta, z wyjątkiem kroku 3, w którym każdy typ gniazda wymaga różne akcje.

> [!TIP]
>  W czasie wykonywania aplikacji serwera rozpoczyna się zwykle najpierw gotowe i "nasłuchiwania", gdy aplikacja kliencka szuka połączenia. Jeśli serwer nie jest gotowy, gdy klient próbuje nawiązać połączenie, zwykle wymagają aplikacji użytkownika i ponów próbę połączenia później.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Aby skonfigurować komunikację między gniazda serwera i gniazda klienta

1. Konstruowania [CSocket](../mfc/reference/csocket-class.md) obiektu.

1. Obiekt używany do tworzenia podstawowych **GNIAZDA** obsługi.

   Dla `CSocket` obiektu klienta, zazwyczaj należy używać parametrów domyślnych do [Utwórz](../mfc/reference/casyncsocket-class.md#create), chyba że potrzebujesz gniazdo datagramu. Aby uzyskać `CSocket` obiektu serwera, należy określić port w `Create` wywołania.

    > [!NOTE]
    >  `CArchive` nie działa z do przesyłania datagramów. Jeśli chcesz używać `CSocket` dla gniazda datagram, należy użyć klasy, jak w przypadku `CAsyncSocket`, to znaczy, bez archiwizacji. Ponieważ nie jest gwarantowane datagramów (nie dotrą do celu i może być powtarzany lub poza sekwencją), nie są zgodne z serializacji, za pomocą archiwum. Możesz oczekiwać na zakończenie niezawodnie i w sekwencji operacji serializacji. Jeśli spróbujesz użyć `CSocket` z `CArchive` obiektu dla datagramu, potwierdzenie MFC nie powiedzie się.

1. Jeśli gniazda klienta, należy wywołać [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) nawiązać obiekt gniazda z gniazda serwera.

     —lub—

   Gniazda w przypadku serwera, wywoływanie [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) umożliwiającą prób nasłuchiwać połączeń z klienta. Po odebraniu żądania połączenia, zaakceptuj je, wywołując [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  `Accept` Funkcja elementu członkowskiego przyjmuje odwołanie do nowy, pusty `CSocket` obiekt jako parametr. Należy utworzyć ten obiekt przed wywołaniem `Accept`. Jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostaje zamknięte. Nie wywołuj `Create` dla tego nowego obiektu gniazda.

1. Tworzenie [CSocketFile](../mfc/reference/csocketfile-class.md) obiektu i kojarzenie `CSocket` obiektu z nim.

1. Tworzenie [CArchive](../mfc/reference/carchive-class.md) obiektu dla ładowania (odbieranie) lub przechowywanie danych (wysyłającym). Archiwum jest skojarzony z `CSocketFile` obiektu.

   Należy pamiętać, że `CArchive` nie działa z do przesyłania datagramów.

1. Użyj `CArchive` obiektu do przekazywania danych między klientem i serwerem gniazda.

   Należy pamiętać, że dany `CArchive` obiektu przenosi dane tylko w jednym kierunku: do ładowania (odbieranie) lub przechowywane (wysyłającym). W niektórych przypadkach użyjesz dwóch `CArchive` obiektów: jeden dla wysyłających dane, druga do odbierania potwierdzenia.

   Po zaakceptowania połączenia i konfigurowania archiwum, można wykonywać zadania, takie jak sprawdzanie poprawności hasła.

1. Zniszcz archiwum, gniazda plików i gniazda obiektów.

    > [!NOTE]
    >  Klasa `CArchive` dostarcza `IsBufferEmpty` funkcja elementu członkowskiego specjalnie dla klasy `CSocket`. Jeśli bufor zawiera wiele wiadomości danych, na przykład, należy w pętli do wszystkich z nich są odczytywane i rozmiar buforu jest wyczyszczone. W przeciwnym razie dalej powiadomienia, że ma danych do odebrania może na czas nieokreślony opóźniona. Użyj `IsBufferEmpty` aby mieć pewność, że można pobrać wszystkich danych.

Artykuł [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md) ilustruje obie strony tego procesu z przykładowym kodem.

Aby uzyskać więcej informacji, zobacz:

- [Gniazda systemu Windows: gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)

- [Gniazda systemu Windows: gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz też

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Create](../mfc/reference/csocket-class.md#create)

