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
ms.openlocfilehash: e384be534bdbb355554c28383e9e214e9084f217
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753032"
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
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Konstruuje `CAsyncSocket` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::Zaakceptuj](#accept)|Akceptuje połączenie na gnieździe.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Żąda powiadomienia o zdarzeniu dla gniazda.|
|[CAsyncSocket::Dołącz](#attach)|Dołącza uchwyt gniazda do `CAsyncSocket` obiektu.|
|[CAsyncSocket::Bind](#bind)|Kojarzy adres lokalny z gniazdem.|
|[CAsyncSocket::Zamknij](#close)|Zamyka gniazdo.|
|[CAsyncSocket::Połącz](#connect)|Ustanawia połączenie z gniazdem równorzędnym.|
|[CAsyncSocket::Tworzenie](#create)|Tworzy gniazdo.|
|[CAsyncSocket::Detach](#detach)|Odłącza uchwyt gniazda `CAsyncSocket` od obiektu.|
|[CAsyncSocket::OdHandle](#fromhandle)|Zwraca wskaźnik do `CAsyncSocket` obiektu, biorąc pod uwagę uchwyt gniazda.|
|[CAsyncSocket::GetLastError](#getlasterror)|Pobiera stan błędu dla ostatniej operacji, która nie powiodła się.|
|[CAsyncSocket::GetPeerName](#getpeername)|Pobiera adres gniazda równorzędnego, do którego jest podłączone gniazdo.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Pobiera adres gniazda równorzędnego, do którego jest podłączone gniazdo (obsługuje adresy IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Pobiera nazwę lokalną dla gniazda.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Pobiera nazwę lokalną gniazda (obsługuje adresy IPv6).|
|[CAsyncSocket::GetSockopt](#getsockopt)|Pobiera opcję gniazda.|
|[CAsyncSocket::IOCtl](#ioctl)|Steruje trybem gniazda.|
|[CAsyncSocket::Słuchaj](#listen)|Ustanawia gniazdo do nasłuchiwać żądań połączeń przychodzących.|
|[CAsyncSocket::Odbieranie](#receive)|Odbiera dane z gniazda.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Odbiera datagram i przechowuje adres źródłowy.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Odbiera datagram i przechowuje adres źródłowy (obsługuje adresy IPv6).|
|[CAsyncSocket::Wyślij](#send)|Wysyła dane do podłączonego gniazda.|
|[CAsyncSocket::Wyślij Do](#sendto)|Wysyła dane do określonego miejsca docelowego.|
|[CAsyncSocket::SendToEx](#sendtoex)|Wysyła dane do określonego miejsca docelowego (obsługuje adresy IPv6).|
|[CAsyncSocket::SetSockopt](#setsockopt)|Ustawia opcję gniazda.|
|[CAsyncSocket::ShutDown](#shutdown)|Wyłącza `Send` i/lub `Receive` wywołuje gniazdo.|
|[CASyncSocket::Gniazdo](#socket)|Przydziela uchwyt gniazda.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::OnAkceptuj](#onaccept)|Powiadamia gniazdo nasłuchiwania, że może akceptować oczekujące żądania połączenia, wywołując `Accept`.|
|[CAsyncSocket::OnClose](#onclose)|Powiadamia gniazdo, że gniazdo podłączone do niego zostało zamknięte.|
|[CAsyncSocket::OnConnect](#onconnect)|Powiadamia gniazdo łączące, że próba połączenia została zakończona, czy pomyślnie lub w wyniku błędu.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Powiadamia gniazdo odbiorcze, że na gnieździe znajdują się dane poza pasmem do odczytu, zwykle pilna wiadomość.|
|[CAsyncSocket::OnReceive](#onreceive)|Powiadamia gniazdo nasłuchiwania, że istnieją dane `Receive`do pobrania przez wywołanie .|
|[CAsyncSocket::OnSend](#onsend)|Powiadamia gniazdo, że może wysyłać `Send`dane, dzwoniąc .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Przypisuje nową wartość do `CAsyncSocket` obiektu.|
|[CAsyncSocket::operator SOCKET](#operator_socket)|Ten operator służy do pobierania uchwytu SOCKET `CAsyncSocket` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Wskazuje uchwyt SOCKET dołączony do `CAsyncSocket` tego obiektu.|

## <a name="remarks"></a>Uwagi

Klasa `CAsyncSocket` hermetyzuje interfejs API funkcji gniazda systemu Windows, zapewniając abstrakcję obiektową dla programistów, którzy chcą używać gniazd systemu Windows w połączeniu z MFC.

Ta klasa opiera się na założeniu, że rozumiesz komunikację sieciową. Użytkownik jest odpowiedzialny za obsługę blokowania, różnic w kolejności bajtów i konwersji między ciągami Unicode i wielobajtowego zestawu znaków (MBCS). Jeśli chcesz wygodniejszy interfejs, który zarządza tymi problemami dla Ciebie, zobacz klasy [CSocket](../../mfc/reference/csocket-class.md).

Aby użyć `CAsyncSocket` obiektu, wywołać jego konstruktora, a następnie [wywołać Create](#create) funkcji, aby utworzyć podstawowy uchwyt gniazda (typ `SOCKET`), z wyjątkiem akceptowanych gniazd. Dla gniazda serwera wywołać Listen funkcji [elementu](#listen) członkowskiego i gniazda klienta [wywołać Connect](#connect) funkcji elementu członkowskiego. Gniazdo serwera należy [wywołać Accept](#accept) funkcji po otrzymaniu żądania połączenia. Pozostałe `CAsyncSocket` funkcje służy do komunikacji między gniazdami. Po zakończeniu, `CAsyncSocket` zniszczyć obiekt, jeśli został utworzony na stercie; destruktor automatycznie wywołuje funkcję [Zamknij.](#close) Typ danych SOCKET jest opisany w artykule [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

> [!NOTE]
> Podczas korzystania z gniazd MFC w wątkach pomocniczych w statycznie połączonej aplikacji MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa gniazd do inicjowania bibliotek gniazd. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku podstawowym.

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z klasy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) i powiązanych artykułów., a także [interfejsu API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Zaakceptuj

Wywołanie tej funkcji elementu członkowskiego, aby zaakceptować połączenie na gnieździe.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parametry

*rConnectedSocket*<br/>
Odwołanie identyfikujące nowe gniazdo, które jest dostępne dla połączenia.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który odbiera adres gniazda łączącego, znany w sieci. Dokładny format argumentu *lpSockAddr* jest określany przez rodzinę adresów ustaloną podczas tworzenia gniazda. Jeśli *lpSockAddr* i/lub *lpSockAddrLen* są równe null, wówczas nie są zwracane żadne informacje o zdalnym adresie akceptowanego gniazda.

*Lpsockaddrlen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. *lpSockAddrLen* jest parametrem value-result: początkowo powinien zawierać ilość miejsca wskazaną przez *lpSockAddr*; po powrocie będzie zawierać rzeczywistą długość (w bajtach) zwracanego adresu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Blokowanie wywołania windows sockets jest w toku.

- WSAEINVAL `Listen` nie został powołany przed przyjęciem.

- WSAEMFILE Kolejka jest pusta po wejściu do zaakceptowania i nie ma dostępnych deskryptorów.

- WSAENOBUFS Brak miejsca w buforze.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- WSAEOPNOTSUPP Gniazdo, do którego istnieje odwołanie, nie jest typem obsługującym usługę zorientowaną na połączenie.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako niezablokujące i nie ma żadnych połączeń do zaakceptowania.

### <a name="remarks"></a>Uwagi

Ta procedura wyodrębnia pierwsze połączenie w kolejce oczekujących połączeń, tworzy nowe gniazdo o tych samych właściwościach co to gniazdo i dołącza je do *rConnectedSocket*. Jeśli w kolejce nie ma `Accept` żadnych oczekujących połączeń, zwraca zero i `GetLastError` zwraca błąd. Akceptowane gniazdo *(rConnectedSocket)* nie może być używane do akceptowania większej liczby połączeń. Oryginalne gniazdo pozostaje otwarte i nasłuchuje.

Argument *lpSockAddr* jest parametrem wyniku, który jest wypełniony adresem gniazda łączącego, znanym warstwie komunikacyjnej. `Accept`jest używany z typami gniazd opartych na połączeniu, takimi jak SOCK_STREAM.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect

Wywołanie tej funkcji elementu członkowskiego, aby zażądać powiadomienia o zdarzeniu dla gniazda.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*Levent*<br/>
Maska bitowa określająca kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ Chcesz otrzymywać powiadomienia o gotowości do czytania.

- FD_WRITE Chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.

- FD_OOB Chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT Chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT Chcesz otrzymywać powiadomienia o wynikach połączenia.

- FD_CLOSE Chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEINVAL Wskazuje, że jeden z określonych parametrów był nieprawidłowy.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana do określenia, które funkcje powiadomień o wywołaniu zwrotnym MFC będą wywoływane dla gniazda. `AsyncSelect`automatycznie ustawia to gniazdo w trybie nieblokujący. Aby uzyskać więcej informacji, zobacz artykuł [Gniazda systemu Windows: Powiadomienia o gniazdach](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Dołącz

Wywołanie tej funkcji elementu członkowskiego, aby `CAsyncSocket` dołączyć uchwyt *hSocket* do obiektu.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*hSocket (własówka)*<br/>
Zawiera uchwyt do gniazda.

*Levent*<br/>
Maska bitowa określająca kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ Chcesz otrzymywać powiadomienia o gotowości do czytania.

- FD_WRITE Chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.

- FD_OOB Chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT Chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT Chcesz otrzymywać powiadomienia o wynikach połączenia.

- FD_CLOSE Chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończy się pomyślnie.

### <a name="remarks"></a>Uwagi

Uchwyt SOCKET jest przechowywany w [m_hSocket](#m_hsocket) element członkowski danych obiektu.

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind

Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć adres lokalny z gniazdem.

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
Adres sieciowy, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu NULL dla tego `CAsyncSocket` parametru wskazuje, że wystąpienie powinno nasłuchiwanie aktywności klienta we wszystkich interfejsach sieciowych.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który zawiera adres do przypisania do tego gniazda.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Poniższa lista zawiera kilka błędów, które mogą być zwracane. Aby uzyskać pełną listę, zobacz [Kody błędów gniazd systemu Windows](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEADDRINUSE Określony adres jest już używany. (Zobacz opcję gniazda SO_REUSEADDR w [obszarze SetSockOpt](#setsockopt).)

- WSAEFAULT Argument *nSockAddrLen* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Blokowanie wywołania windows sockets jest w toku.

- WSAEAFNOSUPPORT Określona rodzina adresów nie jest obsługiwana przez ten port.

- WSAEINVAL Gniazdo jest już powiązane z adresem.

- WSAENOBUFS Za mało buforów dostępnych, zbyt wiele połączeń.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Ta procedura jest używana na niepołączonych datagram `Connect` lub `Listen` gniazdo strumienia, przed kolejnymi lub wywołania. Zanim będzie mógł akceptować żądania połączenia, gniazdo serwera nasłuchiwania musi wybrać `Bind`numer portu i uiścić go w usłudze Windows Sockets, wywołując program . `Bind`ustanawia lokalne skojarzenie (adres hosta/numer portu) gniazda, przypisując nazwę lokalną do gniazda bez nazwy.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket

Konstruuje pusty obiekt gniazda.

```
CAsyncSocket();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu, należy `Create` wywołać jego funkcję elementu członkowskiego, aby utworzyć strukturę danych SOCKET i powiązać jego adres. (Po stronie serwera komunikacji z gniazdami systemu Windows, gdy gniazdo `Accept` nasłuchujące tworzy `Create` gniazdo do użycia w wywołaniu, nie jest wywoływane dla tego gniazda).

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Zamknij

Zamyka gniazdo.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zwalnia deskryptora gniazda, dzięki czemu dalsze odwołania do niego zakończy się niepowodzeniem z błędem WSAENOTSOCK. Jeśli jest to ostatnie odwołanie do gniazda źródłowego, skojarzone informacje o nazewnictwie i dane w kolejce są odrzucane. Destruktor obiektu gniazda wywołuje `Close` dla Ciebie.

Dla `CAsyncSocket`, ale `CSocket`nie dla , semantyka `Close` mają wpływ na opcje gniazda SO_LINGER i SO_DONTLINGER. Aby uzyskać więcej informacji, zobacz funkcję `GetSockOpt`elementu członkowskiego .

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Połącz

Wywołanie tej funkcji elementu członkowskiego, aby ustanowić połączenie z niepodłączonego strumienia lub gniazda datagramu.

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
Adres sieciowy gniazda, do którego jest podłączony ten obiekt: nazwa komputera, taka jak "ftp.microsoft.com" lub numer kropkowany, taki jak "128.56.22.8".

*Port nHost*<br/>
Port identyfikujący aplikację gniazda.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który zawiera adres podłączonego gniazda.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Jeśli wskazuje to kod błędu WSAEWOULDBLOCK, a aplikacja używa zastępowalnych wywołań zwrotnych, aplikacja otrzyma komunikat `OnConnect` po zakończeniu operacji łączenia. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEADDRINUSE Określony adres jest już używany.

- WSAEINPROGRESS Blokowanie wywołania windows sockets jest w toku.

- WSAEADDRNOTAVAIL Określony adres nie jest dostępny na komputerze lokalnym.

- Z tym gniazdem nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie.

- WSAECONNREFUSED Próba połączenia została odrzucona.

- WSAEDESTADDRREQ Wymagany jest adres docelowy.

- WSAEFAULT Argument *nSockAddrLen* jest niepoprawny.

- WSAEINVAL Nieprawidłowy adres hosta.

- WSAEISCONN Gniazdo jest już podłączone.

- WSAEMFILE Nie ma już dostępnych deskryptorów plików.

- WSAENETUNREACH Sieć nie może być osiągnięta z tego hosta w tej chwili.

- WSAENOBUFS Brak miejsca w buforze. Gniazda nie można podłączyć.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- WSAETIMEDOUT Próba połączenia limitu czasu bez ustanawiania połączenia.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i połączenie nie może być natychmiast zakończone.

### <a name="remarks"></a>Uwagi

Jeśli gniazdo jest niezwiązane, unikatowe wartości są przypisywane do lokalnego skojarzenia przez system, a gniazdo jest oznaczone jako powiązane. Należy zauważyć, że jeśli pole adresu struktury `Connect` nazw jest wszystkie zera, zwróci zero. Aby uzyskać informacje o błądach rozszerzonych, należy wywołać `GetLastError` funkcję elementu członkowskiego.

W przypadku gniazd strumienia (typ SOCK_STREAM) aktywne połączenie jest inicjowane z hostem obcym. Po pomyślnym zakończeniu wywołania gniazda gniazdo jest gotowe do wysyłania/odbierania danych.

W przypadku gniazda datagramu (typ SOCK_DGRAM) jest ustawiony domyślny `Send` cel `Receive` podróży, który będzie używany w kolejnych i wywołaniach.

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Tworzenie

Wywołanie `Create` funkcji elementu członkowskiego po skonstruowaniu obiektu gniazda, aby utworzyć gniazdo systemu Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Dobrze znany port, który ma być używany z gniazdem, lub 0, jeśli chcesz, aby gniazda systemu Windows wybrały port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*Levent*<br/>
Maska bitowa określająca kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ Chcesz otrzymywać powiadomienia o gotowości do czytania.

- FD_WRITE Chcesz otrzymywać powiadomienia o gotowości do pisania.

- FD_OOB Chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- FD_ACCEPT Chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- FD_CONNECT Chcesz otrzymywać powiadomienia o zakończonym połączeniu.

- FD_CLOSE Chcesz otrzymywać powiadomienia o zamknięciu gniazda.

*lpszSockAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy podłączonego gniazda, numer kropkowany, taki jak "128.56.22.8". Przekazywanie ciągu NULL dla tego `CAsyncSocket` parametru wskazuje, że wystąpienie powinno nasłuchiwanie aktywności klienta we wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEAFNOSUPPORT Określona rodzina adresów nie jest obsługiwana.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEMFILE Nie ma już dostępnych deskryptorów plików.

- WSAENOBUFS Brak miejsca w buforze. Nie można utworzyć gniazda.

- WSAEPROTONOSUPPORT Określony port nie jest obsługiwany.

- WSAEPROTOTYPE Określony port jest niewłaściwym typem dla tego gniazda.

- WSAESOCKTNOSUPPORT Określony typ gniazda nie jest obsługiwany w tej rodzinie adresów.

### <a name="remarks"></a>Uwagi

`Create`wywołuje [Socket](#socket) i jeśli zakończy się pomyślnie, wywołuje [Bind](#bind) powiązać gniazdo do określonego adresu. Obsługiwane są następujące typy gniazd:

- SOCK_STREAM Zapewnia sekwencjonowane, niezawodne, pełnodupleksowe strumienie bajtów oparte na połączeniu. Używa protokołu TCP (Transmission Control Protocol) dla rodziny adresów internetowych.

- SOCK_DGRAM Obsługuje datagramy, które są bezłącznymi, zawodnymi pakietami o stałej (zazwyczaj małej) maksymalnej długości. Używa protokołu UDP (User Datagram Protocol) dla rodziny adresów internetowych.

    > [!NOTE]
    >  Funkcja `Accept` elementu członkowskiego przyjmuje odwołanie do `CSocket` nowego, pustego obiektu jako parametru. Należy skonstruować ten obiekt `Accept`przed wywołaniem . Należy pamiętać, że jeśli ten obiekt gniazda wykracza poza zakres, połączenie zostanie zamknięte. Nie należy `Create` wywoływać tego nowego obiektu gniazda.

> [!IMPORTANT]
> `Create`**nie** jest bezpieczny dla wątków.  Jeśli wywołujesz go w środowisku wielowątkowym, gdzie może być wywoływana jednocześnie przez różne wątki, należy chronić każde wywołanie za pomocą mutex lub innej blokady synchronizacji.

Aby uzyskać więcej informacji na temat gniazd strumienia i datagramu, zobacz artykuły [Gniazda systemu Windows: Tło](../../mfc/windows-sockets-background.md) i Gniazda systemu [Windows: Porty i adresy gniazd](../../mfc/windows-sockets-ports-and-socket-addresses.md) oraz interfejs API Windows [Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach

Wywołanie tej funkcji elementu członkowskiego, aby odłączyć dojście SOCKET w *m_hSocket* element członkowski danych od `CAsyncSocket` obiektu i ustawić *m_hSocket* na NULL.

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::OdHandle

Zwraca wskaźnik do `CAsyncSocket` obiektu.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket (własówka)*<br/>
Zawiera uchwyt do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CAsyncSocket` obiektu lub NULL, jeśli `CAsyncSocket` do *hSocket*nie jest dołączony żaden obiekt .

### <a name="remarks"></a>Uwagi

Gdy podano dojście `CAsyncSocket` SOCKET, jeśli obiekt nie jest dołączony do dojścia, funkcja elementu członkowskiego zwraca wartość NULL.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać stan błędu dla ostatniej operacji, która nie powiodła się.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje kod błędu dla ostatniej procedury interfejsu API sockets systemu Windows wykonywanej przez ten wątek.

### <a name="remarks"></a>Uwagi

Gdy funkcja określonego elementu członkowskiego wskazuje, `GetLastError` że wystąpił błąd, należy wywołać, aby pobrać odpowiedni kod błędu. Zobacz opisy poszczególnych funkcji członkowskich, aby uzyskać listę odpowiednich kodów błędów.

Aby uzyskać więcej informacji na temat kodów błędów, zobacz [Interfejs API windows sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać adres gniazda równorzędnego, do którego jest podłączone to gniazdo.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parametry

*rPeerAddress (adres)*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*port rPeerPort*<br/>
Odwołanie do UINT, który przechowuje port.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który odbiera nazwę gniazda równorzędnego.

*Lpsockaddrlen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. Po powrocie *argument lpSockAddrLen* zawiera rzeczywisty rozmiar *lpSockAddr* zwrócony w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS Blokowanie wywołania windows sockets jest w toku.

- WSAENOTCONN Gniazdo nie jest podłączone.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Aby obsłużyć adresy IPv6, użyj [CAsyncSocket::GetPeerNameEx](#getpeernameex).

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać adres gniazda równorzędnego, do którego jest podłączone to gniazdo (obsługuje adresy IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parametry

*rPeerAddress (adres)*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*port rPeerPort*<br/>
Odwołanie do UINT, który przechowuje port.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS Blokowanie wywołania windows sockets jest w toku.

- WSAENOTCONN Gniazdo nie jest podłączone.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Ta funkcja jest taka sama jak [CAsyncSocket::GetPeerName](#getpeername) z tą różnicą, że obsługuje adresy IPv6, a także starsze protokoły.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę lokalną dla gniazda.

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
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*Port rSocketPort*<br/>
Odwołanie do UINT, który przechowuje port.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który odbiera adres gniazda.

*Lpsockaddrlen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- WSAEINVAL Gniazdo nie zostało powiązane z `Bind`adresem z .

### <a name="remarks"></a>Uwagi

To wywołanie jest `Connect` szczególnie przydatne, gdy `Bind` połączenie zostało wykonane bez wykonywania pierwszego; to wywołanie zapewnia tylko środki, za pomocą których można określić lokalne skojarzenie, które zostało ustawione przez system.

Aby obsłużyć adresy IPv6, użyj [CAsyncSocket::GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę lokalną dla gniazda (obsługuje adresy IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*Port rSocketPort*<br/>
Odwołanie do UINT, który przechowuje port.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* nie jest wystarczająco duży.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- WSAEINVAL Gniazdo nie zostało powiązane z `Bind`adresem z .

### <a name="remarks"></a>Uwagi

To wywołanie jest taka sama jak [CAsyncSocket::GetSockName](#getsockname) z tą różnicą, że obsługuje adresy IPv6, a także starsze protokoły.

To wywołanie jest `Connect` szczególnie przydatne, gdy `Bind` połączenie zostało wykonane bez wykonywania pierwszego; to wywołanie zapewnia tylko środki, za pomocą których można określić lokalne skojarzenie, które zostało ustawione przez system.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockopt

Wywołanie tej funkcji elementu członkowskiego, aby pobrać opcję gniazda.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName (Nazwa)*<br/>
Opcja gniazda, dla której ma zostać pobrana wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w którym ma zostać zwrócona wartość żądanej opcji. Wartość skojarzona z wybraną opcją jest zwracana w *buforze lpOptionValue*. Liczba całkowita wskazywiana przez *lpOptionLen* powinna pierwotnie zawierać rozmiar tego buforu w bajtach; i po zwrocie zostanie ustawiona na rozmiar zwracanej wartości. Dla SO_LINGER będzie to wielkość `LINGER` struktury; dla wszystkich innych opcji będzie to rozmiar BOOL lub **int**, w zależności od opcji. Zobacz listę opcji i ich rozmiary w sekcji Uwagi.

*lpOptionLen (lpOptionLen)*<br/>
Wskaźnik do rozmiaru *buforu lpOptionValue* w bajtach.

*nPoziom*<br/>
Poziom, na którym zdefiniowano opcję; jedynymi obsługiwanymi poziomami są SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Jeśli opcja nigdy nie `SetSockOpt`została `GetSockOpt` ustawiona z , zwraca wartość domyślną dla opcji. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpOptionLen* był nieprawidłowy.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOPROTOOPT Opcja jest nieznana lub nieobsługiwała. W szczególności SO_BROADCAST nie jest obsługiwany w gniazdach typu SOCK_STREAM, podczas gdy SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazdach typu SOCK_DGRAM.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`GetSockOpt`pobiera bieżącą wartość opcji gniazda skojarzonej z gniazdem dowolnego typu, w dowolnym stanie i przechowuje wynik w *lpOptionValue*. Opcje wpływają na operacje gniazda, takie jak routing pakietów, transfer danych poza pasmem i tak dalej.

Następujące opcje są obsługiwane `GetSockOpt`dla . Typ identyfikuje typ danych adresowanych przez *lpOptionValue*. Opcja TCP_NODELAY używa IPPROTO_TCP poziomu; wszystkie inne opcje używają poziomu SOL_SOCKET.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|Bool|Gniazdo nasłuchuje.|
|SO_BROADCAST|Bool|Gniazdo jest skonfigurowane do transmisji komunikatów emisji.|
|SO_DEBUG|Bool|Debugowanie jest włączone.|
|SO_DONTLINGER|Bool|Jeśli true, opcja SO_LINGER jest wyłączona.|
|SO_DONTROUTE|Bool|Routing jest wyłączony.|
|SO_ERROR|**int**|Pobierz stan błędu i wyczyść.|
|SO_KEEPALIVE|Bool|Keep-alives są wysyłane.|
|So_linger|`struct LINGER`|Zwraca bieżące opcje posuwu.|
|SO_OOBINLINE|Bool|Dane poza pasmem są odbierane w normalnym strumieniu danych.|
|SO_RCVBUF|int|Rozmiar buforu dla odbiera.|
|SO_REUSEADDR|Bool|Gniazdo może być powiązane z adresem, który jest już używany.|
|SO_SNDBUF|**int**|Rozmiar buforu dla wysyła.|
|SO_TYPE|**int**|Typ gniazda (na przykład SOCK_STREAM).|
|Tcp_nodelay|Bool|Wyłącza algorytm Nagle'a do wysyłania scalania.|

Opcje berkeley Software Distribution (BSD) `GetSockOpt` nie są obsługiwane:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Otrzymuj znak niskiej wody.|
|SO_RCVTIMEO|**int**|Limit czasu odbioru.|
|SO_SNDLOWAT|**int**|Wyślij znak niskiej wody.|
|SO_SNDTIMEO|**int**|Wyślij limit czasu.|
|IP_OPTIONS||Pobierz opcje w nagłówku IP.|
|TCP_MAXSEG|**int**|Uzyskaj maksymalny rozmiar segmentu TCP.|

Wywołanie `GetSockOpt` z nieobsługiwanym rozwiązaniem spowoduje, że kod błędu WSAENOPROTOOPT zostanie zwrócony z `GetLastError`.

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

Wywołanie tej funkcji elementu członkowskiego, aby kontrolować tryb gniazda.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parametry

*lKomieńcenie*<br/>
Polecenie do wykonania na gnieździe.

*lpArgument*<br/>
Wskaźnik do parametru *dla lCommand*.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEINVAL *lCommand* nie jest prawidłowym poleceniem lub *lpArgument* nie jest dopuszczalnym parametrem dla *lCommand*lub polecenie nie ma zastosowania do typu dostarczonego gniazda.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

Ta procedura może być używana na dowolnym gnieździe w dowolnym stanie. Służy do pobierania lub pobierania parametrów pracy związanych z gniazdem, niezależnie od podsystemu protokołu i komunikacji. Obsługiwane są następujące polecenia:

- FIONBIO Włącz lub wyłącz tryb nieblokujący na gnieździe. *LpArgument* wskazuje na `DWORD`, który jest niezerowy, jeśli tryb nieblokujący ma być włączony i zero, jeśli ma być wyłączony. Jeśli `AsyncSelect` został wydany na gnieździe, `IOCtl` następnie każda próba użycia, aby ustawić gniazdo z powrotem do trybu blokowania zakończy się niepowodzeniem z WSAEINVAL. Aby przywrócić tryb blokowania gniazda i zapobiec błędowi WSAEINVAL, `AsyncSelect` aplikacja `AsyncSelect` musi najpierw wyłączyć, wywołując z parametrem *lEvent* równym 0, a następnie wywołać `IOCtl`.

- FIONREAD Określ maksymalną liczbę bajtów, `Receive` które mogą być odczytywane za pomocą jednego wywołania z tego gniazda. *LpArgument* wskazuje, `DWORD` w którym `IOCtl` przechowuje wynik. Jeśli to gniazdo jest typu SOCK_STREAM, FIONREAD zwraca całkowitą ilość danych, które `Receive`mogą być odczytane w jednym ; zwykle jest to taka sama jak całkowita ilość danych w kolejce na gnieździe. Jeśli to gniazdo jest typu SOCK_DGRAM, FIONREAD zwraca rozmiar pierwszego datagramu w kolejce na gnieździe.

- SIOCATMARK Określ, czy wszystkie dane poza pasmem zostały odczytane. Dotyczy to tylko gniazda typu SOCK_STREAM które zostało skonfigurowane do odbioru danych poza pasmem (SO_OOBINLINE). Jeśli nie jest oczekiwanie na odczyt danych poza pasmem, operacja zwraca wartość niezerową. W przeciwnym razie zwraca 0, a następny `Receive` lub `ReceiveFrom` wykonany na gnieździe pobierze niektóre lub wszystkie dane poprzedzające "znak"; aplikacja powinna użyć operacji SIOCATMARK, aby ustalić, czy pozostają jakiekolwiek dane. Jeśli istnieją normalne dane poprzedzające "pilne" (poza pasmem) dane, zostaną odebrane w kolejności. (Należy zauważyć, że `Receive` lub `ReceiveFrom` nigdy nie będzie mieszać poza pasmem i normalnych danych w tym samym wywołaniu.) *LpArgument* wskazuje, `DWORD` w którym `IOCtl` przechowuje wynik.

Ta funkcja jest podzbiorem używanym `ioctl()` w gniazdach Berkeley. W szczególności nie ma polecenia, które jest równoważne FIOASYNC, podczas gdy SIOCATMARK jest jedynym poleceniem na poziomie gniazda, które jest obsługiwane.

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Słuchaj

Wywołanie tej funkcji elementu członkowskiego, aby nasłuchiwać żądań połączenia przychodzącego.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parametry

*nConnectionBacklog (dziennik)*<br/>
Maksymalna długość, do której może wzrosnąć kolejka oczekujących połączeń. Prawidłowy zakres wynosi od 1 do 5.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEADDRINUSE Podjęto próbę nasłuchicia na używany adres.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEINVAL Gniazdo nie zostało `Bind` połączone lub jest już podłączone.

- WSAEISCONN Gniazdo jest już podłączone.

- WSAEMFILE Nie ma już dostępnych deskryptorów plików.

- WSAENOBUFS Brak miejsca w buforze.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- WSAEOPNOTSUPP Gniazdo, do którego istnieje odwołanie, `Listen` nie jest typu obsługującego operację.

### <a name="remarks"></a>Uwagi

Aby zaakceptować połączenia, gniazdo jest `Create`najpierw tworzone z , określono `Listen`zaległości dla połączeń przychodzących za `Accept`pomocą , a następnie połączenia są akceptowane za pomocą . `Listen`dotyczy tylko gniazd obsługujących połączenia, czyli tych typu SOCK_STREAM. To gniazdo jest przełączone w tryb "pasywny", w którym połączenia przychodzące są potwierdzane i umieszczane w kolejce do czasu akceptacji przez proces.

Ta funkcja jest zwykle używana przez serwery (lub dowolną aplikację, która chce akceptować połączenia), która może mieć więcej niż jedno żądanie połączenia naraz: jeśli żądanie połączenia zostanie dostarczone z pełną kolejką, klient otrzyma błąd ze wskazaniem WSAECONNREFUSED.

`Listen`próbuje nadal działać racjonalnie, gdy nie ma dostępnych portów (deskryptorów). Będzie akceptować połączenia, dopóki kolejka nie zostanie opróżniona. Jeśli porty staną się `Listen` dostępne, późniejsze wywołanie lub `Accept` uzupełni kolejkę do bieżącego lub najnowszego "zaległości", jeśli to możliwe, i wznowi nasłuchiwanie połączeń przychodzących.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket

Zawiera uchwyt SOCKET dla gniazda hermetyzowany przez ten `CAsyncSocket` obiekt.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAkceptuj

Wywoływane przez strukturę, aby powiadomić gniazdo nasłuchiwania, że może akceptować oczekujące żądania połączenia, wywołując [Accept](#accept) funkcji elementu członkowskiego.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Następujące kody błędów `OnAccept` mają zastosowanie do funkcji elementu członkowskiego:

- **0** Funkcja została pomyślnie wykonana.

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose

Wywoływane przez strukturę, aby powiadomić to gniazdo, że podłączone gniazdo jest zamknięty przez jego proces.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Do funkcji `OnClose` elementu członkowskiego mają zastosowanie następujące kody błędów:

- **0** Funkcja została pomyślnie wykonana.

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAECONNRESET Połączenie zostało zresetowane przez stronę zdalną.

- WSAECONNABORTED Połączenie zostało przerwane z powodu limitu czasu lub innej awarii.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect

Wywoływane przez strukturę, aby powiadomić to gniazdo łączące, że jego próba połączenia została zakończona, czy pomyślnie lub w błędzie.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Do funkcji `OnConnect` elementu członkowskiego mają zastosowanie następujące kody błędów:

- **0** Funkcja została pomyślnie wykonana.

- WSAEADDRINUSE Określony adres jest już używany.

- WSAEADDRNOTAVAIL Określony adres nie jest dostępny na komputerze lokalnym.

- Z tym gniazdem nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie.

- WSAECONNREFUSED Próba połączenia została zdecydowanie odrzucona.

- WSAEDESTADDRREQ Wymagany jest adres docelowy.

- WSAEFAULT Argument *lpSockAddrLen* jest niepoprawny.

- WSAEINVAL Gniazdo jest już powiązane z adresem.

- WSAEISCONN Gniazdo jest już podłączone.

- WSAEMFILE Nie ma już dostępnych deskryptorów plików.

- WSAENETUNREACH Sieć nie może być osiągnięta z tego hosta w tej chwili.

- WSAENOBUFS Brak miejsca w buforze. Gniazda nie można podłączyć.

- WSAENOTCONN Gniazdo nie jest podłączone.

- WSAENOTSOCK Deskryptor jest plikiem, a nie gniazdem.

- WSAETIMEDOUT Próba połączenia limitu czasu bez ustanawiania połączenia.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> W [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` funkcja powiadomień nigdy nie jest wywoływana. W przypadku połączeń wystarczy `Connect`wywołać , który zwróci po zakończeniu połączenia (pomyślnie lub przez pomyłkę). Jak powiadomienia połączenia są obsługiwane jest szczegóły implementacji MFC.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData

Wywoływane przez platformę, aby powiadomić gniazdo odbiorcze, że gniazdo wysyłające ma dane poza pasmem do wysłania.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Do funkcji `OnOutOfBandData` elementu członkowskiego mają zastosowanie następujące kody błędów:

- **0** Funkcja została pomyślnie wykonana.

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

### <a name="remarks"></a>Uwagi

Dane poza pasmem to logicznie niezależny kanał, który jest skojarzony z każdą parą podłączonych gniazd typu SOCK_STREAM. Kanał jest zazwyczaj używany do wysyłania pilnych danych.

MFC obsługuje dane poza pasmem, `CAsyncSocket` ale użytkownicy klasy są odradzane z ich używania. Łatwiejszym sposobem jest utworzenie drugiego gniazda do przekazywania takich danych. Aby uzyskać więcej informacji na temat danych poza pasmem, zobacz [Windows Sockets: Sockets .](../../mfc/windows-sockets-socket-notifications.md)

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive

Wywoływane przez strukturę, aby powiadomić to gniazdo, że istnieją `Receive` dane w buforze, które można pobrać przez wywołanie funkcji elementu członkowskiego.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Do funkcji `OnReceive` elementu członkowskiego mają zastosowanie następujące kody błędów:

- **0** Funkcja została pomyślnie wykonana.

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend

Wywoływane przez strukturę, aby powiadomić gniazdo, `Send` że można teraz wysyłać dane, wywołując funkcję elementu członkowskiego.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*kod nError*<br/>
Ostatni błąd na gnieździe. Do funkcji `OnSend` elementu członkowskiego mają zastosowanie następujące kody błędów:

- **0** Funkcja została pomyślnie wykonana.

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operator =

Przypisuje nową wartość do `CAsyncSocket` obiektu.

```cpp
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parametry

*Rsrc*<br/>
Odwołanie do istniejącego `CAsyncSocket` obiektu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, `CAsyncSocket` aby `CAsyncSocket` skopiować istniejący obiekt do innego obiektu.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::operator SOCKET

Ten operator służy do pobierania uchwytu SOCKET `CAsyncSocket` obiektu.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, uchwyt socket obiektu; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Dojścia można używać do bezpośredniego wywoływania interfejsów API systemu Windows.

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Odbieranie

Wywołanie tej funkcji elementu członkowskiego, aby odbierać dane z gniazda.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_PEEK Wgląd do danych przychodzących. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzanie danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `Receive` żaden błąd, zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [plik GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAENOTCONN Gniazdo nie jest podłączone.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie można wywołać `Receive` gniazda po `ShutDown` wywołaniu z *nHow* ustawiona na 0 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i `Receive` operacja zablokuje.

- WSAEMSGSIZE Datagram był zbyt duży, aby zmieścić się w określonym buforze i został obcięty.

- WSAEINVAL Gniazdo nie zostało `Bind`powiązane z .

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana do podłączonych gniazd strumienia lub datagramu i służy do odczytywania danych przychodzących.

W przypadku gniazd typu SOCK_STREAM zwracana jest jak najwięcej informacji, ile jest obecnie dostępnych do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbioru danych poza pasmem (opcja gniazda SO_OOBINLINE), a dane poza pasmem są nieprzeczytane, zwracane będą tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` opcji lub [OnOutOfBandData,](#onoutofbanddata) aby ustalić, czy więcej danych poza pasmem pozostaje do odczytania.

W przypadku gniazd datagramu dane są wyodrębniane z pierwszego modułu datagramu w kolejce do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż dostarczony bufor, bufor jest wypełniony pierwszą częścią datagramu, `Receive` nadmiar danych zostanie utracony i zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE. Jeśli w gnieździe nie są dostępne żadne dane przychodzące, zwracana jest wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEWOULDBLOCK. [OnReceive](#onreceive) wywołanie zwrotne funkcja może służyć do określenia, kiedy więcej danych nadejdzie.

Jeśli gniazdo jest typu SOCK_STREAM i po stronie zdalnej bezpiecznie zamknąć `Receive` połączenie, a zakończy się natychmiast z 0 bajtów odebranych. Jeśli połączenie zostało zresetowane, błąd WSAECONNRESET zakończy się niepowodzeniem. `Receive`

`Receive`należy wywołać tylko raz za każdym razem [CAsyncSocket::OnReceive](#onreceive) jest wywoływana.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveFrom

Wywołanie tej funkcji elementu członkowskiego, aby otrzymać datagram i przechowywać adres źródłowy w strukturze [SOCKADDR](/windows/win32/winsock/sockaddr-2) lub *w rSocketAddress*.

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

*lpBuf (właśc.*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*Port rSocketPort*<br/>
Odwołanie do UINT, który przechowuje port.

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który przechowuje adres źródłowy po powrocie.

*Lpsockaddrlen*<br/>
Wskaźnik do długości adresu źródłowego w *lpSockAddr* w bajtach.

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_PEEK Wgląd do danych przychodzących. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzanie danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `ReceiveFrom` żaden błąd, zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod `GetLastError`błędu można pobrać, wywołując . Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* był nieprawidłowy: bufor *lpSockAddr* był zbyt mały, aby pomieścić adres równorzędny.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEINVAL Gniazdo nie zostało `Bind`powiązane z .

- WSAENOTCONN Gniazdo nie jest podłączone (tylko SOCK_STREAM).

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie można wywołać `ReceiveFrom` gniazda po `ShutDown` wywołaniu z *nHow* ustawiona na 0 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i `ReceiveFrom` operacja zablokuje.

- WSAEMSGSIZE Datagram był zbyt duży, aby zmieścić się w określonym buforze i został obcięty.

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do odczytywania danych przychodzących na (ewentualnie podłączonym) gnieździe i przechwyceniu adresu, z którego dane zostały wysłane.

Aby obsłużyć adresy IPv6, użyj [CAsyncSocket::ReceiveFromEx](#receivefromex).

W przypadku gniazd typu SOCK_STREAM zwracana jest jak najwięcej informacji, ile jest obecnie dostępnych do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbioru danych poza pasmem (opcja gniazda SO_OOBINLINE), a dane poza pasmem są nieprzeczytane, zwracane będą tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` tej `OnOutOfBandData` opcji lub określić, czy więcej danych poza pasmem pozostaje do odczytania. Parametry *lpSockAddr* i *lpSockAddrLen* są ignorowane dla gniazd SOCK_STREAM.

W przypadku gniazd datagramu dane są wyodrębniane z pierwszego modułu datagramu w kolejce do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż bufor dostarczony, bufor jest wypełniona pierwszą częścią wiadomości, `ReceiveFrom` nadmiar danych zostanie utracony i zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE.

Jeśli *lpSockAddr* jest niezerowy, a gniazdo jest typu SOCK_DGRAM, adres sieciowy gniazda, które wysłał dane, jest kopiowany do odpowiedniej struktury [SOCKADDR.](/windows/win32/winsock/sockaddr-2) Wartość wskazana przez *lpSockAddrLen* jest inicjowana do rozmiaru tej struktury i jest modyfikowana po powrocie, aby wskazać rzeczywisty rozmiar adresu tam przechowywanego. Jeśli w gnieździe nie `ReceiveFrom` są dostępne żadne dane przychodzące, wywołanie czeka na przybycie danych, chyba że gniazdo nie jest blokowanie. W takim przypadku zwracana jest wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEWOULDBLOCK. Wywołanie zwrotne `OnReceive` może służyć do określenia, kiedy więcej danych nadejdzie.

Jeśli gniazdo jest typu SOCK_STREAM i po stronie zdalnej bezpiecznie zamknąć `ReceiveFrom` połączenie, a zakończy się natychmiast z 0 bajtów odebranych.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx

Wywołanie tej funkcji elementu członkowskiego, aby odbierać datagram i przechowywać adres źródłowy w strukturze [SOCKADDR](/windows/win32/winsock/sockaddr-2) lub w *rSocketAddress* (obsługuje adresy IPv6).

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Bufor dla danych przychodzących.

*nBufLen*<br/>
Długość *lpBuf* w bajtach.

*rSocketAddress*<br/>
Odwołanie do `CString` obiektu, który odbiera adres IP z kropkowanym numerem.

*Port rSocketPort*<br/>
Odwołanie do UINT, który przechowuje port.

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_PEEK Wgląd do danych przychodzących. Dane są kopiowane do buforu, ale nie są usuwane z kolejki wejściowej.

- MSG_OOB Przetwarzanie danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `ReceiveFromEx` żaden błąd, zwraca liczbę odebranych bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod `GetLastError`błędu można pobrać, wywołując . Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT Argument *lpSockAddrLen* był nieprawidłowy: bufor *lpSockAddr* był zbyt mały, aby pomieścić adres równorzędny.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEINVAL Gniazdo nie zostało `Bind`powiązane z .

- WSAENOTCONN Gniazdo nie jest podłączone (tylko SOCK_STREAM).

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie można wywołać `ReceiveFromEx` gniazda po `ShutDown` wywołaniu z *nHow* ustawiona na 0 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i `ReceiveFromEx` operacja zablokuje.

- WSAEMSGSIZE Datagram był zbyt duży, aby zmieścić się w określonym buforze i został obcięty.

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do odczytywania danych przychodzących na (ewentualnie podłączonym) gnieździe i przechwyceniu adresu, z którego dane zostały wysłane.

Ta funkcja jest taka sama jak [CAsyncSocket::ReceiveFrom](#receivefrom) z tą różnicą, że obsługuje adresy IPv6, a także starsze protokoły.

W przypadku gniazd typu SOCK_STREAM zwracana jest jak najwięcej informacji, ile jest obecnie dostępnych do rozmiaru dostarczonego buforu. Jeśli gniazdo zostało skonfigurowane do odbioru danych poza pasmem (opcja gniazda SO_OOBINLINE), a dane poza pasmem są nieprzeczytane, zwracane będą tylko dane poza pasmem. Aplikacja może użyć `IOCtlSIOCATMARK` tej `OnOutOfBandData` opcji lub określić, czy więcej danych poza pasmem pozostaje do odczytania. Parametry *lpSockAddr* i *lpSockAddrLen* są ignorowane dla gniazd SOCK_STREAM.

W przypadku gniazd datagramu dane są wyodrębniane z pierwszego modułu datagramu w kolejce do rozmiaru dostarczonego buforu. Jeśli datagram jest większy niż bufor dostarczony, bufor jest wypełniona pierwszą częścią wiadomości, `ReceiveFromEx` nadmiar danych zostanie utracony i zwraca wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEMSGSIZE.

Jeśli *lpSockAddr* jest niezerowy, a gniazdo jest typu SOCK_DGRAM, adres sieciowy gniazda, które wysłał dane, jest kopiowany do odpowiedniej struktury [SOCKADDR.](/windows/win32/winsock/sockaddr-2) Wartość wskazana przez *lpSockAddrLen* jest inicjowana do rozmiaru tej struktury i jest modyfikowana po powrocie, aby wskazać rzeczywisty rozmiar adresu tam przechowywanego. Jeśli w gnieździe nie `ReceiveFromEx` są dostępne żadne dane przychodzące, wywołanie czeka na przybycie danych, chyba że gniazdo nie jest blokowanie. W takim przypadku zwracana jest wartość SOCKET_ERROR z kodem błędu ustawionym na WSAEWOULDBLOCK. Wywołanie zwrotne `OnReceive` może służyć do określenia, kiedy więcej danych nadejdzie.

Jeśli gniazdo jest typu SOCK_STREAM i po stronie zdalnej bezpiecznie zamknąć `ReceiveFromEx` połączenie, a zakończy się natychmiast z 0 bajtów odebranych.

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Wyślij

Wywołanie tej funkcji elementu członkowskiego, aby wysłać dane na podłączonym gnieździe.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Bufor zawierający dane, które mają być przesyłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingowi. Dostawca gniazd systemu Windows może zignorować tę flagę.

- MSG_OOB Wyślij dane poza pasmem (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `Send` żaden błąd, zwraca całkowitą liczbę wysłanych znaków. (Należy zauważyć, że może to być mniejsza niż liczba wskazana przez *nBufLen*.) W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [plik GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEACCES Żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEFAULT Argument *lpBuf* nie znajduje się w prawidłowej części przestrzeni adresowej użytkownika.

- WSAENETRESET Połączenie musi zostać zresetowane, ponieważ implementacja Windows Sockets go upuściła.

- WSAENOBUFS Implementacja Windows Sockets zgłasza zakleszczenie buforu.

- WSAENOTCONN Gniazdo nie jest podłączone.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie jest możliwe `Send` wywołanie gniazda `ShutDown` po wywołaniu z *nHow* ustawiona na 1 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i żądana operacja zablokuje.

- WSAEMSGSIZE Gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.

- WSAEINVAL Gniazdo nie zostało `Bind`powiązane z .

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

`Send`służy do zapisywania danych wychodzących na podłączonych gniazdach strumienia lub datagramu. W przypadku gniazd datagramu należy uważać, aby nie przekraczać maksymalnego rozmiaru pakietów `iMaxUdpDg` IP podsieci, `AfxSocketInit`który jest podawany przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) zwracany przez program . Jeśli dane są zbyt długie, aby przekazać niepodzielnie przez podstawowy protokół, błąd `GetLastError`WSAEMSGSIZE jest zwracany za pośrednictwem , i nie są przesyłane żadne dane.

Należy zauważyć, że dla gniazda datagramu pomyślne zakończenie a `Send` nie oznacza, że dane zostały pomyślnie dostarczone.

W `CAsyncSocket` obiektach typu SOCK_STREAM liczba zapisanych bajtów może wynosić od 1 do żądanej długości, w zależności od dostępności buforu zarówno dla hostów lokalnych, jak i zagranicznych.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnSend](#onsend).

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::Wyślij Do

Wywołanie tej funkcji elementu członkowskiego, aby wysłać dane do określonego miejsca docelowego.

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

*lpBuf (właśc.*<br/>
Bufor zawierający dane, które mają być przesyłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*Port nHost*<br/>
Port identyfikujący aplikację gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, do którego jest podłączony ten obiekt: nazwa komputera, taka jak "ftp.microsoft.com" lub numer kropkowany, taki jak "128.56.22.8".

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingowi. Dostawca gniazd systemu Windows może zignorować tę flagę.

- MSG_OOB Wyślij dane poza pasmem (tylko SOCK_STREAM).

*Lpsockaddr*<br/>
Wskaźnik do struktury [SOCKADDR,](/windows/win32/winsock/sockaddr-2) który zawiera adres gniazda docelowego.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `SendTo` żaden błąd, zwraca całkowitą liczbę wysłanych znaków. (Należy zauważyć, że może to być mniejsza niż liczba wskazana przez *nBufLen*.) W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [plik GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEACCES Żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEFAULT Parametry *lpBuf* lub *lpSockAddr* nie są częścią przestrzeni adresowej użytkownika lub argument *lpSockAddr* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Nazwa hosta jest nieprawidłowa.

- WSAENETRESET Połączenie musi zostać zresetowane, ponieważ implementacja Windows Sockets go upuściła.

- WSAENOBUFS Implementacja Windows Sockets zgłasza zakleszczenie buforu.

- WSAENOTCONN Gniazdo nie jest podłączone (tylko SOCK_STREAM).

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie jest możliwe `SendTo` wywołanie gniazda `ShutDown` po wywołaniu z *nHow* ustawiona na 1 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i żądana operacja zablokuje.

- WSAEMSGSIZE Gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL Określony adres nie jest dostępny na komputerze lokalnym.

- Z tym gniazdem nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie.

- WSAEDESTADDRREQ Wymagany jest adres docelowy.

- WSAENETUNREACH Sieć nie może być osiągnięta z tego hosta w tej chwili.

### <a name="remarks"></a>Uwagi

`SendTo`jest używany na datagramie lub gniazdach strumienia i służy do zapisywania danych wychodzących na gnieździe. W przypadku gniazd datagramu należy uważać, aby nie przekraczać maksymalnego rozmiaru pakietów `iMaxUdpDg` IP podsieci, który jest podany przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) wypełniony [afxsocketinit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby przekazać niepodzielnie przez podstawowy protokół, zwracany jest błąd WSAEMSGSIZE i nie są przesyłane żadne dane.

Należy zauważyć, że `SendTo` pomyślne zakończenie a nie oznacza, że dane zostały pomyślnie dostarczone.

`SendTo`jest używany tylko w gnieździe SOCK_DGRAM do wysyłania datagramu do określonego gniazda identyfikowanego przez parametr *lpSockAddr.*

Aby wysłać emisję (tylko na SOCK_DGRAM), adres w parametrze *lpSockAddr* powinien być skonstruowany przy użyciu specjalnego adresu IP INADDR_BROADCAST (zdefiniowanego w pliku nagłówkowym Windows Sockets WINSOCK. H) wraz z zamierzonym numerem portu. Lub, jeśli parametr *lpszHostAddress* ma wartość NULL, gniazdo jest skonfigurowane do emisji. Jest ogólnie niewzrównalna dla datagramu emisji, aby przekroczyć rozmiar, w którym może wystąpić fragmentacja, co oznacza, że część danych datagramu (z wyłączeniem nagłówków) nie powinna przekraczać 512 bajtów.

Aby obsłużyć adresy IPv6, użyj [CAsyncSocket::SendToEx](#sendtoex).

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx

Wywołanie tej funkcji elementu członkowskiego, aby wysłać dane do określonego miejsca docelowego (obsługuje adresy IPv6).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Bufor zawierający dane, które mają być przesyłane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*Port nHost*<br/>
Port identyfikujący aplikację gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, do którego jest podłączony ten obiekt: nazwa komputera, taka jak "ftp.microsoft.com" lub numer kropkowany, taki jak "128.56.22.8".

*nPłgi*<br/>
Określa sposób, w jaki następuje wywołanie. Semantyka tej funkcji jest określana przez opcje gniazda i parametr *nFlags.* Ten ostatni jest konstruowany przez połączenie dowolnej z następujących wartości z operatorem **C++ OR:**

- MSG_DONTROUTE Określa, że dane nie powinny podlegać routingowi. Dostawca gniazd systemu Windows może zignorować tę flagę.

- MSG_OOB Wyślij dane poza pasmem (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Jeśli nie wystąpi `SendToEx` żaden błąd, zwraca całkowitą liczbę wysłanych znaków. (Należy zauważyć, że może to być mniejsza niż liczba wskazana przez *nBufLen*.) W przeciwnym razie zwracana jest wartość SOCKET_ERROR, a określony kod błędu można pobrać, wywołując [plik GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEACCES Żądany adres jest adresem emisji, ale nie ustawiono odpowiedniej flagi.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEFAULT Parametry *lpBuf* lub *lpSockAddr* nie są częścią przestrzeni adresowej użytkownika lub argument *lpSockAddr* jest za mały (mniejszy niż rozmiar struktury [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Nazwa hosta jest nieprawidłowa.

- WSAENETRESET Połączenie musi zostać zresetowane, ponieważ implementacja Windows Sockets go upuściła.

- WSAENOBUFS Implementacja Windows Sockets zgłasza zakleszczenie buforu.

- WSAENOTCONN Gniazdo nie jest podłączone (tylko SOCK_STREAM).

- WSAENOTSOCK Deskryptor nie jest gniazdem.

- Określono MSG_OOB WSAEOPNOTSUPP, ale gniazdo nie jest typu SOCK_STREAM.

- WSAESHUTDOWN Gniazdo zostało wyłączone; nie jest możliwe `SendToEx` wywołanie gniazda `ShutDown` po wywołaniu z *nHow* ustawiona na 1 lub 2.

- WSAEWOULDBLOCK Gniazdo jest oznaczone jako nieblokujące i żądana operacja zablokuje.

- WSAEMSGSIZE Gniazdo jest typu SOCK_DGRAM, a datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.

- WSAECONNABORTED Obwód wirtualny został przerwany z powodu limitu czasu lub innej awarii.

- WSAECONNRESET Obwód wirtualny został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL Określony adres nie jest dostępny na komputerze lokalnym.

- Z tym gniazdem nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie.

- WSAEDESTADDRREQ Wymagany jest adres docelowy.

- WSAENETUNREACH Sieć nie może być osiągnięta z tego hosta w tej chwili.

### <a name="remarks"></a>Uwagi

Ta metoda jest taka sama jak [CAsyncSocket::SendTo](#sendto) z tą różnicą, że obsługuje adresy IPv6, a także starsze protokoły.

`SendToEx`jest używany na datagramie lub gniazdach strumienia i służy do zapisywania danych wychodzących na gnieździe. W przypadku gniazd datagramu należy uważać, aby nie przekraczać maksymalnego rozmiaru pakietów `iMaxUdpDg` IP podsieci, który jest podany przez element w strukturze [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) wypełniony [afxsocketinit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby przekazać niepodzielnie przez podstawowy protokół, zwracany jest błąd WSAEMSGSIZE i nie są przesyłane żadne dane.

Należy zauważyć, że `SendToEx` pomyślne zakończenie a nie oznacza, że dane zostały pomyślnie dostarczone.

`SendToEx`jest używany tylko w gnieździe SOCK_DGRAM do wysyłania datagramu do określonego gniazda identyfikowanego przez parametr *lpSockAddr.*

Aby wysłać emisję (tylko na SOCK_DGRAM), adres w parametrze *lpSockAddr* powinien być skonstruowany przy użyciu specjalnego adresu IP INADDR_BROADCAST (zdefiniowanego w pliku nagłówkowym Windows Sockets WINSOCK. H) wraz z zamierzonym numerem portu. Lub, jeśli parametr *lpszHostAddress* ma wartość NULL, gniazdo jest skonfigurowane do emisji. Jest ogólnie niewzrównalna dla datagramu emisji, aby przekroczyć rozmiar, w którym może wystąpić fragmentacja, co oznacza, że część danych datagramu (z wyłączeniem nagłówków) nie powinna przekraczać 512 bajtów.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockopt

Wywołanie tej funkcji elementu członkowskiego, aby ustawić opcję gniazda.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parametry

*nOptionName (Nazwa)*<br/>
Opcja gniazda, dla której ma być ustawiona wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w którym jest podana wartość żądanej opcji.

*nOptionLen (NOptionLen)*<br/>
Rozmiar buforu *lpOptionValue* w bajtach.

*nPoziom*<br/>
Poziom, na którym zdefiniowano opcję; jedynymi obsługiwanymi poziomami są SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEFAULT *lpOptionValue* nie znajduje się w prawidłowej części przestrzeni adresowej procesu.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAEINVAL *nLevel* jest nieprawidłowy lub informacje zawarte w *lpOptionValue są nieprawidłowe.*

- WSAENETRESET Connection ma limit czasu, gdy SO_KEEPALIVE jest ustawiona.

- WSAENOPROTOOPT Opcja jest nieznana lub nieobsługiwała. W szczególności SO_BROADCAST nie jest obsługiwana w gniazdach typu SOCK_STREAM, podczas gdy SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazdach typu SOCK_DGRAM.

- Połączenie WSAENOTCONN zostało zresetowane po ustawieniu SO_KEEPALIVE.

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`SetSockOpt`ustawia bieżącą wartość opcji gniazda skojarzonej z gniazdem dowolnego typu, w dowolnym stanie. Chociaż opcje mogą istnieć na wielu poziomach protokołu, ta specyfikacja definiuje tylko opcje, które istnieją na najwyższym poziomie "gniazda". Opcje wpływają na operacje gniazda, takie jak czy przyspieszone dane są odbierane w normalnym strumieniu danych, czy komunikaty emisji mogą być wysyłane na gnieździe i tak dalej.

Istnieją dwa typy opcji gniazda: opcje logiczne, które włączają lub wyłączają funkcję lub zachowanie, oraz opcje, które wymagają wartości lub struktury całkowitej. Aby włączyć opcję logiczną, *lpOptionValue* wskazuje liczbę całkowitą niezerową. Aby wyłączyć opcję *lpOptionValue* wskazuje liczbę całkowitą równą zero. *nOptionLen* powinien być `sizeof(BOOL)` równy dla opcji logicznych. W przypadku innych opcji *lpOptionValue* wskazuje liczbę całkowitą lub strukturę zawierającą żądaną wartość opcji, a *nOptionLen* jest długością liczby całkowitej lub struktury.

SO_LINGER steruje akcją podjętą, gdy niewysłane dane `Close` są umieszczane w kolejce na gnieździe, a funkcja jest wywoływana w celu zamknięcia gniazda.

Domyślnie gniazdo nie może być powiązane (zobacz [Bind)](#bind)do adresu lokalnego, który jest już używany. Czasami jednak pożądane może być "ponowne wykorzystanie" adresu w ten sposób. Ponieważ każde połączenie jest jednoznacznie identyfikowane przez kombinację adresów lokalnych i zdalnych, nie ma problemu z posiadaniem dwóch gniazd powiązanych z tym samym adresem lokalnym, o ile adresy zdalne są różne.

Aby poinformować implementację windows `Bind` sockets, że wywołanie gniazda nie powinno być niedozwolone, ponieważ żądany adres jest już używany przez `Bind` inne gniazdo, aplikacja powinna ustawić opcję gniazda SO_REUSEADDR dla gniazda przed wydaniem wywołania. Należy zauważyć, że opcja jest interpretowana `Bind` tylko w momencie wywołania: dlatego nie jest konieczne (ale nieszkodliwe), aby ustawić opcję na gnieździe, które nie ma być związane z istniejącym adresem, i ustawienie lub zresetowanie opcji po `Bind` wywołaniu nie ma wpływu na to lub inne gniazdo.

Aplikacja może zażądać, aby implementacja Windows Sockets umożliwiała korzystanie z pakietów "keep-alive" na połączeniach TCP (Transmission Control Protocol), włączając opcję gniazda SO_KEEPALIVE. Implementacja windows sockets nie musi obsługiwać korzystania z keep-alives: jeśli tak, dokładne semantyki są specyficzne dla implementacji, ale powinny być zgodne z sekcją 4.2.3.6 RFC 1122: "Wymagania dla hostów internetowych — warstwy komunikacji." Jeśli połączenie zostanie przerwane w wyniku "keep-alives" kod błędu WSAENETRESET jest zwracany do wszystkich wywołań w toku na gnieździe, a wszelkie kolejne wywołania zakończy się niepowodzeniem z WSAENOTCONN.

Opcja TCP_NODELAY wyłącza algorytm Nagle'a. Algorytm Nagle służy do zmniejszenia liczby małych pakietów wysyłanych przez hosta przez buforowanie niepotwierdzonych danych wysyłania, dopóki nie będzie można wysłać pełnowymiarowego pakietu. Jednak w przypadku niektórych aplikacji algorytm ten może utrudniać wydajność i TCP_NODELAY może służyć do wyłączania go. Autorzy aplikacji nie należy ustawiać TCP_NODELAY, chyba że wpływ tego jest dobrze zrozumiany i pożądany, ponieważ ustawienie TCP_NODELAY może mieć znaczący negatywny wpływ na wydajność sieci. TCP_NODELAY jest jedyną obsługiwaną opcją gniazda, która używa IPPROTO_TCP poziomu; wszystkie inne opcje używają poziomu SOL_SOCKET.

Niektóre implementacje windows sockets dostarczają informacje o debugowaniu danych wyjściowych, jeśli opcja SO_DEBUG jest ustawiona przez aplikację.

Następujące opcje są obsługiwane `SetSockOpt`dla . Typ identyfikuje typ danych adresowanych przez *lpOptionValue*.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_BROADCAST|Bool|Zezwalaj na transmisję komunikatów na gnieździe.|
|SO_DEBUG|Bool|Rejestrowanie informacji debugowania.|
|SO_DONTLINGER|Bool|Nie blokuj `Close` oczekiwania na wysłanie niewysłanych danych. Ustawienie tej opcji jest równoważne ustawieniu SO_LINGER z ustawioną `l_onoff` na zero.|
|SO_DONTROUTE|Bool|Nie kierować: wysyłać bezpośrednio do interfejsu.|
|SO_KEEPALIVE|Bool|Wyślij keep-alives.|
|So_linger|`struct LINGER`|Posuń `Close` się, jeśli nie ma danych.|
|SO_OOBINLINE|Bool|Odbieranie danych poza pasmem w normalnym strumieniu danych.|
|SO_RCVBUF|**int**|Określ rozmiar buforu dla odbiera.|
|SO_REUSEADDR|Bool|Zezwalaj na powiązanie gniazda z adresem, który jest już używany. (Zobacz [Bind](#bind).)|
|SO_SNDBUF|**int**|Określ rozmiar buforu dla wysyłań.|
|Tcp_nodelay|Bool|Wyłącza algorytm Nagle'a do wysyłania scalania.|

Opcje berkeley Software Distribution (BSD) `SetSockOpt` nie są obsługiwane:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|Bool|Gniazdo nasłuchuje|
|SO_ERROR|**int**|Uzyskaj stan błędu i wyczyść.|
|SO_RCVLOWAT|**int**|Otrzymuj znak niskiej wody.|
|SO_RCVTIMEO|**int**|Limit czasu odbioru|
|SO_SNDLOWAT|**int**|Wyślij znak niskiej wody.|
|SO_SNDTIMEO|**int**|Wyślij limit czasu.|
|SO_TYPE|**int**|Typ gniazda.|
|IP_OPTIONS||Ustaw pole opcji w nagłówku IP.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown

Wywołanie tej funkcji elementu członkowskiego, aby wyłączyć wysyła, odbiera lub obu na gnieździe.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parametry

*Nhow*<br/>
Flaga opisująca typy operacji nie będą już dozwolone, przy użyciu następujących wyliczonych wartości:

- **odbiera = 0**

- **wysyła = 1**

- **oba = 2**

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, a określony kod błędu można pobrać, wywołując [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- WSANOTINITIALISED Przed użyciem tego interfejsu API musi wystąpić pomyślny [afxsocketinit.](../../mfc/reference/application-information-and-management.md#afxsocketinit)

- WSAENETDOWN Implementacja Windows Sockets wykryła, że podsystem sieciowy nie powiódł się.

- WSAEINVAL *nJak* jest nieprawidłowy.

- WSAEINPROGRESS Trwa blokowanie operacji Windows Sockets.

- WSAENOTCONN Gniazdo nie jest podłączone (tylko SOCK_STREAM).

- WSAENOTSOCK Deskryptor nie jest gniazdem.

### <a name="remarks"></a>Uwagi

`ShutDown`jest używany na wszystkich typach gniazd, aby wyłączyć odbiór, transmisję lub oba te elementy. Jeśli *nJak* jest 0, kolejne odbiera na gnieździe będą niedozwolone. Nie ma to wpływu na dolne warstwy protokołu.

W przypadku protokołu TCP (Transmission Control Protocol) okno TCP nie ulega zmianie, a przychodzące dane będą akceptowane (ale nie potwierdzone) do momentu wyczerpania okna. W przypadku protokołu UDP (User Datagram Protocol) przychodzące datagramy są akceptowane i umieszczane w kolejce. W żadnym wypadku nie zostanie wygenerowany pakiet błędów ICMP. Jeśli *nJak* jest 1, kolejne wysłania są niedozwolone. W przypadku gniazd TCP zostanie wysłana fin. Ustawienie *nJak* na 2 wyłącza zarówno wysyła i odbiera, jak opisano powyżej.

Należy `ShutDown` zauważyć, że nie zamyka gniazda, a zasoby dołączone `Close` do gniazda nie zostaną zwolnione, dopóki nie zostanie wywołana. Aplikacja nie powinna polegać na możliwości ponownego użycia gniazda po jego zamknięciu. W szczególności implementacja Windows Sockets nie jest wymagana `Connect` do obsługi korzystania z takiego gniazda.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Gniazdo

Przydziela uchwyt gniazda.

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

*Levent*<br/>
Maska bitowa określająca kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- `FD_READ`: Chcesz otrzymywać powiadomienie o gotowości do czytania.

- `FD_WRITE`: Chcesz otrzymywać powiadomienie o gotowości do pisania.

- `FD_OOB`: Chcesz otrzymywać powiadomienia o nadejściu danych poza pasmem.

- `FD_ACCEPT`: Chcesz otrzymywać powiadomienia o połączeniach przychodzących.

- `FD_CONNECT`: Chcesz otrzymywać powiadomienia o zakończonym połączeniu.

- `FD_CLOSE`: Chcesz otrzymywać powiadomienia o zamknięciu gniazda.

*nProtocolType*<br/>
Protokół używany z gniazdem specyficznym dla wskazanej rodziny adresów.

*nAddressFormat*<br/>
Adres specyfikacji rodziny.

### <a name="return-value"></a>Wartość zwracana

Powraca `TRUE` po `FALSE` sukcesie, po porażce.

### <a name="remarks"></a>Uwagi

Ta metoda przydziela dojście gniazda. Nie wywołanie [CAsyncSocket::Bind](#bind) do powiązania gniazda do określonego adresu, `Bind` więc należy wywołać później, aby powiązać gniazdo do określonego adresu. [CAsyncSocket::SetSockOpt](#setsockopt) można ustawić opcję gniazda przed jej powiązaniem.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
