---
title: 'Windows Sockets: Sekwencja operacji'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 0f9fd339fdbdfee9381ea693568f40473c2397e9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265551"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets: Sekwencja operacji

W tym artykule przedstawiono obok siebie, sekwencja operacji gniazda serwera i gniazda klienta. Ponieważ jest używany przez gniazdami `CArchive` obiektów, są one zawsze [strumienia sockets](../mfc/windows-sockets-stream-sockets.md).

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Sekwencja operacji komunikacji poprzez gniazdo Stream

Aż do momentu konstruowanie `CSocketFile` obiektu, następująca sekwencja jest dokładne (z kilka różnic parametr) dla obu `CAsyncSocket` i `CSocket`. Od tego momentu sekwencji dotyczy wyłącznie `CSocket`. W poniższej tabeli przedstawiono sekwencja operacji Konfigurowanie komunikacji między klientem a serwerem.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>Konfigurowanie komunikacji między serwerem klientem

|Serwer|Klient|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> —lub—<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> — lub obu —|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> —lub—<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> — lub obu —|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> —lub—<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> —lub—<br /><br /> `arOut << dwValue;`6|

1. Gdzie *nPort* jest numerem portu. Zobacz [Windows Sockets: Porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md) szczegółowe informacje na temat portów.

2. Serwer zawsze należy określić port, dzięki czemu klienci mogą łączyć się. `Create` Wywołanie określa również czasami adresu. Po stronie klienta należy używać parametrów domyślnych, które poproś MFC, aby użyć dowolnego dostępnego portu.

3. Gdzie *nPort* numer portu to a *strAddr* jest adres komputera lub adres protokołu internetowego (IP).

4. Adresy komputera może przybierać różne formy: "pod adresem", "microsoft.com". Adresy IP formularz "kropkowana numer" "127.54.67.32". `Connect` Funkcja sprawdza, czy adres jest liczbą kropkowana (mimo że nie sprawdza ona, aby upewnić się, liczba jest prawidłową maszyna w sieci). W przeciwnym razie `Connect` przyjmuje nazwę komputera w jednej z innych form.

5. Gdy wywołujesz `Accept` po stronie serwera, należy przekazać odwołanie do nowego obiektu gniazda. Należy najpierw utworzyć tego obiektu, ale nie należy wywoływać metody `Create` dla niego. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. MFC łączy nowy obiekt do **GNIAZDA** obsługi. Można skonstruować gniazda na stosie, jak pokazano lub na stosie.

6. Archiwum i plik gniazda są zamykane, gdy wykraczają poza zakres. Ponadto wywołuje destruktora obiektu gniazda [Zamknij](../mfc/reference/casyncsocket-class.md#close) funkcja elementu członkowskiego obiektu gniazda, gdy obiekt wykracza poza zakres lub został usunięty.

## <a name="additional-notes-about-the-sequence"></a>Dodatkowe uwagi dotyczące sekwencji

Sekwencja wywołań przedstawione w powyższej tabeli jest dla gniazda strumieni. Do przesyłania datagramów, które są bez połączenia, nie wymagają [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [nasłuchiwania](../mfc/reference/casyncsocket-class.md#listen), i [Akceptuj](../mfc/reference/casyncsocket-class.md#accept) wywołania (Chociaż możesz opcjonalnie użyć `Connect`). Zamiast tego Jeśli używasz klasy `CAsyncSocket`, datagram gniazd użyj `CAsyncSocket::SendTo` i `ReceiveFrom` funkcji elementów członkowskich. (Jeśli używasz `Connect` na gniazdo datagram używane `Send` i `Receive`.) Ponieważ `CArchive` nie działa z datagramy, nie należy używać `CSocket` z archiwum, w przypadku datagram gniazda.

[CSocketFile](../mfc/reference/csocketfile-class.md) nie obsługuje wszystkich `CFile`firmy funkcjonalności. `CFile` elementów członkowskich, takich jak `Seek`, która nie ma sensu komunikacji gniazda, są niedostępne. W związku z tym niektóre domyślne MFC `Serialize` funkcje nie są zgodne z `CSocketFile`. Jest to szczególnie istotne w `CEditView` klasy. Nie należy próbować serializacji `CEditView` danych za pośrednictwem `CArchive` obiekt dołączony do `CSocketFile` przy użyciu `CEditView::SerializeRaw`; użyj `CEditView::Serialize` zamiast (nie udokumentowano). [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) funkcja oczekuje obiektu pliku, aby funkcje, takie jak `Seek`, które `CSocketFile` nie obsługuje.

Aby uzyskać więcej informacji, zobacz:

- [Windows Sockets: Używanie gniazd z archiwami](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Używanie klasy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Porty i adresy gniazd](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows Sockets: Gniazda Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Do przesyłania datagramów](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Zobacz także

[Gniazda systemu Windows w MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Klasa CSocket](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)
