---
title: Klasa CAsyncSocket
ms.date: 09/03/2019
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
ms.openlocfilehash: 4e14052d400268a8852298113ba9b51fda713dc8
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273790"
---
# <a name="casyncsocket-class"></a>Klasa CAsyncSocket

Reprezentuje gniazdo systemu Windows — punkt końcowy komunikacji sieciowej.

## <a name="syntax"></a>Składnia

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket:: CAsyncSocket](#casyncsocket)|Konstruuje `CAsyncSocket` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket:: Accept](#accept)|Akceptuje połączenie w gnieździe.|
|[CAsyncSocket:: AsyncSelect](#asyncselect)|Żąda powiadomienia o zdarzeniu dla gniazda.|
|[CAsyncSocket:: Attach](#attach)|Dołącza uchwyt gniazda do `CAsyncSocket` obiektu.|
|[CAsyncSocket:: bind](#bind)|Kojarzy adres lokalny z gniazdem.|
|[CAsyncSocket:: Close](#close)|Zamyka gniazdo.|
|[CAsyncSocket:: Connect](#connect)|Ustanawia połączenie z gniazdem równorzędnym.|
|[CAsyncSocket:: Create](#create)|Tworzy gniazdo.|
|[CAsyncSocket::Detach](#detach)|Odłączanie uchwytu gniazda z `CAsyncSocket` obiektu.|
|[CAsyncSocket:: FromHandle](#fromhandle)|Zwraca wskaźnik do `CAsyncSocket` obiektu, w którym znajduje się uchwyt gniazda.|
|[CAsyncSocket:: GetLastError](#getlasterror)|Pobiera stan błędu ostatniej operacji, która zakończyła się niepowodzeniem.|
|[CAsyncSocket:: getpeername](#getpeername)|Pobiera adres gniazda równorzędnego, z którym jest połączone gniazdo.|
|[CAsyncSocket:: GetPeerNameEx](#getpeernameex)|Pobiera adres gniazda równorzędnego, z którym jest połączone gniazdo (obsługuje adresy IPv6).|
|[CAsyncSocket:: GetSockName](#getsockname)|Pobiera nazwę lokalną dla gniazda.|
|[CAsyncSocket:: GetSockNameEx](#getsocknameex)|Pobiera nazwę lokalną dla gniazda (obsługuje adresy IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Pobiera opcję gniazda.|
|[CAsyncSocket:: IOCtl](#ioctl)|Kontroluje tryb gniazda.|
|[CAsyncSocket:: Listen](#listen)|Ustanawia gniazdo do nasłuchiwania przychodzących żądań połączeń.|
|[CAsyncSocket:: Receive](#receive)|Odbiera dane z gniazda.|
|[CAsyncSocket:: ReceiveFrom](#receivefrom)|Odbiera datagram i przechowuje adres źródłowy.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Odbiera datagram i przechowuje adres źródłowy (obsługuje adresy IPv6).|
|[CAsyncSocket:: Send](#send)|Wysyła dane do połączonego gniazda.|
|[CAsyncSocket::SendTo](#sendto)|Wysyła dane do określonego miejsca docelowego.|
|[CAsyncSocket::SendToEx](#sendtoex)|Wysyła dane do określonego miejsca docelowego (obsługuje adresy IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Ustawia opcję gniazda.|
|[CAsyncSocket:: ShutDown](#shutdown)|Wyłącza `Send` i/lub `Receive` wywołuje w gnieździe.|
|[CASyncSocket:: Socket](#socket)|Przydziela obsługę gniazda.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket:: OnAccept](#onaccept)|Powiadamia gniazdo nasłuchiwania, które może akceptować oczekujące żądania połączenia `Accept`przez wywołanie.|
|[CAsyncSocket:: OnClose](#onclose)|Powiadamia gniazdo, że gniazdo podłączone do niego zostało zamknięte.|
|[CAsyncSocket:: OnConnect](#onconnect)|Powiadamia gniazdo łączące, że próba nawiązania połączenia kończy się powodzeniem lub błędem.|
|[CAsyncSocket:: OnOutOfBandData](#onoutofbanddata)|Powiadamia gniazdo odbiorcze, że dane poza pasmem są odczytywane w gnieździe, zazwyczaj jest to komunikat pilny.|
|[CAsyncSocket:: OnReceive](#onreceive)|Powiadamia gniazdo nasłuchujące, że dane mają być pobierane przez wywołanie `Receive`.|
|[CAsyncSocket:: OnSend](#onsend)|Powiadamia gniazdo, że może wysyłać dane przez wywołanie `Send`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket:: operator =](#operator_eq)|Przypisuje nową wartość do `CAsyncSocket` obiektu.|
|[CAsyncSocket:: operator — gniazdo](#operator_socket)|Użyj tego operatora, aby pobrać uchwyt `CAsyncSocket` gniazda obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Wskazuje dojście gniazda dołączone do tego `CAsyncSocket` obiektu.|

## <a name="remarks"></a>Uwagi

Klasa `CAsyncSocket` hermetyzuje interfejs API funkcji gniazda systemu Windows, zapewniając abstrakcję zorientowaną obiektowo dla programistów, którzy chcą korzystać z Windows Sockets w połączeniu z MFC.

Ta klasa jest oparta na założeniu, że rozumiesz komunikację sieciową. Użytkownik jest odpowiedzialny za obsługę blokowania, różnic w kolejności bajtów i konwersji między ciągami Unicode i wielobajtowym zestawem znaków (MBCS). Jeśli potrzebujesz bardziej wygodnego interfejsu, który zarządza tymi problemami, zobacz Klasa [CSocket](../../mfc/reference/csocket-class.md).

Aby użyć `CAsyncSocket` obiektu, wywołaj jego konstruktora, a następnie wywołaj funkcję [Create](#create) , aby utworzyć bazowe dojście gniazda `SOCKET`(typ), z wyjątkiem zaakceptowanych gniazd. W przypadku gniazda serwerowego wywołaj funkcję elementu członkowskiego [Listen](#listen) i dla gniazda klienta wywołaj funkcję [łączenie](#connect) elementu członkowskiego. Gniazdo serwera powinno wywołać funkcję [Accept](#accept) po odebraniu żądania połączenia. Użyj pozostałych `CAsyncSocket` funkcji do przeprowadzenia komunikacji między gniazdami. Po zakończeniu Zniszcz `CAsyncSocket` obiekt, jeśli został utworzony na stercie. destruktor automatycznie wywołuje funkcję [Close](#close) . Typ danych gniazda został opisany w artykule [Windows Sockets: Tło](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  W przypadku korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC `AfxSocketInit` należy wywołać w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Korzystanie z CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) klas i powiązanych artykułów, a także [interfejsu API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AfxSock. h

##  <a name="accept"></a>CAsyncSocket:: Accept

Wywołaj tę funkcję elementu członkowskiego, aby zaakceptować połączenie w gnieździe.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parametry

*rConnectedSocket*<br/>
Odwołanie identyfikujące nowe gniazdo, które jest dostępne do połączenia.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , który odbiera adres połączonego gniazda, zgodnie z opisem w sieci. Dokładny Format argumentu *lpSockAddr* jest określany przez rodzinę adresów ustanowioną podczas tworzenia gniazda. Jeśli *lpSockAddr* i/lub *LPSOCKADDRLEN* są równe null, to nie jest zwracana żadna informacja o adresie zdalnym zaakceptowanego gniazda.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. *LpSockAddrLen* jest parametrem wyniku wartości: powinien początkowo zawierać ilość miejsca wskazywanego przez *lpSockAddr*; po zwróceniu będzie zawierać rzeczywistą Długość (w bajtach) zwróconego adresu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS blokowanie wywołania Windows Sockets jest w toku.

- WSAEINVAL `Listen` nie została wywołana przed zaakceptowaniem.

- WSAEMFILE kolejka jest pusta, gdy wpis zostanie zaakceptowany i nie ma dostępnych deskryptorów.

- WSAENOBUFS Brak dostępnego miejsca w buforze.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- WSAEOPNOTSUPP gniazdo, do którego istnieje odwołanie, nie jest typem, który obsługuje usługi zorientowane na połączenia.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokujące i nie ma żadnych połączeń do zaakceptowania.

### <a name="remarks"></a>Uwagi

Ta procedura wyodrębnia pierwsze połączenie w kolejce oczekujących połączeń, tworzy nowe gniazdo z tymi samymi właściwościami co to gniazdo i dołącza je do *rConnectedSocket*. Jeśli w kolejce nie ma żadnych oczekujących połączeń, `Accept` funkcja zwróci wartość `GetLastError` zero i zwróci błąd. Nie można użyć zaakceptowanego gniazda ( *rConnectedSocket)* w celu zaakceptowania większej liczby połączeń. Oryginalne gniazdo pozostaje otwarte i nasłuchuje.

Argument *lpSockAddr* jest parametrem wynikowym, który jest wypełniany adresem połączonego gniazda, tak jak w przypadku warstwy komunikacji. `Accept`jest używany z typami gniazd opartymi na połączeniach, takimi jak SOCK_STREAM.

##  <a name="asyncselect"></a>CAsyncSocket:: AsyncSelect

Wywołaj tę funkcję elementu członkowskiego, aby zażądać powiadomienia o zdarzeniu dla gniazda.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*lEvent*<br/>
Maska bitów, która określa kombinację zdarzeń sieci, w których interesuje aplikacja.

- FD_READ chcą otrzymywać powiadomienia o gotowości do odczytu.

- FD_WRITE chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.

- FD_OOB chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT chcesz otrzymywać powiadomienia o wynikach połączenia.

- FD_CLOSE chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEINVAL wskazuje, że jeden z określonych parametrów jest nieprawidłowy.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określania, które funkcje powiadomień wywołania zwrotnego MFC będą wywoływane dla gniazda. `AsyncSelect`automatycznie ustawia ten gniazdo na tryb niezablokowany. Aby uzyskać więcej informacji, zobacz artykuł [Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

##  <a name="attach"></a>CAsyncSocket:: Attach

Wywołaj tę funkcję elementu członkowskiego, aby dołączyć dojście *hSocket* do `CAsyncSocket` obiektu.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera uchwyt do gniazda.

*lEvent*<br/>
Maska bitów, która określa kombinację zdarzeń sieci, w których interesuje aplikacja.

- FD_READ chcą otrzymywać powiadomienia o gotowości do odczytu.

- FD_WRITE chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.

- FD_OOB chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT chcesz otrzymywać powiadomienia o wynikach połączenia.

- FD_CLOSE chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie.

### <a name="remarks"></a>Uwagi

Uchwyt gniazda jest przechowywany w elemencie członkowskim danych [m_hSocket](#m_hsocket) obiektu.

##  <a name="bind"></a>CAsyncSocket:: bind

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć adres lokalny z gniazdem.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Port identyfikujący aplikację gniazda.

*lpszSocketAddress*<br/>
Adres sieciowy, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu o wartości null dla tego parametru wskazuje `CAsyncSocket` , że wystąpienie powinno nasłuchiwać aktywności klienta na wszystkich interfejsach sieciowych.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , która zawiera adres, który ma zostać przypisany do tego gniazda.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Poniższa lista zawiera kilka błędów, które mogą zostać zwrócone. Aby uzyskać pełną listę, zobacz [kody błędów usługi Windows Sockets](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEADDRINUSE określony adres jest już używany. (Zobacz opcję SO_REUSEADDR Socket w obszarze [SetSockOpt](#setsockopt)).

- WSAEFAULT argument *nSockAddrLen* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS blokowanie wywołania Windows Sockets jest w toku.

- WSAEAFNOSUPPORT określona Rodzina adresów nie jest obsługiwana przez ten port.

- WSAEINVAL gniazdo jest już powiązane z adresem.

- WSAENOBUFS jest za mało dostępnych buforów, za dużo połączeń.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Ta procedura jest używana w niepołączonym datagramie lub gnieździe Stream przed `Connect` kolejnymi lub `Listen` wywołaniami. Aby umożliwić akceptowanie żądań połączeń, nasłuchiwanie gniazda serwera musi wybrać numer portu i określić, że jest on znany dla gniazd `Bind`Windows Sockets przez wywołanie. `Bind`ustanawia lokalne skojarzenie (adres hosta/numer portu) gniazda przez przypisanie lokalnej nazwy do nienazwanego gniazda.

##  <a name="casyncsocket"></a>CAsyncSocket:: CAsyncSocket

Konstruuje pusty obiekt gniazda.

```
CAsyncSocket();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy wywołać jego `Create` funkcję członkowską, aby utworzyć strukturę danych gniazda i powiązać jej adres. (Po stronie serwera komunikacji Windows Sockets, gdy gniazdo nasłuchiwania tworzy gniazdo do użycia w `Accept` wywołaniu, nie jest wywoływana `Create` dla tego gniazda).

##  <a name="close"></a>CAsyncSocket:: Close

Zamyka gniazdo.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zwalnia deskryptor gniazda, dzięki czemu dalsze odwołania do niego będą kończyć się niepowodzeniem z powodu błędu WSAENOTSOCK. Jeśli jest to ostatnie odwołanie do bazowego gniazda, skojarzone informacje o nazewnictwie i dane znajdujące się w kolejce są odrzucane. Destruktor obiektu gniazda wywołuje `Close` Cię.

W `CAsyncSocket`przypadku, ale nie `CSocket`dla `Close` , semantyki ma wpływ Opcje gniazda SO_LINGER i SO_DONTLINGER. Aby uzyskać więcej informacji, zobacz Funkcja `GetSockOpt`członkowska.

##  <a name="connect"></a>CAsyncSocket:: Connect

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie z niepołączonym strumieniem lub gniazdem datagramu.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parametry

*lpszHostAddress*<br/>
Adres sieciowy gniazda, z którym jest połączony ten obiekt: Nazwa komputera, taka jak "ftp.microsoft.com" lub cyfra kropkowana, taka jak "128.56.22.8".

*nHostPort*<br/>
Port identyfikujący aplikację gniazda.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , która zawiera adres połączonego gniazda.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Jeśli wskazuje to na kod błędu WSAEWOULDBLOCK, a aplikacja używa zaszeregowania wywołania zwrotnego, aplikacja otrzyma `OnConnect` komunikat po zakończeniu operacji łączenia. Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEADDRINUSE określony adres jest już używany.

- WSAEINPROGRESS blokowanie wywołania Windows Sockets jest w toku.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny na komputerze lokalnym.

- Adresów WSAEAFNOSUPPORT w określonej rodzinie nie można używać w tym gnieździe.

- WSAECONNREFUSED próba nawiązania połączenia została odrzucona.

- WSAEDESTADDRREQ jest wymagany adres docelowy.

- WSAEFAULT argument *nSockAddrLen* jest niepoprawny.

- WSAEINVAL nieprawidłowy adres hosta.

- WSAEISCONN gniazdo jest już połączone.

- WSAEMFILE nie ma więcej dostępnych deskryptorów plików.

- WSAENETUNREACH w tej chwili nie można nawiązać połączenia z siecią.

- WSAENOBUFS Brak dostępnego miejsca w buforze. Nie można nawiązać połączenia z gniazdem.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- WSAETIMEDOUT podjęto próbę nawiązania połączenia bez nawiązania połączenia.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe, a połączenie nie może zostać zakończone natychmiast.

### <a name="remarks"></a>Uwagi

Jeśli gniazdo jest niepowiązane, unikatowe wartości są przypisywane do lokalnego skojarzenia przez system, a gniazdo jest oznaczone jako powiązane. Należy pamiętać, że jeśli pole adres struktury nazw ma same wartości zerowe, `Connect` program zwróci wartość zero. Aby uzyskać rozszerzone informacje o błędzie, wywołaj `GetLastError` funkcję członkowską.

Dla gniazd strumienia (typu SOCK_STREAM) aktywne połączenie jest inicjowane dla hosta obcego. Gdy połączenie gniazda zakończy się pomyślnie, gniazdo jest gotowe do wysyłania/odbierania danych.

Dla gniazda datagramu (typu SOCK_DGRAM) ustawia się domyślne miejsce docelowe, które będzie używane podczas kolejnych `Send` i `Receive` wywołań.

##  <a name="create"></a>CAsyncSocket:: Create

Wywołaj `Create` funkcję członkowską po utworzeniu obiektu gniazda, aby utworzyć gniazdo systemu Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Dobrze znany port do użycia w gnieździe lub 0, jeśli chcesz, aby system Windows Sockets wybierał port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*lEvent*<br/>
Maska bitów, która określa kombinację zdarzeń sieci, w których interesuje aplikacja.

- FD_READ chcą otrzymywać powiadomienia o gotowości do odczytu.

- FD_WRITE chcą otrzymywać powiadomienia o gotowości do zapisu.

- FD_OOB chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT chcesz otrzymywać powiadomienia o ukończonym połączeniu.

- FD_CLOSE chcesz otrzymywać powiadomienia o zamknięciu gniazda.

*lpszSockAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy połączonego gniazda, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu o wartości null dla tego parametru wskazuje `CAsyncSocket` , że wystąpienie powinno nasłuchiwać aktywności klienta na wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEAFNOSUPPORT określona Rodzina adresów nie jest obsługiwana.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEMFILE nie ma więcej dostępnych deskryptorów plików.

- WSAENOBUFS Brak dostępnego miejsca w buforze. Nie można utworzyć gniazda.

- WSAEPROTONOSUPPORT określony port nie jest obsługiwany.

- WSAEPROTOTYPE określony port jest niewłaściwy dla tego gniazda.

- WSAESOCKTNOSUPPORT określony typ gniazda nie jest obsługiwany w tej rodzinie adresów.

### <a name="remarks"></a>Uwagi

`Create`wywołuje [gniazdo](#socket) i jeśli to się powiedzie, wywołuje [powiązanie](#bind) , aby powiązać gniazdo z określonym adresem. Obsługiwane są następujące typy gniazd:

- SOCK_STREAM zapewnia sekwencyjne i niezawodne strumienie strumienia bajtów z pełnymi połączeniami. Używa Transmission Control Protocol (TCP) dla rodziny adresów internetowych.

- SOCK_DGRAM obsługuje datagramy, które są bezpołączeniowe, niezawodne pakiety o stałej (zwykle małych) długości. Używa protokołu UDP (User Datagram) dla rodziny adresów internetowych.

    > [!NOTE]
    >  Funkcja członkowska przyjmuje odwołanie do nowego, pustego `CSocket` obiektu jako jego parametru. `Accept` Należy skonstruować ten obiekt przed wywołaniem `Accept`. Należy pamiętać, że jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie wywołuj `Create` dla tego nowego obiektu gniazda.

> [!IMPORTANT]
> `Create`**nie** jest bezpieczny wątkowo.  Jeśli wywołujesz ją w środowisku wielowątkowym, w którym może być wywoływana jednocześnie przez różne wątki, pamiętaj o ochronie każdego wywołania z muteksem lub inną blokadą synchronizacji.

Aby uzyskać więcej informacji na temat gniazd strumienia i datagramów [, zobacz artykuły dotyczące Windows Sockets: W](../../mfc/windows-sockets-background.md) tle [i Windows Sockets: Porty i adresy](../../mfc/windows-sockets-ports-and-socket-addresses.md) gniazd oraz [interfejs API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>CAsyncSocket::D etach

Wywołaj tę funkcję elementu członkowskiego, aby odłączyć uchwyt gniazda z elementu członkowskiego `CAsyncSocket` danych m_hSocket z obiektu i ustawić *m_hSocket* na wartość null.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>CAsyncSocket:: FromHandle

Zwraca wskaźnik do `CAsyncSocket` obiektu.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CAsyncSocket` obiektu lub wartość null, jeśli nie `CAsyncSocket` ma obiektu dołączonego do *hSocket*.

### <a name="remarks"></a>Uwagi

Gdy dany `CAsyncSocket` obiekt nie jest dołączony do dojścia, funkcja członkowska zwraca wartość null.

##  <a name="getlasterror"></a>CAsyncSocket:: GetLastError

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać stan błędu dla ostatniej operacji, która się nie powiodła.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana wskazuje kod błędu dla ostatniej procedury interfejsu API Windows Sockets wykonywanej przez ten wątek.

### <a name="remarks"></a>Uwagi

Gdy określona funkcja członkowska wskazuje, że wystąpił błąd, `GetLastError` należy wywołać, aby pobrać odpowiedni kod błędu. Listę odpowiednich kodów błędów można znaleźć w opisach funkcji poszczególnych elementów członkowskich.

Aby uzyskać więcej informacji o kodach błędów, zobacz [interfejs API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>CAsyncSocket:: getpeername

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać adres gniazda równorzędnego, z którym jest połączone to gniazdo.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rPeerAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rPeerPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , która otrzymuje nazwę gniazda równorzędnego.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. W przypadku powrotu argument *lpSockAddrLen* zawiera rzeczywisty rozmiar *lpSockAddr* zwrócony w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS blokowanie wywołania Windows Sockets jest w toku.

- WSAENOTCONN gniazdo nie jest połączone.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Aby obsłużyć adresy IPv6, należy użyć [CAsyncSocket:: GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>CAsyncSocket:: GetPeerNameEx

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać adres gniazda równorzędnego, z którym jest połączone to gniazdo (obsługuje adresy IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parametry

*rPeerAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rPeerPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS blokowanie wywołania Windows Sockets jest w toku.

- WSAENOTCONN gniazdo nie jest połączone.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Ta funkcja jest taka sama jak [CAsyncSocket:: getpeername](#getpeername) , z tą różnicą, że obsługuje adresy IPv6 oraz starsze protokoły.

##  <a name="getsockname"></a>CAsyncSocket:: GetSockName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać lokalną nazwę gniazda.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rSocketPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , który odbiera adres gniazda.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- WSAEINVAL gniazdo nie zostało powiązane z adresem z `Bind`.

### <a name="remarks"></a>Uwagi

To wywołanie jest szczególnie przydatne, gdy `Connect` wywołanie zostało wykonane bez `Bind` wykonywania pierwszej operacji. to wywołanie zapewnia tylko metodę określania skojarzenia lokalnego, które zostało ustawione przez system.

Aby obsłużyć adresy IPv6, użyj [CAsyncSocket:: GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>CAsyncSocket:: GetSockNameEx

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać lokalną nazwę gniazda (obsługuje adresy IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rSocketPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- WSAEINVAL gniazdo nie zostało powiązane z adresem z `Bind`.

### <a name="remarks"></a>Uwagi

To wywołanie jest takie samo jak [CAsyncSocket:: GetSockName](#getsockname) , z tą różnicą, że obsługuje adresy IPv6 oraz starsze protokoły.

To wywołanie jest szczególnie przydatne, gdy `Connect` wywołanie zostało wykonane bez `Bind` wykonywania pierwszej operacji. to wywołanie zapewnia tylko metodę określania skojarzenia lokalnego, które zostało ustawione przez system.

##  <a name="getsockopt"></a>CAsyncSocket:: GetSockOpt

Wywołaj tę funkcję elementu członkowskiego, aby pobrać opcję gniazda.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName*<br/>
Opcja gniazda, dla której ma zostać pobrana wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w którym ma zostać zwrócona wartość dla wybranej opcji. Wartość skojarzona z wybraną opcją jest zwracana w buforze *lpOptionValue*. Liczba całkowita wskazywana przez *lpOptionLen* powinna początkowo zawierać rozmiar tego buforu w bajtach; i w przypadku powrotu zostanie ustawiony rozmiar zwracanej wartości. W przypadku SO_LINGER jest to rozmiar `LINGER` struktury; dla wszystkich innych opcji będzie rozmiar bool lub **int**, w zależności od opcji. Zapoznaj się z listą opcji i ich rozmiarów w sekcji uwagi.

*lpOptionLen*<br/>
Wskaźnik do rozmiaru buforu *lpOptionValue* w bajtach.

*nLevel*<br/>
Poziom, na którym jest zdefiniowana opcja; Jedyne obsługiwane poziomy to SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Jeśli opcja nigdy nie została ustawiona z `SetSockOpt` `GetSockOpt` , funkcja zwraca wartość domyślną dla opcji. Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpOptionLen* był nieprawidłowy.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOPROTOOPT opcja jest nieznana lub nieobsługiwana. W szczególności SO_BROADCAST nie jest obsługiwane w gniazdach typu SOCK_STREAM, podczas gdy SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazdach typu SOCK_DGRAM.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`GetSockOpt`Pobiera bieżącą wartość dla opcji gniazda skojarzonej z gniazdem dowolnego typu, w dowolnym stanie i zapisuje wynik w *lpOptionValue*. Opcje mają wpływ na operacje gniazda, takie jak routing pakietów, transfer danych poza pasmem itd.

W programie są obsługiwane `GetSockOpt`następujące opcje. Typ identyfikuje typ danych rozmieszczonych przez *lpOptionValue*. Opcja TCP_NODELAY używa poziomu IPPROTO_TCP; wszystkie inne opcje używają SOL_SOCKET poziomu.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Gniazdo nasłuchuje.|
|SO_BROADCAST|BOOL|Gniazdo jest skonfigurowane do przesyłania komunikatów emisji.|
|SO_DEBUG|BOOL|Debugowanie jest włączone.|
|SO_DONTLINGER|BOOL|W przypadku opcji true opcja SO_LINGER jest wyłączona.|
|SO_DONTROUTE|BOOL|Routing jest wyłączony.|
|SO_ERROR|**int**|Pobierz stan błędu i usuń zaznaczenie.|
|SO_KEEPALIVE|BOOL|Trwa wysyłanie aktywności.|
|SO_LINGER|`struct LINGER`|Zwraca bieżące opcje pokutujące.|
|SO_OOBINLINE|BOOL|Dane poza pasmem są odbierane w normalnym strumieniu danych.|
|SO_RCVBUF|int|Rozmiar buforu dla odbieranych.|
|SO_REUSEADDR|BOOL|Gniazdo może być powiązane z adresem, który jest już używany.|
|SO_SNDBUF|**int**|Rozmiar buforu do wysłania.|
|SO_TYPE|**int**|Typ gniazda (na przykład SOCK_STREAM).|
|TCP_NODELAY|BOOL|Wyłącza algorytm nagle dla łączenia wysyłania.|

Opcje rozpowszechniania oprogramowania Berkeley (BSD) nie są `GetSockOpt` obsługiwane w przypadku programu:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Odbierz znak wodny.|
|SO_RCVTIMEO|**int**|Limit czasu odbierania.|
|SO_SNDLOWAT|**int**|Wyślij znak wodny.|
|SO_SNDTIMEO|**int**|Limit czasu wysyłania.|
|IP_OPTIONS||Pobierz opcje w nagłówku IP.|
|TCP_MAXSEG|**int**|Pobierz maksymalny rozmiar segmentu TCP.|

Wywołanie `GetSockOpt` z nieobsługiwaną opcją spowoduje zwrócenie kodu błędu WSAENOPROTOOPT z `GetLastError`.

##  <a name="ioctl"></a>CAsyncSocket:: IOCtl

Wywołaj tę funkcję elementu członkowskiego, aby kontrolować tryb gniazda.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parametry

*lCommand*<br/>
Polecenie do wykonania w gnieździe.

*lpArgument*<br/>
Wskaźnik do parametru dla *lCommand*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEINVAL *lCommand* nie jest prawidłowym poleceniem lub *lpArgument* nie jest akceptowalnym parametrem dla *lCommand*lub polecenie nie ma zastosowania do typu dostarczonego gniazda.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Tej procedury można użyć w dowolnym gnieździe w dowolnym stanie. Służy do pobierania lub pobierania parametrów operacyjnych skojarzonych z gniazdem, niezależnie od podsystemu protokołu i komunikacji. Obsługiwane są następujące polecenia:

- FIONBIO włączać lub wyłączać tryb nieblokowany w gnieździe. Parametr *lpArgument* wskazuje `DWORD`, że jest różna od zera, jeśli tryb nieblokowany ma być włączony i zero, jeśli ma być wyłączone. Jeśli `AsyncSelect` został wystawiony w gnieździe, każda próba użycia `IOCtl` w celu ustawienia gniazda z powrotem do trybu blokowania zakończy się niepowodzeniem z WSAEINVAL. Aby ustawić gniazdo z powrotem do trybu blokowania i zapobiec wystąpieniu błędu WSAEINVAL, aplikacja musi zostać najpierw wyłączona `AsyncSelect` przez wywołanie `AsyncSelect` z parametrem *Levent* równym 0, a następnie `IOCtl`Wywołaj metodę.

- FIONREAD określić maksymalną liczbę bajtów, które mogą być odczytane przy `Receive` użyciu jednego wywołania z tego gniazda. Parametr *lpArgument* wskazuje, w którym `DWORD` `IOCtl` jest przechowywany wynik. Jeśli to gniazdo jest typu SOCK_STREAM, FIONREAD zwraca łączną ilość danych, które mogą być odczytywane w jednym `Receive`; jest to zwykle takie samo, jak całkowita ilość danych umieszczonych w kolejce w gnieździe. Jeśli to gniazdo jest typu SOCK_DGRAM, FIONREAD zwraca rozmiar pierwszego datagramu w kolejce.

- SIOCATMARK określić, czy wszystkie dane poza pasmem zostały odczytane. Dotyczy to tylko gniazda typu SOCK_STREAM, który został skonfigurowany do odbierania danych poza pasmem (SO_OOBINLINE). Jeśli żadne dane poza pasmem oczekują na odczytanie, operacja zwróci wartość różną od zera. W przeciwnym razie zwraca wartość 0, a `Receive` następny `ReceiveFrom` lub wykonany w gnieździe spowoduje pobranie niektórych lub wszystkich danych poprzedzających "markę". aplikacja powinna użyć operacji SIOCATMARK, aby określić, czy dane pozostaną niezmienione. Jeśli istnieją normalne dane poprzedzające "pilne" (poza pasmem), zostaną one odebrane w podanej kolejności. (Należy zauważyć, `Receive` że `ReceiveFrom` lub nigdy nie będą mieszać poza pasmem i zwykłych danych w tym samym wywołaniu). Parametr *lpArgument* wskazuje, w którym `DWORD` `IOCtl` jest przechowywany wynik.

Ta funkcja jest podzbiorem `ioctl()` używanym w usłudze Berkeley Sockets. W szczególności nie ma polecenia odpowiadającego FIOASYNC, podczas gdy SIOCATMARK jest jedynym obsługiwanym poleceniem na poziomie gniazda.

##  <a name="listen"></a>CAsyncSocket:: Listen

Wywołaj tę funkcję elementu członkowskiego, aby nasłuchiwać żądań połączeń przychodzących.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parametry

*nConnectionBacklog*<br/>
Maksymalna długość, do której można zwiększyć kolejkę oczekujących połączeń. Prawidłowy zakres to od 1 do 5.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEADDRINUSE podjęto próbę nasłuchiwania na używanym adresie.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEINVAL gniazdo nie zostało powiązane z `Bind` lub jest już połączone.

- WSAEISCONN gniazdo jest już połączone.

- WSAEMFILE nie ma więcej dostępnych deskryptorów plików.

- WSAENOBUFS Brak dostępnego miejsca w buforze.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- WSAEOPNOTSUPP gniazdo, do którego istnieje odwołanie, nie jest typu, `Listen` który obsługuje operację.

### <a name="remarks"></a>Uwagi

Aby akceptować połączenia, gniazdo jest tworzone w pierwszej `Create`kolejności przy użyciu, a następnie w przypadku `Listen`, gdy połączenia są akceptowane przy użyciu `Accept`. `Listen`dotyczy tylko gniazd, które obsługują połączenia, czyli te, które są typu SOCK_STREAM. To gniazdo jest umieszczane w trybie pasywnym, w którym połączenia przychodzące są potwierdzane i umieszczane w kolejce oczekujące na akceptację przez proces.

Ta funkcja jest zwykle używana przez serwery (lub dowolną aplikację, która chce akceptować połączenia), która może mieć jednocześnie więcej niż jedno żądanie połączenia: Jeśli żądanie połączenia dociera do kolejki, klient otrzyma błąd z oznaczeniem WSAECONNREFUSED.

`Listen`próbuje nadal działać racjonalnie, gdy nie ma dostępnych portów (deskryptorów). Spowoduje to zaakceptowanie połączeń do momentu opróżnienia kolejki. Jeśli porty staną się dostępne, późniejsze wywołanie `Listen` lub `Accept` przepełnienie kolejki do bieżącej lub najnowszej zaległości, o ile jest to możliwe, i wznowienie nasłuchiwania połączeń przychodzących.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Zawiera uchwyt gniazda dla gniazda hermetyzowanego przez ten `CAsyncSocket` obiekt.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>CAsyncSocket:: OnAccept

Wywoływane przez platformę w celu powiadomienia gniazda nasłuchiwania, które może akceptować oczekujące żądania połączenia przez wywołanie funkcji [Zaakceptuj](#accept) element członkowski.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów dotyczą `OnAccept` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

##  <a name="onclose"></a>CAsyncSocket:: OnClose

Wywoływane przez platformę w celu powiadomienia tego gniazda o zamknięciu połączonego gniazda przez ten proces.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów mają zastosowanie do `OnClose` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAECONNRESET połączenie zostało zresetowane przez stronę zdalną.

- WSAECONNABORTED połączenie zostało przerwane z powodu przekroczenia limitu czasu lub innego błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

##  <a name="onconnect"></a>CAsyncSocket:: OnConnect

Wywoływane przez platformę, by powiadomić to gniazdo łączące, że jego próba połączenia została zakończona, czy błąd wystąpił pomyślnie, czy z powodu błędu.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów mają zastosowanie do `OnConnect` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAEADDRINUSE określony adres jest już używany.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny na komputerze lokalnym.

- Adresów WSAEAFNOSUPPORT w określonej rodzinie nie można używać w tym gnieździe.

- WSAECONNREFUSED próba nawiązania połączenia została wymuszona.

- WSAEDESTADDRREQ jest wymagany adres docelowy.

- WSAEFAULT argument *lpSockAddrLen* jest niepoprawny.

- WSAEINVAL gniazdo jest już powiązane z adresem.

- WSAEISCONN gniazdo jest już połączone.

- WSAEMFILE nie ma więcej dostępnych deskryptorów plików.

- WSAENETUNREACH w tej chwili nie można nawiązać połączenia z siecią.

- WSAENOBUFS Brak dostępnego miejsca w buforze. Nie można nawiązać połączenia z gniazdem.

- WSAENOTCONN gniazdo nie jest połączone.

- WSAENOTSOCK deskryptora to plik, a nie gniazdo.

- WSAETIMEDOUT próba nawiązania połączenia bez nawiązywania połączenia.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  W [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` Funkcja powiadomień nigdy nie jest wywoływana. W przypadku połączeń można po prostu `Connect`wywołać, co spowoduje zwrócenie po zakończeniu połączenia (pomyślnie lub w błąd). Sposób obsługi powiadomień o połączeniach to szczegóły implementacji MFC.

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>CAsyncSocket:: OnOutOfBandData

Wywoływane przez platformę, by powiadomić gniazdo odbiorcze, że wysłano dane poza pasmem.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów mają zastosowanie do `OnOutOfBandData` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

### <a name="remarks"></a>Uwagi

Dane poza pasmem są logicznie niezależnym kanałem skojarzonym z każdą parą podłączonych gniazd typu SOCK_STREAM. Kanał jest zazwyczaj używany do wysyłania pilnych danych.

MFC obsługuje dane poza pasmem, ale nie jest odradzane korzystanie `CAsyncSocket` z nich przez użytkowników klasy. Łatwiejszym sposobem, aby utworzyć drugie gniazdo do przekazywania takich danych. Aby uzyskać więcej informacji na temat danych poza pasmem, zobacz [Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

##  <a name="onreceive"></a>CAsyncSocket:: OnReceive

Wywoływane przez platformę w celu powiadomienia tego gniazda o danych w buforze, który można pobrać, wywołując `Receive` funkcję członkowską.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów mają zastosowanie do `OnReceive` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>CAsyncSocket:: OnSend

Wywoływane przez platformę, by powiadomić gniazdo, że może teraz wysyłać dane, wywołując `Send` funkcję członkowską.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd w gnieździe. Następujące kody błędów mają zastosowanie do `OnSend` funkcji składowej:

- **0** funkcja została wykonana pomyślnie.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, [zobacz Windows Sockets: Powiadomienia](../../mfc/windows-sockets-socket-notifications.md)gniazda.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>CAsyncSocket:: operator =

Przypisuje nową wartość do `CAsyncSocket` obiektu.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odwołanie do istniejącego `CAsyncSocket` obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby skopiować `CAsyncSocket` istniejący obiekt do `CAsyncSocket` innego obiektu.

##  <a name="operator_socket"></a>CAsyncSocket:: operator — gniazdo

Użyj tego operatora, aby pobrać uchwyt `CAsyncSocket` gniazda obiektu.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt obiektu SOCKET; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Możesz użyć uchwytu, aby bezpośrednio wywołać interfejsy API systemu Windows.

##  <a name="receive"></a>CAsyncSocket:: Receive

Wywołaj tę funkcję elementu członkowskiego, aby odbierać dane z gniazda.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzaj dane poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `Receive` zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAENOTCONN gniazdo nie jest połączone.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `Receive` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 0 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe, a `Receive` operacja zostałaby zablokowana.

- WSAEMSGSIZE datagram był zbyt duży, aby zmieścił się w określonym buforze i został obcięty.

- WSAEINVAL gniazdo nie zostało powiązane z `Bind`.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana dla podłączonych strumieni lub gniazd datasockets i służy do odczytywania danych przychodzących.

W przypadku gniazd typu SOCK_STREAM zwracana jest ilość informacji, która jest obecnie dostępna do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbierania w wierszu danych poza pasmem (opcja gniazda SO_OOBINLINE) i dane poza pasmem są odczytane, zostaną zwrócone tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` opcji lub [OnOutOfBandData](#onoutofbanddata) , aby określić, czy jeszcze więcej danych poza pasmem ma być odczytywane.

W przypadku gniazd datagramów dane są wyodrębniane z pierwszego zapakowanego datagramu do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż podany bufor, bufor jest wypełniany pierwszą częścią datagramu, nadmiarowe dane są tracone i `Receive` zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE. Jeśli w gnieździe nie są dostępne żadne dane przychodzące, wartość SOCKET_ERROR jest zwracana z kodem błędu ustawionym na WSAEWOULDBLOCK. Funkcja wywołania zwrotnego [OnReceive](#onreceive) może służyć do określania, kiedy docierają więcej danych.

Jeśli gniazdo jest typu SOCK_STREAM, a zdalna Strona zamknie połączenie bezpiecznie, `Receive` zostanie wykonane natychmiast po 0 bajtach. Jeśli połączenie zostało zresetowane, `Receive` zakończy się niepowodzeniem z powodu błędu WSAECONNRESET.

`Receive`powinna być wywoływana tylko raz dla każdego [CAsyncSocket:: OnReceive](#onreceive) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CAsyncSocket:: OnReceive](#onreceive).

##  <a name="receivefrom"></a>CAsyncSocket:: ReceiveFrom

Wywołaj tę funkcję elementu członkowskiego, aby odbierać datagram i przechowywać adres źródłowy w strukturze [SOCKADDR](/windows/win32/winsock/sockaddr-2) lub w *rSocketAddress*.

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);

int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rSocketPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , która przechowuje adres źródłowy po powrocie.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu źródłowego w *lpSockAddr* w bajtach.

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzaj dane poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `ReceiveFrom` zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a konkretny kod błędu może zostać pobrany przez wywołanie `GetLastError`. Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* był nieprawidłowy: bufor *lpSockAddr* był zbyt mały, aby pomieścić adres elementu równorzędnego.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEINVAL gniazdo nie zostało powiązane z `Bind`.

- WSAENOTCONN gniazdo nie jest połączone (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `ReceiveFrom` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 0 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe, a `ReceiveFrom` operacja zostałaby zablokowana.

- WSAEMSGSIZE datagram był zbyt duży, aby zmieścił się w określonym buforze i został obcięty.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do odczytywania danych przychodzących na (prawdopodobnie podłączonym) gnieździe i przechwytywania adresu, z którego dane zostały wysłane.

Aby obsłużyć adresy IPv6, należy użyć [CAsyncSocket:: ReceiveFromEx](#receivefromex).

W przypadku gniazd typu SOCK_STREAM zwracana jest ilość informacji, która jest obecnie dostępna do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbierania w wierszu danych poza pasmem (opcja gniazda SO_OOBINLINE) i dane poza pasmem są odczytane, zostaną zwrócone tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` opcji lub `OnOutOfBandData` , aby określić, czy więcej danych poza pasmem ma być odczytywane. Parametry *lpSockAddr* i *lpSockAddrLen* są ignorowane w przypadku SOCK_STREAM Sockets.

W przypadku gniazd datagramów dane są wyodrębniane z pierwszego zapakowanego datagramu do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż podany bufor, bufor jest wypełniany pierwszą częścią komunikatu, nadmiarowe dane są tracone i `ReceiveFrom` zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE.

Jeśli *lpSockAddr* jest różna od zera, a gniazdo jest typu SOCK_DGRAM, adres sieciowy gniazda, które przesłało dane, jest kopiowany do odpowiedniej struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) . Wartość wskazywana przez *lpSockAddrLen* jest inicjowana do rozmiaru tej struktury i jest modyfikowana przy powrocie, aby wskazać rzeczywisty rozmiar przechowywanych tam adresów. Jeśli w gnieździe nie są dostępne żadne dane przychodzące, `ReceiveFrom` wywołanie czeka na dostarczenie danych, chyba że gniazdo nie jest blokowane. W takim przypadku wartość SOCKET_ERROR jest zwracana z kodem błędu ustawionym na WSAEWOULDBLOCK. `OnReceive` Wywołanie zwrotne może służyć do określania, kiedy docierają więcej danych.

Jeśli gniazdo jest typu SOCK_STREAM, a zdalna Strona zamknie połączenie bezpiecznie, `ReceiveFrom` zostanie wykonane natychmiast po 0 bajtach.

##  <a name="receivefromex"></a>CAsyncSocket:: ReceiveFromEx

Wywołaj tę funkcję elementu członkowskiego, aby odbierać datagram i przechowywać adres źródłowy w strukturze [SOCKADDR](/windows/win32/winsock/sockaddr-2) lub w *rSocketAddress* (obsługuje adresy IPv6).

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP o liczbie kropek.

*rSocketPort*<br/>
Odwołanie do typu UINT, który przechowuje port.

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzaj dane poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `ReceiveFromEx` zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a konkretny kod błędu może zostać pobrany przez wywołanie `GetLastError`. Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT argument *lpSockAddrLen* był nieprawidłowy: bufor *lpSockAddr* był zbyt mały, aby pomieścić adres elementu równorzędnego.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEINVAL gniazdo nie zostało powiązane z `Bind`.

- WSAENOTCONN gniazdo nie jest połączone (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `ReceiveFromEx` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 0 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe, a `ReceiveFromEx` operacja zostałaby zablokowana.

- WSAEMSGSIZE datagram był zbyt duży, aby zmieścił się w określonym buforze i został obcięty.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do odczytywania danych przychodzących na (prawdopodobnie podłączonym) gnieździe i przechwytywania adresu, z którego dane zostały wysłane.

Ta funkcja jest taka sama jak [CAsyncSocket:: ReceiveFrom](#receivefrom) , z tą różnicą, że obsługuje adresy IPv6 oraz starsze protokoły.

W przypadku gniazd typu SOCK_STREAM zwracana jest ilość informacji, która jest obecnie dostępna do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbierania w wierszu danych poza pasmem (opcja gniazda SO_OOBINLINE) i dane poza pasmem są odczytane, zostaną zwrócone tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` opcji lub `OnOutOfBandData` , aby określić, czy więcej danych poza pasmem ma być odczytywane. Parametry *lpSockAddr* i *lpSockAddrLen* są ignorowane w przypadku SOCK_STREAM Sockets.

W przypadku gniazd datagramów dane są wyodrębniane z pierwszego zapakowanego datagramu do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż podany bufor, bufor jest wypełniany pierwszą częścią komunikatu, nadmiarowe dane są tracone i `ReceiveFromEx` zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE.

Jeśli *lpSockAddr* jest różna od zera, a gniazdo jest typu SOCK_DGRAM, adres sieciowy gniazda, które przesłało dane, jest kopiowany do odpowiedniej struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) . Wartość wskazywana przez *lpSockAddrLen* jest inicjowana do rozmiaru tej struktury i jest modyfikowana przy powrocie, aby wskazać rzeczywisty rozmiar przechowywanych tam adresów. Jeśli w gnieździe nie są dostępne żadne dane przychodzące, `ReceiveFromEx` wywołanie czeka na dostarczenie danych, chyba że gniazdo nie jest blokowane. W takim przypadku wartość SOCKET_ERROR jest zwracana z kodem błędu ustawionym na WSAEWOULDBLOCK. `OnReceive` Wywołanie zwrotne może służyć do określania, kiedy docierają więcej danych.

Jeśli gniazdo jest typu SOCK_STREAM, a zdalna Strona zamknie połączenie bezpiecznie, `ReceiveFromEx` zostanie wykonane natychmiast po 0 bajtach.

##  <a name="send"></a>CAsyncSocket:: Send

Wywołaj tę funkcję elementu członkowskiego, aby wysłać dane w podłączonym gnieździe.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor zawierający dane, które mają zostać przesłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingu. Dostawca Windows Sockets może wybrać ignorowanie tej flagi.

- MSG_OOB Wysyłaj dane poza pasmem (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `Send` zwraca łączną liczbę wysłanych znaków. (Należy pamiętać, że może to być mniejsze niż liczba wskazywana przez *nBufLen*). W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEFAULT argument *lpBuf* nie znajduje się w prawidłowej części przestrzeni adresowej użytkownika.

- WSAENETRESET połączenie musi zostać zresetowane, ponieważ jego implementacja została porzucona przez implementację Windows Sockets.

- WSAENOBUFS implementacja Windows Sockets zgłasza zakleszczenie bufora.

- WSAENOTCONN gniazdo nie jest połączone.

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `Send` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 1 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe i żądana operacja zostałaby zablokowana.

- WSAEMSGSIZE gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalny obsługiwany przez implementację Windows Sockets.

- WSAEINVAL gniazdo nie zostało powiązane z `Bind`.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

`Send`służy do zapisywania danych wychodzących w podłączonym strumieniu lub gniazdach datagramów. W przypadku gniazd datagramów należy zachować ostrożność, aby nie przekroczyć maksymalnego rozmiaru pakietu IP bazowych podsieci, która jest `iMaxUdpDg` określona przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) zwróconej przez `AfxSocketInit`. Jeśli dane są zbyt długie, aby można je było przekazać niepodzielnie za pośrednictwem bazowego protokołu, `GetLastError`błąd WSAEMSGSIZE jest zwracany za pośrednictwem i nie są przesyłane żadne dane.

Należy pamiętać, że w przypadku gniazda datagramu pomyślne `Send` ukończenie programu nie wskazuje, że dane zostały dostarczone pomyślnie.

W `CAsyncSocket` przypadku obiektów typu SOCK_STREAM liczba zapisanych bajtów może należeć do przedziału od 1 do długości, w zależności od dostępności bufora na hostach lokalnych i obcych.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CAsyncSocket:: OnSend](#onsend).

##  <a name="sendto"></a>CAsyncSocket:: SendTo

Wywołaj tę funkcję elementu członkowskiego, aby wysłać dane do określonego miejsca docelowego.

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);

int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor zawierający dane, które mają zostać przesłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nHostPort*<br/>
Port identyfikujący aplikację gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, z którym jest połączony ten obiekt: Nazwa komputera, taka jak "ftp.microsoft.com", lub cyfra kropkowana, taka jak "128.56.22.8".

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingu. Dostawca Windows Sockets może wybrać ignorowanie tej flagi.

- MSG_OOB Wysyłaj dane poza pasmem (tylko SOCK_STREAM).

*lpSockAddr*<br/>
Wskaźnik do struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) , która zawiera adres gniazda docelowego.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `SendTo` zwraca łączną liczbę wysłanych znaków. (Należy pamiętać, że może to być mniejsze niż liczba wskazywana przez *nBufLen*). W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEFAULT parametry *lpBuf* lub *lpSockAddr* nie są częścią przestrzeni adresowej użytkownika lub argument *lpSockAddr* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL nazwa hosta jest nieprawidłowa.

- WSAENETRESET połączenie musi zostać zresetowane, ponieważ jego implementacja została porzucona przez implementację Windows Sockets.

- WSAENOBUFS implementacja Windows Sockets zgłasza zakleszczenie bufora.

- WSAENOTCONN gniazdo nie jest połączone (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `SendTo` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 1 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe i żądana operacja zostałaby zablokowana.

- WSAEMSGSIZE gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalny obsługiwany przez implementację Windows Sockets.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny na komputerze lokalnym.

- Adresów WSAEAFNOSUPPORT w określonej rodzinie nie można używać w tym gnieździe.

- WSAEDESTADDRREQ jest wymagany adres docelowy.

- WSAENETUNREACH w tej chwili nie można nawiązać połączenia z siecią.

### <a name="remarks"></a>Uwagi

`SendTo`jest używany w gnieździe lub gniazdach strumienia i jest używany do zapisywania wychodzących danych z gniazda. W przypadku gniazd datagramów należy zachować ostrożność, aby nie przekroczyć maksymalnego rozmiaru pakietów IP bazowych podsieci, które są `iMaxUdpDg` podane przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) wypełnionej przez [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby przekazać niepodzielność przez podstawowy protokół, zwracany jest błąd WSAEMSGSIZE i nie są przesyłane żadne dane.

Należy zauważyć, że pomyślne zakończenie a `SendTo` nie wskazuje, że dane zostały dostarczone pomyślnie.

`SendTo`jest używany tylko w gnieździe SOCK_DGRAM do wysyłania datagramu do określonego gniazda identyfikowanego przez parametr *lpSockAddr* .

Aby wysłać emisję (tylko na SOCK_DGRAM), adres w parametrze *lpSockAddr* powinien być zbudowany przy użyciu specjalnego adresu IP INADDR_BROADCAST (zdefiniowanego w pliku nagłówkowym Windows Sockets Winsock). H) wraz z zamierzonym numerem portu. Lub, jeśli parametr *lpszHostAddress* ma wartość null, gniazdo jest skonfigurowane do emisji. Zwykle nie jest to zalecane, aby datagram rozgłaszał przekroczenie rozmiaru, w którym może wystąpić fragmentacja, co oznacza, że część danych datagramu (z wyjątkiem nagłówków) nie powinna przekraczać 512 bajtów.

Aby obsłużyć adresy IPv6, należy użyć [CAsyncSocket:: SendToEx](#sendtoex).

##  <a name="sendtoex"></a>CAsyncSocket:: SendToEx

Wywołaj tę funkcję elementu członkowskiego, aby wysłać dane do określonego miejsca docelowego (obsługuje adresy IPv6).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor zawierający dane, które mają zostać przesłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nHostPort*<br/>
Port identyfikujący aplikację gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, z którym jest połączony ten obiekt: Nazwa komputera, taka jak "ftp.microsoft.com", lub cyfra kropkowana, taka jak "128.56.22.8".

*nFlags*<br/>
Określa sposób, w jaki nawiązywane jest wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags* . Druga jest zbudowana przez połączenie następujących wartości z C++ operatorem **or** :

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingu. Dostawca Windows Sockets może wybrać ignorowanie tej flagi.

- MSG_OOB Wysyłaj dane poza pasmem (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Jeśli błąd nie wystąpi, `SendToEx` zwraca łączną liczbę wysłanych znaków. (Należy pamiętać, że może to być mniejsze niż liczba wskazywana przez *nBufLen*). W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEFAULT parametry *lpBuf* lub *lpSockAddr* nie są częścią przestrzeni adresowej użytkownika lub argument *lpSockAddr* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL nazwa hosta jest nieprawidłowa.

- WSAENETRESET połączenie musi zostać zresetowane, ponieważ jego implementacja została porzucona przez implementację Windows Sockets.

- WSAENOBUFS implementacja Windows Sockets zgłasza zakleszczenie bufora.

- WSAENOTCONN gniazdo nie jest połączone (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazdem.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazdo zostało zamknięte; nie można wywołać `SendToEx` w gnieździe po `ShutDown` wywołaniu z *Nhow* ustawionym na 1 lub 2.

- WSAEWOULDBLOCK gniazdo jest oznaczone jako nieblokowe i żądana operacja zostałaby zablokowana.

- WSAEMSGSIZE gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalny obsługiwany przez implementację Windows Sockets.

- WSAECONNABORTED obwód wirtualny został przerwany z powodu przekroczenia limitu czasu lub innego błędu.

- WSAECONNRESET obwód wirtualny został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny na komputerze lokalnym.

- Adresów WSAEAFNOSUPPORT w określonej rodzinie nie można używać w tym gnieździe.

- WSAEDESTADDRREQ jest wymagany adres docelowy.

- WSAENETUNREACH w tej chwili nie można nawiązać połączenia z siecią.

### <a name="remarks"></a>Uwagi

Ta metoda jest taka sama jak [CAsyncSocket:: SendTo](#sendto) , z tą różnicą, że obsługuje adresy IPv6 oraz starsze protokoły.

`SendToEx`jest używany w gnieździe lub gniazdach strumienia i jest używany do zapisywania wychodzących danych z gniazda. W przypadku gniazd datagramów należy zachować ostrożność, aby nie przekroczyć maksymalnego rozmiaru pakietów IP bazowych podsieci, które są `iMaxUdpDg` podane przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) wypełnionej przez [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby przekazać niepodzielność przez podstawowy protokół, zwracany jest błąd WSAEMSGSIZE i nie są przesyłane żadne dane.

Należy zauważyć, że pomyślne zakończenie a `SendToEx` nie wskazuje, że dane zostały dostarczone pomyślnie.

`SendToEx`jest używany tylko w gnieździe SOCK_DGRAM do wysyłania datagramu do określonego gniazda identyfikowanego przez parametr *lpSockAddr* .

Aby wysłać emisję (tylko na SOCK_DGRAM), adres w parametrze *lpSockAddr* powinien być zbudowany przy użyciu specjalnego adresu IP INADDR_BROADCAST (zdefiniowanego w pliku nagłówkowym Windows Sockets Winsock). H) wraz z zamierzonym numerem portu. Lub, jeśli parametr *lpszHostAddress* ma wartość null, gniazdo jest skonfigurowane do emisji. Zwykle nie jest to zalecane, aby datagram rozgłaszał przekroczenie rozmiaru, w którym może wystąpić fragmentacja, co oznacza, że część danych datagramu (z wyjątkiem nagłówków) nie powinna przekraczać 512 bajtów.

##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt

Wywołaj tę funkcję elementu członkowskiego, aby ustawić opcję gniazda.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName*<br/>
Opcja gniazda, dla której ma zostać ustawiona wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w którym podano wartość dla wybranej opcji.

*nOptionLen*<br/>
Rozmiar buforu *lpOptionValue* w bajtach.

*nLevel*<br/>
Poziom, na którym jest zdefiniowana opcja; Jedyne obsługiwane poziomy to SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEFAULT *lpOptionValue* nie znajduje się w prawidłowej części przestrzeni adresowej procesu.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAEINVAL *nLevel* jest nieprawidłowa lub informacje w *lpOptionValue* są nieprawidłowe.

- Przekroczono limit czasu połączenia WSAENETRESET po ustawieniu SO_KEEPALIVE.

- WSAENOPROTOOPT opcja jest nieznana lub nieobsługiwana. W szczególności SO_BROADCAST nie jest obsługiwane w gniazdach typu SOCK_STREAM, podczas gdy SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazdach typu SOCK_DGRAM.

- Połączenie WSAENOTCONN zostało zresetowane, gdy ustawiono SO_KEEPALIVE.

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`SetSockOpt`ustawia bieżącą wartość dla opcji gniazda skojarzonej z gniazdem dowolnego typu w dowolnym stanie. Chociaż opcje mogą istnieć na wielu poziomach protokołu, Ta specyfikacja definiuje tylko opcje, które istnieją na najwyższym poziomie "gniazda". Opcje mają wpływ na operacje gniazda, takie jak to, czy przyspieszone dane są odbierane w normalnym strumieniu danych, czy komunikaty emisji można wysyłać w gnieździe itd.

Dostępne są dwa typy opcji gniazda: Opcje logiczne, które włączają lub wyłączają funkcję lub zachowanie oraz opcje, które wymagają wartości całkowitej lub struktury. Aby włączyć opcję Boolean, *lpOptionValue* wskazuje niezerową liczbę całkowitą. Aby wyłączyć opcję *lpOptionValue* wskazuje liczbę całkowitą równą zero. *nOptionLen* powinna być taka sama `sizeof(BOOL)` jak w przypadku opcji logicznych. W przypadku innych opcji *lpOptionValue* wskazuje liczbę całkowitą lub strukturę, która zawiera pożądaną wartość dla opcji, a *nOptionLen* jest długością liczby całkowitej lub struktury.

SO_LINGER steruje akcją wykonywaną, gdy niewysłane dane są umieszczane w `Close` gnieździe, a funkcja jest wywoływana, aby zamknąć gniazdo.

Domyślnie gniazdo nie może być powiązane (patrz [bind](#bind)) z adresem lokalnym, który jest już używany. Zdarza się jednak, że w ten sposób może być wskazane "ponowne użycie" adresu. Ponieważ każde połączenie jest jednoznacznie identyfikowane przez kombinację adresów lokalnych i zdalnych, nie występuje problem z dwoma gniazdami związanymi z tym samym adresem lokalnym, o ile adresy zdalne są różne.

Aby poinformować implementację Windows Sockets, `Bind` że wywołanie w gnieździe nie powinno być niedozwolone, ponieważ żądany adres jest już używany przez inne gniazdo, aplikacja powinna ustawić opcję gniazda SO_REUSEADDR dla gniazda przed wystawieniem `Bind` wywołanie. Należy zauważyć, że opcja jest interpretowana tylko w czasie `Bind` wywołania: jest to niepotrzebne (ale nieszkodliwe), aby ustawić opcję w gnieździe, które nie ma być powiązane z istniejącym adresem, i ustawić lub zresetować opcję `Bind` po wywołaniu nie ma wpływu na to ani żadne inne gniazdo.

Aplikacja może zażądać, aby implementacja Windows Sockets umożliwiała korzystanie z pakietów "Keep-Alive" w połączeniach Transmission Control Protocol (TCP) przez włączenie opcji gniazda SO_KEEPALIVE. Implementacja Windows Sockets nie musi obsługiwać używania Keep-Alives: Jeśli tak, dokładna semantyka jest specyficzna dla implementacji, ale powinna być zgodna z sekcją 4.2.3.6 specyfikacji RFC 1122: "Wymagania dotyczące hostów internetowych — warstwy komunikacji". Jeśli połączenie zostanie porzucone jako wynik "Keep-Alives", kod błędu WSAENETRESET jest zwracany do wszelkich wywołań w toku w gnieździe, a wszystkie kolejne wywołania zakończą się niepowodzeniem z WSAENOTCONN.

Opcja TCP_NODELAY wyłącza algorytm nagle. Algorytm nagle służy do zmniejszania liczby małych pakietów wysyłanych przez hosta przez buforowanie niepotwierdzonych danych wysyłanych do momentu wysłania pakietu o pełnym rozmiarze. Jednak w przypadku niektórych aplikacji ten algorytm może obsłużyć wydajność, a TCP_NODELAY można go wyłączyć. Autorzy aplikacji nie powinni ustawiać TCP_NODELAY, chyba że wpływ takiego działania jest dobrze zrozumiały i żądany, ponieważ ustawienie TCP_NODELAY może mieć znaczny negatywny wpływ na wydajność sieci. TCP_NODELAY jest jedyną obsługiwaną opcją gniazda, która używa poziomu IPPROTO_TCP; wszystkie inne opcje używają SOL_SOCKET poziomu.

Niektóre implementacje programu Windows Sockets dostarczają informacji debugowania danych wyjściowych, jeśli opcja SO_DEBUG jest ustawiona przez aplikację.

W programie są obsługiwane `SetSockOpt`następujące opcje. Typ identyfikuje typ danych rozmieszczonych przez *lpOptionValue*.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Zezwalaj na przekazywanie komunikatów emisji w gnieździe.|
|SO_DEBUG|BOOL|Rejestruj informacje debugowania.|
|SO_DONTLINGER|BOOL|Nie blokuj `Close` oczekiwania na wysłanie niewysłanych danych. Ustawienie tej opcji jest równoznaczne z ustawieniem `l_onoff` SO_LINGER z ustawionym na zero.|
|SO_DONTROUTE|BOOL|Nie trasuj: Wyślij bezpośrednio do interfejsu.|
|SO_KEEPALIVE|BOOL|Wyślij utrzymywanie aktywności.|
|SO_LINGER|`struct LINGER`|Pokutujący na `Close` obecność niewysłanych danych.|
|SO_OOBINLINE|BOOL|Odbieraj dane poza pasmem w normalnym strumieniu danych.|
|SO_RCVBUF|**int**|Określ rozmiar buforu dla odbieranych.|
|SO_REUSEADDR|BOOL|Zezwól na powiązanie gniazda z adresem, który jest już używany. (Zobacz [bind](#bind).)|
|SO_SNDBUF|**int**|Określ rozmiar buforu dla wysyłanych.|
|TCP_NODELAY|BOOL|Wyłącza algorytm nagle dla łączenia wysyłania.|

Opcje rozpowszechniania oprogramowania Berkeley (BSD) nie są `SetSockOpt` obsługiwane w przypadku programu:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Gniazdo nasłuchuje|
|SO_ERROR|**int**|Pobierz stan błędu i usuń zaznaczenie.|
|SO_RCVLOWAT|**int**|Odbierz znak wodny.|
|SO_RCVTIMEO|**int**|Limit czasu odbierania|
|SO_SNDLOWAT|**int**|Wyślij znak wodny.|
|SO_SNDTIMEO|**int**|Limit czasu wysyłania.|
|SO_TYPE|**int**|Typ gniazda.|
|IP_OPTIONS||Ustaw pole opcji w nagłówku adresu IP.|

##  <a name="shutdown"></a>CAsyncSocket:: ShutDown

Wywołaj tę funkcję elementu członkowskiego, aby wyłączyć wysyłanie, odbieranie lub oba w gnieździe.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parametry

*nHow*<br/>
Flaga opisująca, jakie typy operacji nie będą już dozwolone, przy użyciu następujących wartości wyliczanych:

- **odebrane = 0**

- **wysyła = 1**

- **Oba = 2**

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [wartość GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji składowej:

- WSANOTINITIALISED pomyślne [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- WSAENETDOWN implementacja Windows Sockets wykryła, że podsystem sieci nie powiódł się.

- WSAEINVAL *Nhow* jest nieprawidłowy.

- WSAEINPROGRESS blokuje operację blokowania Windows Sockets.

- WSAENOTCONN gniazdo nie jest połączone (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`ShutDown`służy do wyłączania odbierania, transmisji lub obu typów gniazd. Jeśli *Nhow* ma wartość 0, kolejne odbiory w gnieździe będą niedozwolone. Nie ma to wpływu na niższe warstwy protokołu.

W przypadku Transmission Control Protocol (TCP) okno protokołu TCP nie jest zmieniane, a przychodzące dane zostaną zaakceptowane (ale nie potwierdzone), dopóki okno nie zostanie wyczerpane. W przypadku protokołu UDP (User Datagram Protocol) przychodzące datagramy są akceptowane i umieszczane w kolejce. W żadnym przypadku nie zostanie wygenerowany pakiet błędu protokołu ICMP. Jeśli *Nhow* wynosi 1, kolejne operacje wysyłania są niedozwolone. Dla gniazd TCP zostanie wysłane polecenie FIN. Ustawienie *Nhow* na 2 powoduje wyłączenie obu wysyłanych i odbieranych danych zgodnie z powyższym opisem.

Należy pamiętać `ShutDown` , że nie zamyka gniazda, a zasoby dołączone do gniazda nie zostaną zwolnione do momentu `Close` wywołania. Aplikacja nie powinna polegać na możliwości ponownego użycia gniazda po jego wyłączeniu. W szczególności implementacja Windows Sockets nie jest wymagana do obsługi `Connect` tego gniazda.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CAsyncSocket:: OnReceive](#onreceive).

##  <a name="socket"></a>CASyncSocket:: Socket

Przydziela obsługę gniazda.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Parametry

*nSocketType*<br/>
Określa `SOCK_STREAM` lub `SOCK_DGRAM`.

*lEvent*<br/>
Maska bitów, która określa kombinację zdarzeń sieci, w których interesuje aplikacja.

- `FD_READ`: Chcesz otrzymywać powiadomienia o gotowości do odczytu.

- `FD_WRITE`: Chcesz otrzymywać powiadomienia o gotowości do zapisu.

- `FD_OOB`: Chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- `FD_ACCEPT`: Chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- `FD_CONNECT`: Chcesz otrzymywać powiadomienia o ukończonym połączeniu.

- `FD_CLOSE`: Chcesz otrzymywać powiadomienia o zamknięciu gniazda.

*nProtocolType*<br/>
Protokół, który ma być używany z gniazdem specyficznym dla wskazanej rodziny adresów.

*nAddressFormat*<br/>
Specyfikacja rodziny adresów.

### <a name="return-value"></a>Wartość zwracana

Zwraca `TRUE` po powodzeniu, `FALSE` w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda przydziela dojście gniazda. Nie wywołuje [CAsyncSocket:: bind](#bind) , aby powiązać gniazdo z określonym adresem, dlatego należy wywołać `Bind` go później, aby powiązać gniazdo z określonym adresem. Aby ustawić opcję gniazda przed powiązaniem, można użyć [CAsyncSocket:: SetSockOpt](#setsockopt) .

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
