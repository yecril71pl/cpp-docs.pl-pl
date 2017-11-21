---
title: "Windows Sockets: Używanie gniazd z archiwami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3eb7d6c18e1a1fd77e0c0c8506d46536add5cb21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: używanie gniazd z archiwami
W tym artykule opisano [CSocket — model programowania](#_core_the_csocket_programming_model). Klasa [CSocket —](../mfc/reference/csocket-class.md) dostarcza obsługi gniazda na wyższym poziomie abstrakcji niż klasa [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`używana wersja protokołu serializacji MFC do przekazywania danych do i z obiektu gniazda za pomocą MFC [CArchive](../mfc/reference/carchive-class.md) obiektu. `CSocket`Umożliwia blokowanie (podczas zarządzania przetwarzania komunikatów systemu Windows w tle) i umożliwia dostęp do `CArchive`, która zarządza wielu aspektów komunikacji, który będzie musiał wykonać samodzielnie przy użyciu raw interfejsu API albo klasy `CAsyncSocket`.  
  
> [!TIP]
>  Można użyć klasy `CSocket` przez siebie, wersja wygodniejsze `CAsyncSocket`, ale najprostszym modelem programowania jest użycie `CSocket` z `CArchive` obiektu.  
  
 Aby uzyskać więcej informacji na temat stosowania gniazda z archiwami działania, zobacz [Windows Sockets: jak gniazda z archiwów pracy](../mfc/windows-sockets-how-sockets-with-archives-work.md). Na przykład kodu, zobacz [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md) i [Windows Sockets: przykład z gniazda przy użyciu archiwa](../mfc/windows-sockets-example-of-sockets-using-archives.md). Informacje o pewnych funkcji uzyskać wyprowadzanie z klas gniazd własnych klas, zobacz [Windows Sockets: wyprowadzanie z klas gniazd](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
> [!NOTE]
>  Jeśli piszesz program kliencki MFC do komunikacji z serwerami ustalonych (z systemem innym niż MFC) nie należy wysyłać obiektów C++ w archiwum. Chyba, że serwer jest aplikacją MFC obsługującą typy obiektów, które chcesz wysyłać, nie będzie mogła odbierać i deserializacji obiektów. Pokrewnego w zakresie komunikacji z aplikacjami innego typu niż MFC, również w artykule [Windows Sockets: Określanie kolejności bajtów](../mfc/windows-sockets-byte-ordering.md).  
  
##  <a name="_core_the_csocket_programming_model"></a>CSocket — Model programowania  
 Przy użyciu `CSocket` obiektu obejmuje tworzenie i kojarzenie ze sobą kilka obiektów klas MFC. W poniższej procedurze ogólne każdy krok jest zajęta przez gniazda serwera i klienta gniazda, z wyjątkiem kroku 3, w której każdy typ gniazda wymaga różne akcje.  
  
> [!TIP]
>  W czasie wykonywania aplikacja serwera zazwyczaj rozpoczyna najpierw jest gotowa do "nasłuchiwania", gdy aplikacja kliencka ma połączenie. Jeśli serwer nie jest gotowy, gdy klient próbuje nawiązać połączenie, zwykle wymagają aplikacji użytkownika, aby spróbować połączyć się ponownie później.  
  
#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Aby skonfigurować komunikację między gniazda serwera i klienta gniazda  
  
1.  Utworzyć [CSocket —](../mfc/reference/csocket-class.md) obiektu.  
  
2.  Obiekt używany do tworzenia podstawowych **GNIAZDA** obsługi.  
  
     Dla `CSocket` obiektu klienta o normalnie powinno być używane domyślne parametry [Utwórz](../mfc/reference/casyncsocket-class.md#create), chyba że potrzebne gniazda datagramów. Dla `CSocket` obiektu serwera, należy określić port w **Utwórz** wywołania.  
  
    > [!NOTE]
    >  `CArchive`nie działa z gniazda do przesyłania datagramów. Jeśli chcesz użyć `CSocket` dla gniazda datagram, należy użyć klasy, jak w przypadku `CAsyncSocket`, która jest bez archiwizacji. Ponieważ datagramy są zawodnych (nie dotrą do i może zostać powtórzony lub poza sekwencją), nie są zgodne z serializacji za pomocą archiwum. Należy oczekiwać na zakończenie niezawodne i w sekwencji operacji serializacji. Jeśli spróbujesz użyć `CSocket` z `CArchive` obiektu dla datagramu, potwierdzenie MFC nie powiedzie się.  
  
3.  Jeśli klient jest gniazda, wywołanie [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) do nawiązania połączenia gniazda serwera obiektu gniazda.  
  
     —lub—  
  
     Jeśli gniazda jest serwer, wywołanie [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) zacząć prób nasłuchiwania dla połączeń z klienta. Po odebraniu żądania połączenia, zaakceptuj ją przez wywołanie metody [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
    > [!NOTE]
    >  **Akceptuj** funkcji członkowskiej przyjmuje odwołanie do nowy, pusty `CSocket` obiektu jako jego parametr. Należy utworzyć ten obiekt przed wywołaniem **Akceptuj**. Jeśli ten obiekt gniazda odbędzie się poza zakresem, zamyka połączenie. Nie wywołuj **Utwórz** dla tego nowego obiektu gniazda.  
  
4.  Utwórz [CSocketFile](../mfc/reference/csocketfile-class.md) obiekt kojarzenie `CSocket` obiektu z nim.  
  
5.  Utwórz [CArchive](../mfc/reference/carchive-class.md) obiektu (odbieranie) podczas ładowania lub przechowywania danych (wysyłającym). Archiwum jest skojarzony z `CSocketFile` obiektu.  
  
     Należy pamiętać, że `CArchive` nie działa z gniazda do przesyłania datagramów.  
  
6.  Użyj `CArchive` obiektu do przekazywania danych między sockets klienta i serwera.  
  
     Należy pamiętać, że dany `CArchive` obiektu przenosi dane tylko w jednym kierunku: do ładowania (odbieranie) lub przechowywane (wysyłającym). W niektórych przypadkach użyjesz dwóch `CArchive` obiektów: jeden dla wysyłających dane, inne do odbierania potwierdzenia.  
  
     Po zaakceptowania połączenia i ustawianie archiwum, można wykonywać zadania, takie jak sprawdzanie poprawności hasła.  
  
7.  Zniszcz archiwum, pliku gniazda i obiekty gniazda.  
  
    > [!NOTE]
    >  Klasa `CArchive` dostarcza `IsBufferEmpty` funkcji członkowskiej specjalnie dla klasy `CSocket`. Jeśli bufor zawiera wiele danych komunikatów, na przykład należy pętli do wszystkich z nich są odczytywane i bufor jest wyczyszczone. W przeciwnym razie dalej Brak danych do odebrania powiadomienia mogą być nieskończoność opóźnione. Użyj `IsBufferEmpty` aby mieć pewność, że można pobrać wszystkich danych.  
  
 Artykuł [Windows Sockets: Sekwencja operacji](../mfc/windows-sockets-sequence-of-operations.md) przedstawiono obie strony tego procesu z przykładowego kodu.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Windows Sockets: Gniazda strumieni](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Gniazda do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Sockets w MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../mfc/reference/csocket-class.md#create)

