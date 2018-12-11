---
title: Klasa CAsyncSocket
ms.date: 11/04/2016
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
ms.openlocfilehash: b138c4f84a10823d9c340218baefd530c016027a
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53179035"
---
# <a name="casyncsocket-class"></a>Klasa CAsyncSocket

Przedstawia gniazdo Windows — punkt końcowy komunikacji sieciowej.

## <a name="syntax"></a>Składnia

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Konstruuje `CAsyncSocket` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::Accept](#accept)|Akceptuje połączenia w gnieździe.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Powiadomienie o zdarzeniu żądania dla gniazda.|
|[CAsyncSocket::Attach](#attach)|Dołącza dojścia do gniazda `CAsyncSocket` obiektu.|
|[CAsyncSocket::Bind](#bind)|Kojarzy adresu lokalnego z gniazda.|
|[CAsyncSocket::Close](#close)|Zamyka gniazda.|
|[CAsyncSocket::Connect](#connect)|Ustanawia połączenie z gniazdem elementów równorzędnych.|
|[CAsyncSocket::Create](#create)|Tworzy gniazdo.|
|[CAsyncSocket::Detach](#detach)|Odłącza dojścia do gniazda z `CAsyncSocket` obiektu.|
|[CAsyncSocket::FromHandle](#fromhandle)|Zwraca wskaźnik do `CAsyncSocket` obiektu, biorąc pod uwagę uchwyt gniazda.|
|[CAsyncSocket::GetLastError](#getlasterror)|Pobiera stan błędu Ostatnia operacja, która nie powiodła się.|
|[CAsyncSocket::GetPeerName](#getpeername)|Pobiera adres gniazda elementów równorzędnych, z którą jest połączony gniazda.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Pobiera adres gniazda równorzędnej gniazda jest połączonych (uchwytów adresów IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Pobiera nazwę lokalnego dla gniazda.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Pobiera nazwę lokalnego dla gniazda (uchwytów adresów IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Pobiera opcję gniazda.|
|[CAsyncSocket::IOCtl](#ioctl)|Określa tryb gniazda.|
|[CAsyncSocket::Listen](#listen)|Ustanawia gniazda, aby nasłuchiwać żądań połączenia przychodzących.|
|[CAsyncSocket::Receive](#receive)|Odbiera dane z gniazda.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Odbiera datagram i przechowuje adres źródłowy.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Odbiera datagram i przechowuje adres źródłowy (uchwytów adresów IPv6).|
|[CAsyncSocket::Send](#send)|Wysyła dane do połączone gniazdo.|
|[CAsyncSocket::SendTo](#sendto)|Wysyła dane do określonego miejsca docelowego.|
|[CAsyncSocket::SendToEx](#sendtoex)|Wysyła dane do określonego miejsca docelowego (uchwytów adresów IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Ustawia opcję gniazda.|
|[CAsyncSocket::ShutDown](#shutdown)|Wyłącza `Send` i/lub `Receive` wywołuje dla gniazda.|
|[CASyncSocket::Socket](#socket)|Przydziela dojścia do gniazda.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Powiadamia nasłuchiwania gniazda, który może akceptować oczekujące żądania połączenia, wywołując `Accept`.|
|[CAsyncSocket::OnClose](#onclose)|Powiadamia gniazda, który jest połączony gniazda zostało zamknięte.|
|[CAsyncSocket::OnConnect](#onconnect)|Połączenie gniazda, próba połączenia powiadamia o ukończeniu procesu, czy pomyślnie, lub w wyniku błędu.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Powiadamia gniazda odbierania, ma danych poza pasmem do odczytu w gnieździe, zwykle pilne wiadomości.|
|[CAsyncSocket::OnReceive](#onreceive)|Powiadamia nasłuchiwania gniazda, ma danych do pobrania przez wywołanie metody `Receive`.|
|[CAsyncSocket::OnSend](#onsend)|Powiadamia gniazdo, że mogą wysyłać dane, wywołując `Send`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Przypisuje nową wartość do `CAsyncSocket` obiektu.|
|[CAsyncSocket::operator GNIAZDA](#operator_socket)|Użyj tego operatora, aby pobrać uchwyt GNIAZDA `CAsyncSocket` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Wskazuje, dołączony do tego dojścia do GNIAZDA `CAsyncSocket` obiektu.|

## <a name="remarks"></a>Uwagi

Klasa `CAsyncSocket` hermetyzuje Windows gniazda funkcji interfejsu API, zapewniając abstrakcję zorientowane obiektowo dla programistów, którzy chcą używać Windows Sockets w połączeniu z MFC.

Ta klasa opiera się na założeniu, że rozumiesz komunikacji sieciowej. Jesteś odpowiedzialny za obsługę, blokowanie, różnice w kolejności bajtów i konwersji między Unicode i multibyte character Ustaw ciągów (znaków MBCS). Jeśli chcesz bardziej wygodne interfejs, który zarządza tymi problemami, zobacz klasę [CSocket](../../mfc/reference/csocket-class.md).

Do użycia `CAsyncSocket` obiektu, wywołaj jej konstruktora, następnie wywołać [Utwórz](#create) funkcja służąca do tworzenia podstawowego dojścia do gniazda (typ `SOCKET`), z wyjątkiem gniazda akceptowane. Połączenie gniazda serwera [nasłuchiwania](#listen) funkcja elementu członkowskiego i połączenia gniazda klienta [Connect](#connect) funkcja elementu członkowskiego. Gniazda serwera powinien wywoływać [Akceptuj](#accept) funkcji po otrzymaniu żądania połączenia. Użyj pozostałe `CAsyncSocket` funkcje do przeprowadzania komunikacji między gniazda. Po zakończeniu zniszczyć `CAsyncSocket` obiektu, jeśli został utworzony na stercie; destruktor automatycznie wywołuje [Zamknij](#close) funkcji. Typ danych GNIAZDA jest opisany w artykule [Windows Sockets: Tło](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  Korzystając z MFC gniazd w pomocnicze wątki w statycznie połączonym aplikacji MFC, należy wywołać `AfxSocketInit` w każdy wątek, który używa gniazda można zainicjować biblioteki gniazda. Domyślnie `AfxSocketInit` jest wywoływana tylko w wątku głównym.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Używanie klasy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) i powiązanych artykułach., a także [Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsock.h

##  <a name="accept"></a>  CAsyncSocket::Accept

Wywołaj tę funkcję elementu członkowskiego, aby akceptować połączenia dla gniazda.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parametry

*rConnectedSocket*<br/>
Odwołanie identyfikuje nowe gniazdo, który jest dostępny dla połączenia.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która otrzymuje adres nawiązywaniu połączenia gniazda znane w sieci. Dokładny format *lpSockAddr* argument jest określana przez Rodzina adresów ustalone podczas tworzenia gniazda. Jeśli *lpSockAddr* i/lub *lpSockAddrLen* są równe NULL, zwracana jest żadnych informacji dotyczących adresów zdalnych akceptowane gniazda.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. *LpSockAddrLen* jest parametrem wynik wartości: początkowo powinien on zawierać ilość miejsca, do których prowadzą *lpSockAddr*; przy powrocie będzie zawierać rzeczywista długość (w bajtach) zwrócony adres.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument jest za mały (mniejszą niż rozmiar [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury).

- WSAEINPROGRESS który wywołania blokowania Windows Sockets jest w toku.

- WSAEINVAL `Listen` nie została wywołana przed zaakceptować.

- WSAEMFILE kolejka jest pusta, po wejściu do akceptowania i są dostępne nie deskryptorów.

- Ilość miejsca w buforze WSAENOBUFS nie jest dostępna.

- WSAENOTSOCK deskryptor nie jest gniazda.

- WSAEOPNOTSUPP gniazda odwołania nie jest typem, który obsługuje usługę ukierunkowane na połączenia.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i połączenia nie są obecne do zaakceptowania.

### <a name="remarks"></a>Uwagi

Ta procedura wyodrębnia pierwszego połączenia w kolejce oczekujących połączeń, tworzy nowe gniazdo z tymi samymi właściwościami co tego gniazda i dołącza go do *rConnectedSocket*. Jeśli żadne oczekujące połączenia znajdują się w kolejce, `Accept` zwraca zero i `GetLastError` zwraca błąd. Zaakceptowane gniazda ( *rConnectedSocket)* nie można zaakceptować więcej połączeń. Oryginalny gniazda pozostaje otwarty i czy działa nasłuchiwanie.

Argument *lpSockAddr* jest parametr wynik, który jest wypełniane adresem połączenia gniazda, ponieważ wiadomo, że warstwa komunikacji. `Accept` jest używana z typami gniazda opartego na połączeniach, takie jak SOCK_STREAM.

##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect

Wywołaj tę funkcję elementu członkowskiego, aby zażądać powiadomień o zdarzeniach dla gniazda.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*lEvent*<br/>
Maska bitów, który określa kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ chcesz otrzymać powiadomienie o gotowości do odczytu.

- FD_WRITE chcesz otrzymać powiadomienie, gdy dane są dostępne do odczytu.

- FD_OOB chcesz otrzymać powiadomienie o dostarczeniu danych poza pasmem.

- FD_ACCEPT chcesz otrzymać powiadomienie o połączeń przychodzących.

- FD_CONNECT chcesz otrzymać powiadomienie o wynikach połączenia.

- FD_CLOSE chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEINVAL wskazuje, że jedna z określonych parametrów jest nieprawidłowy.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana do określenia, które funkcje MFC wywołania zwrotnego powiadomień zostanie wywołana dla gniazda. `AsyncSelect` automatycznie ustawia tryb nieblokujących tego gniazda. Aby uzyskać więcej informacji, zobacz artykuł [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="attach"></a>  CAsyncSocket::Attach

Wywołaj tę funkcję elementu członkowskiego, aby dołączyć *hSocket* uchwytu do `CAsyncSocket` obiektu.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera dojścia do gniazda.

*lEvent*<br/>
Maska bitów, który określa kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ chcesz otrzymać powiadomienie o gotowości do odczytu.

- FD_WRITE chcesz otrzymać powiadomienie, gdy dane są dostępne do odczytu.

- FD_OOB chcesz otrzymać powiadomienie o dostarczeniu danych poza pasmem.

- FD_ACCEPT chcesz otrzymać powiadomienie o połączeń przychodzących.

- FD_CONNECT chcesz otrzymać powiadomienie o wynikach połączenia.

- FD_CLOSE chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli funkcja się powiedzie.

### <a name="remarks"></a>Uwagi

Uchwyt GNIAZDA są przechowywane w obiekcie [m_hSocket](#m_hsocket) element członkowski danych.

##  <a name="bind"></a>  CAsyncSocket::Bind

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć adresu lokalnego z gniazda.

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
Port identyfikowanie aplikacji gniazda.

*lpszSocketAddress*<br/>
Adres sieciowy liczbą kropkowana, takie jak "128.56.22.8". Przekazanie wartości NULL ciągu dla tego parametru oznacza `CAsyncSocket` wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która zawiera adres, który zostanie przypisany do tego gniazda.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEADDRINUSE określony adres jest już używana. (Zobacz opcję gniazda SO_REUSEADDR w obszarze [SetSockOpt](#setsockopt).)

- WSAEFAULT *nSockAddrLen* argument jest za mały (mniejszą niż rozmiar [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury).

- WSAEINPROGRESS który wywołania blokowania Windows Sockets jest w toku.

- WSAEAFNOSUPPORT rodziny określony adres nie jest obsługiwana przez ten port.

- WSAEINVAL gniazda jest już powiązana z adresem.

- Nie WSAENOBUFS wystarczająco buforuje dostępne, zbyt wiele połączeń.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

Ta procedura jest używana na niepołączonych datagram lub w gnieździe strumienia przed kolejnych `Connect` lub `Listen` wywołania. Zanim będzie mógł akceptować żądań połączeń, nasłuchiwania gniazda serwera należy wybrać numer portu i poinformuj Windows Sockets, wywołując `Bind`. `Bind` ustanawia skojarzenie lokalne (host adresu/numeru portu) gniazda, przypisując nazwę lokalnego do gniazda bez nazwy.

##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket

Tworzy obiekt do pustego gniazda.

```
CAsyncSocket();
```

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, należy wywołać jej `Create` funkcja elementu członkowskiego do tworzenia struktury danych GNIAZDA i powiąż jego adresu. (Po stronie serwera w komunikacji z Windows Sockets nasłuchiwania gniazda tworzy gniazdo do użycia w `Accept` wywołanie, nie zostanie wywołana `Create` dla tego gniazda.)

##  <a name="close"></a>  CAsyncSocket::Close

Zamyka gniazda.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Ta funkcja zwolni deskryptora gniazda tak, aby dodatkowo odwołania do niego zakończy się niepowodzeniem z powodu błędu WSAENOTSOCK. Jeśli jest to ostatnie odwołanie do podstawowej gniazda, skojarzone informacje dotyczące nazewnictwa i umieszczone w kolejce dane zostaną odrzucone. Obiekt gniazda wywołania destruktora `Close` dla Ciebie.

Dla `CAsyncSocket`, ale nie dla `CSocket`, semantykę `Close` dotyczy opcji gniazda SO_LINGER i SO_DONTLINGER. Aby uzyskać więcej informacji, zobacz Funkcja elementu członkowskiego `GetSockOpt`.

##  <a name="connect"></a>  CAsyncSocket::Connect

Wywołaj tę funkcję elementu członkowskiego, aby nawiązać połączenie z strumienia o odłączony lub w gnieździe datagram.

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
Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa maszyny, takie jak "pod adresem" lub liczbą kropkowana, takie jak "128.56.22.8".

*nHostPort*<br/>
Port identyfikowanie aplikacji gniazda.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która zawiera adres połączone gniazdo.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Jeśli oznacza to, kod błędu WSAEWOULDBLOCK, a aplikacja korzysta z możliwością wywołania zwrotne, aplikacja będzie odbierać `OnConnect` komunikat po zakończeniu operacji nawiązywania połączenia. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEADDRINUSE określony adres jest już używana.

- WSAEINPROGRESS który wywołania blokowania Windows Sockets jest w toku.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny z maszyny lokalnej.

- Nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie z tego gniazda.

- WSAECONNREFUSED próby nawiązania połączenia zostało odrzucone.

- Wymagany jest adres docelowy element WSAEDESTADDRREQ.

- WSAEFAULT *nSockAddrLen* argument jest nieprawidłowy.

- WSAEINVAL nieprawidłowy adres hosta.

- WSAEISCONN gniazda jest już połączony.

- Brak WSAEMFILE więcej dostępnych deskryptorów plików.

- WSAENETUNREACH sieci nie można nawiązać połączenia z tego hosta w tej chwili.

- Ilość miejsca w buforze WSAENOBUFS nie jest dostępna. Nie można połączyć gniazda.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Upłynął limit czasu WSAETIMEDOUT próba nawiązania połączenia bez ustanawiania połączenia.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i połączenia nie może zostać zakończona natychmiast.

### <a name="remarks"></a>Uwagi

Jeśli gniazda jest niezwiązany, unikatowe wartości są przypisane do lokalnych skojarzenia przez system i gniazda jest oznaczony jako powiązana. Należy pamiętać, że jeśli pole Adres struktury nazw jest zer, `Connect` zwróci wartość zero. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError` funkcja elementu członkowskiego.

Dla gniazda strumieni (typ SOCK_STREAM) inicjowane jest aktywne połączenie w celu obcego hosta. Po pomyślnym zakończeniu wywołanie gniazda gniazda jest gotowy do wysyłania i odbierania danych.

Dla gniazda datagramów (typ SOCK_DGRAM) ustawiono domyślne miejsce docelowe, które będą używane w kolejnych `Send` i `Receive` wywołania.

##  <a name="create"></a>  CAsyncSocket::Create

Wywołaj `Create` funkcja elementu członkowskiego po konstruowanie obiektu gniazda, aby utworzyć gniazda Windows i dołączyć go.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Dobrze znany port do użycia z gniazda lub 0, jeśli chcesz, aby Windows Sockets, aby wybrać port.

*nSocketType*<br/>
SOCK_STREAM lub SOCK_DGRAM.

*lEvent*<br/>
Maska bitów, który określa kombinację zdarzeń sieciowych, w których aplikacja jest zainteresowana.

- FD_READ chcesz otrzymać powiadomienie o gotowości do odczytu.

- FD_WRITE chcesz otrzymać powiadomienie o gotowości do zapisu.

- FD_OOB chcesz otrzymać powiadomienie o dostarczeniu danych poza pasmem.

- FD_ACCEPT chcesz otrzymać powiadomienie o połączeń przychodzących.

- FD_CONNECT chcesz otrzymać powiadomienie o zakończonych połączeń.

- FD_CLOSE chcesz otrzymać powiadomienie o zamknięcia gniazda.

*lpszSockAddress*<br/>
Wskaźnik do ciągu zawierającego adres sieciowy połączone gniazdo, liczbą kropkowana, takie jak "128.56.22.8". Przekazanie wartości NULL ciągu dla tego parametru oznacza `CAsyncSocket` wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEAFNOSUPPORT rodziny określony adres nie jest obsługiwane.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- Brak WSAEMFILE więcej dostępnych deskryptorów plików.

- Ilość miejsca w buforze WSAENOBUFS nie jest dostępna. Nie można utworzyć gniazda.

- WSAEPROTONOSUPPORT określony port nie jest obsługiwane.

- WSAEPROTOTYPE określonego portu jest nieprawidłowy typ dla tego gniazda.

- WSAESOCKTNOSUPPORT podanego typu gniazda nie jest obsługiwana w tej rodzinie adresów.

### <a name="remarks"></a>Uwagi

`Create` wywołania [gniazda](#socket) , a jeśli to się powiedzie, wywołuje [powiązać](#bind) powiązać gniazda z określonego adresu. Obsługiwane są następujące typy gniazda:

- Udostępnia SOCK_STREAM sekwencjonowania, strumienie bajtów niezawodne, pełny dupleks, opartego na połączeniach. Używa Transmission Control Protocol (TCP) dla internetowej rodziny adresowej.

- Datagramy SOCK_DGRAM obsługuje przesyłanie, zawodne pakietów stała długość maksymalną (zazwyczaj małego). Używa protokołu UDP (User Datagram) dla internetowej rodziny adresowej.

    > [!NOTE]
    >  `Accept` Funkcja elementu członkowskiego przyjmuje odwołanie do nowy, pusty `CSocket` obiekt jako parametr. Należy utworzyć ten obiekt przed wywołaniem `Accept`. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. Nie wywołuj `Create` dla tego nowego obiektu gniazda.

> [!IMPORTANT]
> `Create` jest **nie** metodą o bezpiecznych wątkach.  Jeśli wywołujesz ją w środowisku wielowątkowych go może zostać przywołane jednocześnie przez inne wątki, pamiętaj chronić każdego wywołania elementu mutex lub innych lock synchronizacji.

Aby uzyskać więcej informacji na temat usługi stream i datagram gniazda, zobacz artykuły [Windows Sockets: Tło](../../mfc/windows-sockets-background.md) i [Windows Sockets: Porty i adresy gniazd](../../mfc/windows-sockets-ports-and-socket-addresses.md) i [interfejsu Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>  CAsyncSocket::Detach

Wywołaj tę funkcję elementu członkowskiego, aby odłączyć uchwyt GNIAZDA w *m_hSocket* element członkowski danych z `CAsyncSocket` obiektu i ustaw *m_hSocket* na wartość NULL.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle

Zwraca wskaźnik do `CAsyncSocket` obiektu.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Zawiera dojścia do gniazda.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CAsyncSocket` obiekt lub wartość NULL, jeśli ma nie `CAsyncSocket` obiekt dołączony do *hSocket*.

### <a name="remarks"></a>Uwagi

Gdy zwracany uchwyt GNIAZDA, jeśli `CAsyncSocket` obiektu nie jest dołączony do uchwytu, funkcja elementu członkowskiego zwraca wartość NULL.

##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać stan błędu Ostatnia operacja, która nie powiodła się.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość wskazuje kod błędu dla ostatniej procedury interfejsu API programu Windows Sockets, wykonywane przez ten wątek.

### <a name="remarks"></a>Uwagi

Gdy funkcja określony element członkowski wskazuje, że wystąpił błąd, `GetLastError` powinna być wywoływana, aby pobrać kod odpowiedni komunikat o błędzie. Zobacz opisy funkcji poszczególnym członkom listę kodów błędów dotyczy.

Aby uzyskać więcej informacji o kodach błędów, zobacz [Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać adres gniazda elementów równorzędnych, do którego jest podłączony tego gniazda.

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
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rPeerPort*<br/>
Odwołanie do UINT, która przechowuje portu.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury, która otrzymuje nazwę gniazda elementów równorzędnych.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach. Przy powrocie *lpSockAddrLen* argument zawiera rzeczywisty rozmiar *lpSockAddr* zwracany w bajtach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument nie jest wystarczająco duży.

- WSAEINPROGRESS który wywołania blokowania Windows Sockets jest w toku.

- WSAENOTCONN gniazda nie jest połączony.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx

Wywołaj tę funkcję elementu członkowskiego, aby pobrać adres gniazda równorzędnej to gniazdo jest połączonych (uchwytów adresów IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parametry

*rPeerAddress*<br/>
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rPeerPort*<br/>
Odwołanie do UINT, która przechowuje portu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument nie jest wystarczająco duży.

- WSAEINPROGRESS który wywołania blokowania Windows Sockets jest w toku.

- WSAENOTCONN gniazda nie jest połączony.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

Ta funkcja jest taka sama jak [CAsyncSocket::GetPeerName](#getpeername) z tą różnicą, że ta obsługuje protokół IPv6 rozwiązuje również jako starszych protokołów.

##  <a name="getsockname"></a>  CAsyncSocket::GetSockName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwy lokalnego dla gniazda.

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
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rSocketPort*<br/>
Odwołanie do UINT, która przechowuje portu.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która otrzymuje adres gniazda.

*lpSockAddrLen*<br/>
Wskaźnik do długości adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument nie jest wystarczająco duży.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Gniazda nie została powiązana z adresem z WSAEINVAL `Bind`.

### <a name="remarks"></a>Uwagi

To wywołanie jest szczególnie przydatne, gdy `Connect` nawiązano połączenie bez to `Bind` najpierw; to wywołanie dostarcza tylko oznacza, że za pomocą którego można określić skojarzenie lokalne, który został ustawiony przez system.

Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać nazwy lokalnego dla gniazda (uchwytów adresów IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parametry

*rSocketAddress*<br/>
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rSocketPort*<br/>
Odwołanie do UINT, która przechowuje portu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument nie jest wystarczająco duży.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Gniazda nie została powiązana z adresem z WSAEINVAL `Bind`.

### <a name="remarks"></a>Uwagi

To wywołanie jest taka sama jak [CAsyncSocket::GetSockName](#getsockname) z tą różnicą, że ta obsługuje protokół IPv6 rozwiązuje również jako starszych protokołów.

To wywołanie jest szczególnie przydatne, gdy `Connect` nawiązano połączenie bez to `Bind` najpierw; to wywołanie dostarcza tylko oznacza, że za pomocą którego można określić skojarzenie lokalne, który został ustawiony przez system.

##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt

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
Opcja gniazda, dla którego ma być pobrana wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w której jest zwracana wartość żądanej opcji. Wartość skojarzona z wybraną opcję jest zwracany w buforze *lpOptionValue*. Liczba całkowita, wskazywana przez *lpOptionLen* pierwotnie powinien zawierać rozmiaru buforu w bajtach; i przy powrocie, zostanie ustawiony rozmiar wartości zwracanej. W przypadku SO_LINGER, będzie to rozmiar `LINGER` struktury; w przypadku wszystkich innych opcji będzie rozmiar typu wartość logiczna lub **int**, w zależności od opcji. Zobacz listę opcji i ich rozmiary, w sekcji uwag.

*lpOptionLen*<br/>
Wskaźnik do rozmiaru *lpOptionValue* buforu w bajtach.

*nLevel*<br/>
Poziom, na którym jest zdefiniowana opcja; tylko obsługiwane poziomy są SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Jeśli nigdy nie ustawiono opcję z `SetSockOpt`, następnie `GetSockOpt` zwraca wartości domyślne dla opcji. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpOptionLen* argument ten był nieprawidłowy.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOPROTOOPT opcją jest nieznany lub nieobsługiwany. W szczególności SO_BROADCAST nie jest obsługiwana na sockets SOCK_STREAM podczas SO_ACCEPTCONN SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazda typu SOCK_DGRAM typu.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

`GetSockOpt` pobiera bieżącą wartość dla opcji gniazda skojarzone z gniazda dowolnego typu, w dowolnym stanie i zapisuje wynik w *lpOptionValue*. Opcje mają wpływ na operacje gniazda, takie jak routing pakietów, transfer danych poza pasmem i tak dalej.

Poniższe opcje są obsługiwane w przypadku `GetSockOpt`. Typ określa typ danych, które zostały rozwiązane przez *lpOptionValue*. Opcja TCP_NODELAY przy użyciu poziomu IPPROTO_TCP; wszystkie inne opcje Użyj poziomu SOL_SOCKET.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|WARTOŚĆ LOGICZNA|Nasłuchuje gniazda.|
|SO_BROADCAST|WARTOŚĆ LOGICZNA|Gniazda jest skonfigurowany dla transmisji komunikatów emisji.|
|SO_DEBUG|WARTOŚĆ LOGICZNA|Debugowanie jest włączone.|
|SO_DONTLINGER|WARTOŚĆ LOGICZNA|W przypadku opcji true opcja SO_LINGER jest wyłączona.|
|SO_DONTROUTE|WARTOŚĆ LOGICZNA|Routing jest wyłączony.|
|SO_ERROR|**int**|Pobierz stan błędu i usuń zaznaczenie.|
|SO_KEEPALIVE|WARTOŚĆ LOGICZNA|Utrzymywania aktywności są wysyłane.|
|SO_LINGER|`struct LINGER`|Zwraca bieżące opcje linger —.|
|SO_OOBINLINE|WARTOŚĆ LOGICZNA|Out-of-band danych jest odbierany w strumieniu danych normalny.|
|SO_RCVBUF|int|Rozmiar buforu dla odbiera.|
|SO_REUSEADDR|WARTOŚĆ LOGICZNA|Gniazda może być powiązana z adres, który jest już używana.|
|SO_SNDBUF|**int**|Rozmiar buforu dla wysyła.|
|SO_TYPE|**int**|Typ gniazda (na przykład SOCK_STREAM).|
|TCP_NODELAY|WARTOŚĆ LOGICZNA|Wyłącza algorytm Nagle'a łączenie wysyłania.|

Opcje dystrybucji oprogramowania Berkeley (BSD) nie jest obsługiwane dla `GetSockOpt` są:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Odbieranie znaku wodnym niskiego.|
|SO_RCVTIMEO|**int**|Otrzymywać limit czasu.|
|SO_SNDLOWAT|**int**|Wyślij znaku wodnym niskiego.|
|SO_SNDTIMEO|**int**|Limitu czasu wysyłania.|
|IP_OPTIONS||Pobierz opcje w nagłówku protokołu IP.|
|TCP_MAXSEG|**int**|Uzyskaj TCP maksymalny rozmiar segmentu.|

Wywoływanie `GetSockOpt` z Nieobsługiwana opcja spowoduje kod błędu WSAENOPROTOOPT zwracanego `GetLastError`.

##  <a name="ioctl"></a>  CAsyncSocket::IOCtl

Wywołaj tę funkcję elementu członkowskiego do sterowania trybem gniazda.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parametry

*lCommand*<br/>
Polecenie do wykonania w gnieździe.

*lpArgument*<br/>
Wskaźnik do parametru *lCommand*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEINVAL *lCommand* nie jest prawidłowym poleceniem lub *lpArgument* nie jest dopuszczalne parametrem *lCommand*, lub polecenia nie ma zastosowania do typu gniazda dostarczony .

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

Ta procedura może służyć w dowolnym gniazda w dowolnym stanie. Służy do pobierania lub pobrać parametry operacyjne skojarzone z gniazda, niezależnie od podsystemu protokołu i komunikacji. Obsługiwane są następujące polecenia:

- FIONBIO Włącz lub wyłącz tryb nieblokujących w gnieździe. *LpArgument* parametr wskazuje na `DWORD`, który jest różny od zera, jeśli można włączyć tryb nieblokujących i zero, jeśli jest wyłączone. Jeśli `AsyncSelect` został wystawiony dla gniazda, a następnie dowolne próba użycia `IOCtl` można ustawić gniazda z powrotem w tryb blokowania zakończy się niepowodzeniem z WSAEINVAL. Aby wartość gniazda tryb blokowania i zapobiec błąd WSAEINVAL, należy najpierw wyłączyć aplikację `AsyncSelect` przez wywołanie metody `AsyncSelect` z *lEvent* parametru równa 0, następnie wywołać `IOCtl`.

- FIONREAD określić maksymalną liczbę bajtów, które mogą być odczytywane przy użyciu jednego `Receive` wywołać z tego gniazda. *LpArgument* parametr wskazuje na `DWORD` w którym `IOCtl` zapisuje wynik. W przypadku tego gniazda typu SOCK_STREAM, FIONREAD zwraca łączna ilość danych, które mogą być odczytywane w jednym `Receive`; to jest zwykle taka sama jak łączna ilość danych w kolejce w gnieździe. W przypadku tego gniazda typu SOCK_DGRAM, FIONREAD zwróci rozmiar datagram pierwszy w kolejce w gnieździe.

- SIOCATMARK ustalić, czy wszystkie dane poza pasmem został odczytany. Dotyczy to tylko gniazda typu SOCK_STREAM, który został skonfigurowany do odbioru w tekście dowolnych danych poza pasmem (SO_OOBINLINE). Jeśli żadne dane poza pasmem oczekuje do odczytu, operacja zwraca wartość różną od zera. W przeciwnym razie zwraca wartość 0, a następnie `Receive` lub `ReceiveFrom` wykonywane na gniazdo pobierze niektórych lub wszystkich danych poprzedzających "znakiem"; aplikacja powinna używać operacji SIOCATMARK, aby ustalić, czy wszystkie dane pozostają. W przypadku wszelkich danych normalne poprzedzających "pilnych" danych (poza pasmem) będą odbierane w kolejności. (Należy pamiętać, że `Receive` lub `ReceiveFrom` będzie nigdy nie Mieszaj out-of-band i normalne danych w tym samym wywołaniu.) *LpArgument* parametr wskazuje na `DWORD` w którym `IOCtl` zapisuje wynik.

Ta funkcja jest podzbiorem `ioctl()` w Berkeley gniazda. W szczególności nie ma żadnego polecenia, co jest równoważne z FIOASYNC, w trakcie SIOCATMARK polecenia tylko gniazda na poziomie, który jest obsługiwany.

##  <a name="listen"></a>  CAsyncSocket::Listen

Wywołaj tę funkcję elementu członkowskiego, aby nasłuchiwać żądań połączenia przychodzących.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parametry

*nConnectionBacklog*<br/>
Maksymalna długość, do którego można powiększać kolejka oczekujących połączeń. Prawidłowy zakres to od 1 do 5.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEADDRINUSE zostanie podjęta próba stało się do nasłuchiwania na adres w użyciu.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- Gniazda nie została powiązana z WSAEINVAL `Bind` lub został już połączony.

- WSAEISCONN gniazda jest już połączony.

- Brak WSAEMFILE więcej dostępnych deskryptorów plików.

- Ilość miejsca w buforze WSAENOBUFS nie jest dostępna.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Gniazda odwołania nie jest typu, który obsługuje WSAEOPNOTSUPP `Listen` operacji.

### <a name="remarks"></a>Uwagi

Do akceptowania połączeń, gniazda tworzona jest najpierw za pomocą `Create`, listy prac dla połączeń przychodzących jest określony za pomocą `Listen`, a następnie połączenia są akceptowane z `Accept`. `Listen` dotyczy tylko gniazd, które obsługują połączenia, oznacza to, że te typu SOCK_STREAM. Tego gniazda zostanie przełączone w tryb "pasywny", gdzie potwierdzone i umieszczane w kolejce do czasu zatwierdzenia przez proces połączeń przychodzących.

Ta funkcja jest zwykle używane przez serwery (lub inna aplikacja chce, aby akceptował połączenia), może mieć więcej niż jedno żądanie połączenia w czasie: Jeśli żądanie połączenia zostanie odebrana z pełną kolejką, klient otrzyma błąd ze wskazaniem WSAECONNREFUSED.

`Listen` podejmuje próbę kontynuowania działania racjonalne, gdy nie dostępnych portów (deskryptory). Go będzie akceptować połączenia, dopóki opróżnieniu kolejki. Jeśli porty stają się dostępne, nowsze wywołanie `Listen` lub `Accept` uzupełnienie kolejki do bieżącej lub najnowszych "zaległości,", jeśli jest to możliwe, a wznowienie nasłuchuje połączeń przychodzących.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Uchwyt GNIAZDA dla gniazda hermetyzowane to zawiera `CAsyncSocket` obiektu.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>  CAsyncSocket::OnAccept

Wywoływane przez platformę, by powiadomić gniazdo nasłuchiwania, który może akceptować oczekujące żądania połączenia, wywołując [Akceptuj](#accept) funkcja elementu członkowskiego.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów ma zastosowanie do `OnAccept` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onclose"></a>  CAsyncSocket::OnClose

Metoda wywoływana przez platformę, by powiadomić tego gniazda, że połączone gniazdo jest zamknięty przez jego proces.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnClose` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAECONNRESET połączenie zostało zresetowane przez stronę zdalną.

- WSAECONNABORTED połączenie zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onconnect"></a>  CAsyncSocket::OnConnect

Metoda wywoływana przez platformę, by powiadomić tego połączenia gniazda, że jego zakończyła się próba połączenia, czy pomyślnie, lub w wyniku błędu.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnConnect` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- WSAEADDRINUSE określony adres jest już używana.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny z maszyny lokalnej.

- Nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie z tego gniazda.

- Wymuszone odrzucono WSAECONNREFUSED próby nawiązania połączenia.

- Wymagany jest adres docelowy element WSAEDESTADDRREQ.

- WSAEFAULT *lpSockAddrLen* argument jest nieprawidłowy.

- WSAEINVAL gniazda jest już powiązana z adresem.

- WSAEISCONN gniazda jest już połączony.

- Brak WSAEMFILE więcej dostępnych deskryptorów plików.

- WSAENETUNREACH sieci nie można nawiązać połączenia z tego hosta w tej chwili.

- Ilość miejsca w buforze WSAENOBUFS nie jest dostępna. Nie można połączyć gniazda.

- WSAENOTCONN gniazda nie jest połączony.

- WSAENOTSOCK deskryptor jest plikiem, nie gniazda.

- Upłynął limit czasu WSAETIMEDOUT próby nawiązania połączenia bez ustanawiania połączenia.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  W [CSocket](../../mfc/reference/csocket-class.md), `OnConnect` nigdy nie jest wywoływana funkcja powiadamiania. W przypadku połączeń, należy po prostu wywołać `Connect`, co spowoduje zwrócenie zakończeniu połączenie (pomyślnie lub w wyniku błędu). Sposób obsługi powiadomień połączenia jest szczegółowo opisuje implementacja MFC.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData

Metoda wywoływana przez platformę, by powiadomić gniazda odbierania, zawierającej wysyłania gniazda w out-of-band dane do wysłania.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnOutOfBandData` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

### <a name="remarks"></a>Uwagi

Out-of-band dane są logicznie niezależny od kanału, który jest skojarzony z każdej pary połączonych sockets typu SOCK_STREAM. Kanał jest zazwyczaj używane do wysyłania pilnych danych.

Biblioteka MFC obsługuje dane poza pasmem, ale użytkownicy klasy `CAsyncSocket` są odradzane korzystanie z niego. Jest łatwiejszy sposób utworzyć drugi gniazda przekazywania tych danych. Aby uzyskać więcej informacji na temat danych out-of-band zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onreceive"></a>  CAsyncSocket::OnReceive

Wywoływane przez platformę, by powiadomić tego gniazda, jest danych buforu, który może być pobierany przez wywołanie `Receive` funkcja elementu członkowskiego.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnReceive` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>  CAsyncSocket::OnSend

Wywoływane przez platformę, by powiadomić gniazdo, teraz przesyłania danych przez wywołanie metody `Send` funkcja elementu członkowskiego.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parametry

*nErrorCode*<br/>
Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnSend` funkcja elementu członkowskiego:

- **0** funkcja została wykonana pomyślnie.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Gniazda powiadomienia](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>  CAsyncSocket::operator =

Przypisuje nową wartość do `CAsyncSocket` obiektu.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parametry

*rSrc*<br/>
Odwołanie do istniejącego `CAsyncSocket` obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby skopiować istniejący `CAsyncSocket` obiektu do drugiego `CAsyncSocket` obiektu.

##  <a name="operator_socket"></a>  CAsyncSocket::operator GNIAZDA

Użyj tego operatora, aby pobrać uchwyt GNIAZDA `CAsyncSocket` obiektu.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt obiektu GNIAZDA. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Dojście służy do wywoływania interfejsów API Windows bezpośrednio.

##  <a name="receive"></a>  CAsyncSocket::Receive

Wywołaj tę funkcję elementu członkowskiego na odbieranie danych z gniazda.

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
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie zostanie usunięty z kolejki wejściowej.

- MSG_OOB przetwarzania danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `Receive` zwraca liczbę bajtów odebranych. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAENOTCONN gniazda nie jest połączony.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `Receive` na gniazdo po `ShutDown` zostało wywołane z *nHow* ustawione na 0 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i `Receive` mogłyby spowodować zablokowanie operacji.

- WSAEMSGSIZE datagram był zbyt duży, aby mieściły się w określonym buforu i zostały obcięte.

- Gniazda nie została powiązana z WSAEINVAL `Bind`.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do strumienia połączonych lub do przesyłania datagramów i służy do odczytywania danych przychodzących.

Gniazda typu SOCK_STREAM zwracany jest jak najwięcej informacji jest obecnie dostępny w rozmiarze dostarczonego buforu. Jeśli dane poza pasmem są nieprzeczytane gniazda został skonfigurowany do odbioru w tekście, out-of-band danych (opcja gniazda SO_OOBINLINE), tylko poza pasmem dane zostaną zwrócone. Aplikacja może używać `IOCtlSIOCATMARK` opcji lub [OnOutOfBandData](#onoutofbanddata) do określenia, czy wszystkie dane bardziej out-of-band pozostają do odczytania.

Do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, rozmiarze dostarczonego buforu. Jeśli datagram jest większy niż rozmiar buforu przekazanego, rozmiar buforu jest wypełniany w pierwszej części datagram, nadmiarowe dane zostaną utracone, a `Receive` zwraca WSAEMSGSIZE ustawiona wartość SOCKET_ERROR, podając mu kod błędu. Jeśli gniazdo są dostępne żadne dane przychodzące, wartość SOCKET_ERROR zwracany jest kod błędu równa WSAEWOULDBLOCK. [Zdarzenia OnReceive](#onreceive) funkcji wywołania zwrotnego może służyć do określenia po nadejściu większej ilości danych.

Jeśli typ SOCK_STREAM to gniazdo i strony zdalnej ma zamknięcie połączenia, `Receive` zostanie zakończony i natychmiast 0 bajtów odebranych. Jeśli połączenie zostało zresetowane, `Receive` zakończy się niepowodzeniem z powodu błędu WSAECONNRESET.

`Receive` powinna być wywoływana tylko raz dla każdej godziny [CAsyncSocket::OnReceive](#onreceive) jest wywoływana.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).

##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom

Wywołaj tę funkcję elementu członkowskiego, aby otrzymywać datagram i Zapisz adres źródłowy w [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury lub *rSocketAddress*.

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
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rSocketPort*<br/>
Odwołanie do UINT, która przechowuje portu.

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która przechowuje adres źródła po powrocie.

*lpSockAddrLen*<br/>
Wskaźnik do długości adres źródłowy w *lpSockAddr* w bajtach.

*nFlags*<br/>
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie zostanie usunięty z kolejki wejściowej.

- MSG_OOB przetwarzania danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `ReceiveFrom` zwraca liczbę bajtów odebranych. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie `GetLastError`. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument ten był nieprawidłowy: *lpSockAddr* bufor jest za mały, aby uwzględnić adres elementu równorzędnego.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- Gniazda nie została powiązana z WSAEINVAL `Bind`.

- WSAENOTCONN gniazda nie jest połączona (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `ReceiveFrom` na gniazdo po `ShutDown` zostało wywołane z *nHow* ustawione na 0 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i `ReceiveFrom` mogłyby spowodować zablokowanie operacji.

- WSAEMSGSIZE datagram był zbyt duży, aby mieściły się w określonym buforu i zostały obcięte.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana do odczytu danych przychodzących na gniazdo (prawdopodobnie połączonych) i przechwytywania adres, z którego wysłano dane.

Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::ReceiveFromEx](#receivefromex).

Gniazda typu SOCK_STREAM zwracany jest jak najwięcej informacji jest obecnie dostępny w rozmiarze dostarczonego buforu. Jeśli dane poza pasmem są nieprzeczytane gniazda został skonfigurowany do odbioru w tekście, out-of-band danych (opcja gniazda SO_OOBINLINE), tylko poza pasmem dane zostaną zwrócone. Aplikacja może używać `IOCtlSIOCATMARK` opcji lub `OnOutOfBandData` do określenia, czy wszystkie dane bardziej out-of-band pozostają do odczytania. *LpSockAddr* i *lpSockAddrLen* parametry są ignorowane w przypadku SOCK_STREAM gniazda.

Do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, rozmiarze dostarczonego buforu. Jeśli datagram jest większy niż rozmiar buforu przekazanego, rozmiar buforu jest wypełniany w pierwszej części komunikatu, nadmiarowe dane zostaną utracone, a `ReceiveFrom` zwraca WSAEMSGSIZE ustawiona wartość SOCKET_ERROR, podając mu kod błędu.

Jeśli *lpSockAddr* jest różna od zera i gniazda jest typu SOCK_DGRAM, adres sieciowy gniazda, w których zostały one wysyłane dane są kopiowane do odpowiednich [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury. Wartość wskazywana przez *lpSockAddrLen* jest inicjowany do rozmiaru tej struktury, a jest modyfikowana przy powrocie do wskazania rzeczywisty rozmiar adresu tam przechowywane. Jeśli w gnieździe, są dostępne żadne dane przychodzące `ReceiveFrom` wywołania oczekuje na dane do odbierania, chyba że gniazdo jest nieblokujących. W tym przypadku jest zwracana wartość SOCKET_ERROR, podając mu kod błędu równa WSAEWOULDBLOCK. `OnReceive` Wywołania zwrotnego może służyć do określenia po nadejściu większej ilości danych.

Jeśli typ SOCK_STREAM to gniazdo i strony zdalnej ma zamknięcie połączenia, `ReceiveFrom` zostanie zakończony i natychmiast 0 bajtów odebranych.

##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx

Wywołaj tę funkcję elementu członkowskiego, aby otrzymywać datagram i Zapisz adres źródłowy w [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury lub *rSocketAddress* (obsługuje adresy IPv6).

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
Odwołanie do `CString` obiekt, który odbiera kropkowana numer adresu IP.

*rSocketPort*<br/>
Odwołanie do UINT, która przechowuje portu.

*nFlags*<br/>
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_PEEK wgląd w dane przychodzące. Dane są kopiowane do buforu, ale nie zostanie usunięty z kolejki wejściowej.

- MSG_OOB przetwarzania danych poza pasmem.

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `ReceiveFromEx` zwraca liczbę bajtów odebranych. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie `GetLastError`. Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpSockAddrLen* argument ten był nieprawidłowy: *lpSockAddr* bufor jest za mały, aby uwzględnić adres elementu równorzędnego.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- Gniazda nie została powiązana z WSAEINVAL `Bind`.

- WSAENOTCONN gniazda nie jest połączona (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `ReceiveFromEx` na gniazdo po `ShutDown` zostało wywołane z *nHow* ustawione na 0 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i `ReceiveFromEx` mogłyby spowodować zablokowanie operacji.

- WSAEMSGSIZE datagram był zbyt duży, aby mieściły się w określonym buforu i zostały obcięte.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

Ta funkcja jest używana do odczytu danych przychodzących na gniazdo (prawdopodobnie połączonych) i przechwytywania adres, z którego wysłano dane.

Ta funkcja jest taka sama jak [CAsyncSocket::ReceiveFrom](#receivefrom) z tą różnicą, że ta obsługuje protokół IPv6 rozwiązuje również jako starszych protokołów.

Gniazda typu SOCK_STREAM zwracany jest jak najwięcej informacji jest obecnie dostępny w rozmiarze dostarczonego buforu. Jeśli dane poza pasmem są nieprzeczytane gniazda został skonfigurowany do odbioru w tekście, out-of-band danych (opcja gniazda SO_OOBINLINE), tylko poza pasmem dane zostaną zwrócone. Aplikacja może używać `IOCtlSIOCATMARK` opcji lub `OnOutOfBandData` do określenia, czy wszystkie dane bardziej out-of-band pozostają do odczytania. *LpSockAddr* i *lpSockAddrLen* parametry są ignorowane w przypadku SOCK_STREAM gniazda.

Do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, rozmiarze dostarczonego buforu. Jeśli datagram jest większy niż rozmiar buforu przekazanego, rozmiar buforu jest wypełniany w pierwszej części komunikatu, nadmiarowe dane zostaną utracone, a `ReceiveFromEx` zwraca WSAEMSGSIZE ustawiona wartość SOCKET_ERROR, podając mu kod błędu.

Jeśli *lpSockAddr* jest różna od zera i gniazda jest typu SOCK_DGRAM, adres sieciowy gniazda, w których zostały one wysyłane dane są kopiowane do odpowiednich [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury. Wartość wskazywana przez *lpSockAddrLen* jest inicjowany do rozmiaru tej struktury, a jest modyfikowana przy powrocie do wskazania rzeczywisty rozmiar adresu tam przechowywane. Jeśli w gnieździe, są dostępne żadne dane przychodzące `ReceiveFromEx` wywołania oczekuje na dane do odbierania, chyba że gniazdo jest nieblokujących. W tym przypadku jest zwracana wartość SOCKET_ERROR, podając mu kod błędu równa WSAEWOULDBLOCK. `OnReceive` Wywołania zwrotnego może służyć do określenia po nadejściu większej ilości danych.

Jeśli typ SOCK_STREAM to gniazdo i strony zdalnej ma zamknięcie połączenia, `ReceiveFromEx` zostanie zakończony i natychmiast 0 bajtów odebranych.

##  <a name="send"></a>  CAsyncSocket::Send

Wywołaj tę funkcję elementu członkowskiego do przesyłania danych w połączonych gniazda.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Bufor zawierający dane, które mają być przekazywane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nFlags*<br/>
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_DONTROUTE Określa, że dane nie należy stosować routingu. Windows Sockets dostawcy można wybrać opcję ignorują tę flagę.

- Wyślij MSG_OOB out-of-band dane (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `Send` zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazywanym przez *nBufLen*.) W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAEFAULT *lpBuf* argument nie jest prawidłową częścią przestrzeni adresowej użytkownika.

- Musi zostać zresetowana WSAENETRESET połączenia, ponieważ implementacja Windows Sockets go porzucić.

- Implementacja WSAENOBUFS Windows Sockets raporty zakleszczenie buforu.

- WSAENOTCONN gniazda nie jest połączony.

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `Send` na gniazdo po `ShutDown` zostało wywołane z *nHow* równa 1 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i mogłyby spowodować zablokowanie żądanej operacji.

- Typ SOCK_DGRAM to WSAEMSGSIZE gniazda, a datagram jest większa niż maksymalna obsługiwana przez implementację Windows Sockets.

- Gniazda nie została powiązana z WSAEINVAL `Bind`.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

### <a name="remarks"></a>Uwagi

`Send` używany do zapisywania danych wychodzących na połączonych strumienia lub do przesyłania datagramów. Do przesyłania datagramów, należy uważać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez `iMaxUdpDg` element [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) zwracany przez strukturę `AfxSocketInit`. Jeśli dane są zbyt długo niepodzielne przekazywania podstawowych protokołów, WSAEMSGSIZE zwracany jest błąd za pośrednictwem `GetLastError`, i są przesyłane żadne dane.

Należy zauważyć, że dla datagramu gniazda pomyślne zakończenie `Send` nie wskazuje, że danych zostało pomyślnie dostarczone.

Na `CAsyncSocket` obiektów typu SOCK_STREAM, liczba zapisanych bajtów może zawierać od 1 do żądanej długości, w zależności od dostępności buforu na hostach lokalne i obce.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnSend](#onsend).

##  <a name="sendto"></a>  CAsyncSocket::SendTo

Wywołaj tę funkcję elementu członkowskiego do wysyłania danych do określonego miejsca docelowego.

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
Bufor zawierający dane, które mają być przekazywane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nHostPort*<br/>
Port identyfikowanie aplikacji gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa maszyny, takie jak "pod adresem" lub liczbą kropkowana, takie jak "128.56.22.8".

*nFlags*<br/>
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_DONTROUTE Określa, że dane nie należy stosować routingu. Windows Sockets dostawcy można wybrać opcję ignorują tę flagę.

- Wyślij MSG_OOB out-of-band dane (tylko SOCK_STREAM).

*lpSockAddr*<br/>
Wskaźnik do [SOCKADDR](/windows/desktop/winsock/sockaddr-2) strukturę, która zawiera adres gniazda docelowego.

*nSockAddrLen*<br/>
Długość adresu w *lpSockAddr* w bajtach.

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `SendTo` zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazywanym przez *nBufLen*.) W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAEFAULT *lpBuf* lub *lpSockAddr* parametry nie są częścią przestrzeni adresowej użytkowników lub *lpSockAddr* argument jest za mały (mniejszą niż rozmiar [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury).

- WSAEINVAL nazwa hosta jest nieprawidłowa.

- Musi zostać zresetowana WSAENETRESET połączenia, ponieważ implementacja Windows Sockets go porzucić.

- Implementacja WSAENOBUFS Windows Sockets raporty zakleszczenie buforu.

- WSAENOTCONN gniazda nie jest połączona (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `SendTo` na gniazdo po `ShutDown` zostało wywołane z *nHow* równa 1 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i mogłyby spowodować zablokowanie żądanej operacji.

- Typ SOCK_DGRAM to WSAEMSGSIZE gniazda, a datagram jest większa niż maksymalna obsługiwana przez implementację Windows Sockets.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny z maszyny lokalnej.

- Nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie z tego gniazda.

- Wymagany jest adres docelowy element WSAEDESTADDRREQ.

- WSAENETUNREACH sieci nie można nawiązać połączenia z tego hosta w tej chwili.

### <a name="remarks"></a>Uwagi

`SendTo` jest używana na sockets datagram lub strumienia i używany do zapisywania danych wychodzących dla gniazda. Do przesyłania datagramów, należy uważać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez `iMaxUdpDg` element [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) struktury wypełnione przez [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długo niepodzielne przekazywania podstawowych protokołów, ten błąd jest zwracany WSAEMSGSIZE i są przesyłane żadne dane.

Należy pamiętać, że pomyślne zakończenie `SendTo` nie wskazuje, że danych zostało pomyślnie dostarczone.

`SendTo` jest używana tylko na gniazdo SOCK_DGRAM wysyłać datagram gniazdo szczególne identyfikowane przez *lpSockAddr* parametru.

Aby wysłać emisji (na klawiaturze SOCK_DGRAM tylko), adres w *lpSockAddr* parametr powinien być skonstruowany przy użyciu specjalnych adresu IP INADDR_BROADCAST (zdefiniowane w pliku nagłówkowym Windows Sockets WINSOCK. H) wraz z numeru portu zamierzone. Lub, jeśli *lpszHostAddress* parametr ma wartość NULL, gniazdo jest skonfigurowana dla odpowiedniej do emisji. Nie jest zazwyczaj wskazane dla datagramu emisji przekracza rozmiar, jaką może wystąpić fragmentacji, co oznacza, że część danych datagramów (bez nagłówków) nie może przekraczać 512 bajtów.

Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::SendToEx](#sendtoex).

##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx

Wywołaj tę funkcję elementu członkowskiego do wysyłania danych do określonego miejsca docelowego (uchwytów adresów IPv6).

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
Bufor zawierający dane, które mają być przekazywane.

*nBufLen*<br/>
Długość danych w *lpBuf* w bajtach.

*nHostPort*<br/>
Port identyfikowanie aplikacji gniazda.

*lpszHostAddress*<br/>
Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa maszyny, takie jak "pod adresem" lub liczbą kropkowana, takie jak "128.56.22.8".

*nFlags*<br/>
Określa sposób, w którym jest nawiązywane połączenie. Semantyka tej funkcji są określane przez opcje gniazda i *nFlags* parametru. Drugim jest tworzony przez łączenie dowolne z następujących wartości przy użyciu języka C++ **lub** operator:

- MSG_DONTROUTE Określa, że dane nie należy stosować routingu. Windows Sockets dostawcy można wybrać opcję ignorują tę flagę.

- Wyślij MSG_OOB out-of-band dane (tylko SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

W przypadku braku błędów `SendToEx` zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazywanym przez *nBufLen*.) W przeciwnym razie jest zwracana wartość SOCKET_ERROR i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEACCES żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAEFAULT *lpBuf* lub *lpSockAddr* parametry nie są częścią przestrzeni adresowej użytkowników lub *lpSockAddr* argument jest za mały (mniejszą niż rozmiar [SOCKADDR](/windows/desktop/winsock/sockaddr-2) struktury).

- WSAEINVAL nazwa hosta jest nieprawidłowa.

- Musi zostać zresetowana WSAENETRESET połączenia, ponieważ implementacja Windows Sockets go porzucić.

- Implementacja WSAENOBUFS Windows Sockets raporty zakleszczenie buforu.

- WSAENOTCONN gniazda nie jest połączona (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazda.

- Określono WSAEOPNOTSUPP MSG_OOB, ale gniazda nie jest typu SOCK_STREAM.

- WSAESHUTDOWN gniazda została wyłączona; nie jest możliwe do wywołania `SendToEx` na gniazdo po `ShutDown` zostało wywołane z *nHow* równa 1 lub 2.

- WSAEWOULDBLOCK gniazda jest oznaczony jako nieblokujących i mogłyby spowodować zablokowanie żądanej operacji.

- Typ SOCK_DGRAM to WSAEMSGSIZE gniazda, a datagram jest większa niż maksymalna obsługiwana przez implementację Windows Sockets.

- WSAECONNABORTED obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inna awaria.

- WSAECONNRESET obwodu wirtualnego został zresetowany przez stronę zdalną.

- WSAEADDRNOTAVAIL określony adres nie jest dostępny z maszyny lokalnej.

- Nie można używać adresów WSAEAFNOSUPPORT w określonej rodzinie z tego gniazda.

- Wymagany jest adres docelowy element WSAEDESTADDRREQ.

- WSAENETUNREACH sieci nie można nawiązać połączenia z tego hosta w tej chwili.

### <a name="remarks"></a>Uwagi

Ta metoda jest taka sama jak [CAsyncSocket::SendTo](#sendto) z tą różnicą, że ta obsługuje protokół IPv6 rozwiązuje również jako starszych protokołów.

`SendToEx` jest używana na sockets datagram lub strumienia i używany do zapisywania danych wychodzących dla gniazda. Do przesyłania datagramów, należy uważać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez `iMaxUdpDg` element [WSADATA](/windows/desktop/api/winsock2/ns-winsock2-wsadata) struktury wypełnione przez [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długo niepodzielne przekazywania podstawowych protokołów, ten błąd jest zwracany WSAEMSGSIZE i są przesyłane żadne dane.

Należy pamiętać, że pomyślne zakończenie `SendToEx` nie wskazuje, że danych zostało pomyślnie dostarczone.

`SendToEx` jest używana tylko na gniazdo SOCK_DGRAM wysyłać datagram gniazdo szczególne identyfikowane przez *lpSockAddr* parametru.

Aby wysłać emisji (na klawiaturze SOCK_DGRAM tylko), adres w *lpSockAddr* parametr powinien być skonstruowany przy użyciu specjalnych adresu IP INADDR_BROADCAST (zdefiniowane w pliku nagłówkowym Windows Sockets WINSOCK. H) wraz z numeru portu zamierzone. Lub, jeśli *lpszHostAddress* parametr ma wartość NULL, gniazdo jest skonfigurowana dla odpowiedniej do emisji. Nie jest zazwyczaj wskazane dla datagramu emisji przekracza rozmiar, jaką może wystąpić fragmentacji, co oznacza, że część danych datagramów (bez nagłówków) nie może przekraczać 512 bajtów.

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
Opcja gniazda, dla którego ma być ustawiona wartość.

*lpOptionValue*<br/>
Wskaźnik do buforu, w którym podano wartość żądanej opcji.

*nOptionLen*<br/>
Rozmiar *lpOptionValue* buforu w bajtach.

*nLevel*<br/>
Poziom, na którym jest zdefiniowana opcja; tylko obsługiwane poziomy są SOL_SOCKET i IPPROTO_TCP.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEFAULT *lpOptionValue* nie jest prawidłową częścią przestrzeni adresowej procesu.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAEINVAL *nLevel* nie jest prawidłowy, i informacje przedstawione w *lpOptionValue* jest nieprawidłowy.

- Jeśli ustawiono SO_KEEPALIVE, WSAENETRESET połączenia został przekroczony.

- WSAENOPROTOOPT opcją jest nieznany lub nieobsługiwany. W szczególności SO_BROADCAST nie jest obsługiwana na sockets SOCK_STREAM podczas SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER i SO_OOBINLINE nie są obsługiwane w gniazda typu SOCK_DGRAM typu.

- Połączenie WSAENOTCONN zostało zresetowane, jeśli ustawiono SO_KEEPALIVE.

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

`SetSockOpt` Ustawia bieżącą wartość dla opcji gniazda skojarzone z gniazda dowolnego typu, w dowolnym stanie. Chociaż opcje może istnieć na różnych poziomach protokołu, ta specyfikacja definiuje tylko opcje, które istnieją na poziomie najwyższym "gniazda". Opcje mają wpływ na operacje gniazda, takie jak tego, czy odebrano przyspieszone dane w strumieniu zwykłych danych czy komunikatów rozgłaszanych mogą być wysyłane w gnieździe i tak dalej.

Istnieją dwa typy opcji gniazda: Logiczna opcje, które włączać lub wyłączać funkcją lub zachowaniem i opcje, które wymagają wartość całkowitą lub struktury. Aby włączyć opcję Boolean, *lpOptionValue* wskazuje całkowitą różną od zera. Aby wyłączyć opcję *lpOptionValue* wskazuje na liczbę całkowitą równą zero. *nOptionLen* powinna być taka sama jak `sizeof(BOOL)` opcji Boolean. Inne opcje *lpOptionValue* wskazuje całkowitą lub struktura zawierająca żądaną wartość dla opcji, a *nOptionLen* jest to liczba całkowita lub struktury.

Określa akcję podejmowaną po niewysłanych danych znajduje się w kolejce na gniazdo, SO_LINGER i `Close` funkcja jest wywoływana, aby zamknąć gniazda.

Domyślnie nie można powiązać gniazda (zobacz [powiązać](#bind)) do lokalnego adresu, który jest już używana. Czasami jednak może być pożądane "ponowne użycie" adres w ten sposób. Ponieważ każde połączenie jest unikatowo identyfikowana przez kombinację adresów lokalnych i zdalnych, nie istnieje żaden problem wymaga dwóch gniazdach powiązany z tego samego adresu lokalnego, tak długo, jak różnią się adresów zdalnych.

Informowanie implementację Windows Sockets, `Bind` wywołanie gniazda nie powinien niedozwolone, ponieważ żądany adres jest już używany przez inny gniazda, aplikacji, należy ustawić opcję gniazda SO_REUSEADDR dla gniazda przed wystawieniem `Bind` wywołania. Należy pamiętać, interpretację opcję tylko w momencie `Bind` wywołania: jest konieczne (ale nieszkodliwe) Ustawianie opcji dla gniazda, które nie może być powiązane z istniejącego adresu i ustawiania lub resetowania opcji po `Bind` wywołanie ma nie wpływa na to lub inne gniazda.

Aplikacja może zażądać, że implementacja Windows Sockets korzystanie z pakietów "keep-alive" w przypadku połączeń protokołu Transmission Control Protocol (TCP), włączając opcję gniazda SO_KEEPALIVE. Implementacja Windows Sockets muszą nie obsługują utrzymywania aktywności: Jeśli tak jest, dokładne semantyki są specyficzne dla implementacji, ale powinny być zgodne z sekcji 4.2.3.6 RFC 1122: "Wymagania dla hostów internetowych — warstwami komunikacyjnymi." Jeśli połączenie zostało przerwane w wyniku elementu "utrzymywania aktywności" Kod błędu: WSAENETRESET jest zwracane żadnym wywołaniom w toku w gnieździe, a WSAENOTCONN niepowodzenie kolejnych wywołań.

Opcja TCP_NODELAY wyłącza algorytm Nagle'a. Algorytm Nagle'a jest używana do zmniejszenia liczby małe pakiety wysyłane przez hosta przez buforowanie danych niepotwierdzonych wysyłania, dopóki nie można wysłać pakietu w pełnym rozmiarze. Jednak w niektórych aplikacjach ten algorytm może utrudniać wydajności i TCP_NODELAY można je wyłączyć. Autorzy aplikacji nie należy ustawić TCP_NODELAY, chyba że wpływ spowoduje więc przejrzyste i żądany, ponieważ ustawienie TCP_NODELAY może mieć znaczący wpływ na wydajność sieci. TCP_NODELAY to jedyny obsługiwany opcję gniazda, która korzysta z poziomu IPPROTO_TCP; wszystkie inne opcje Użyj poziomu SOL_SOCKET.

Niektóre implementacje dostaw Windows Sockets danych wyjściowych informacji dotyczących debugowania, jeśli ustawiono opcję SO_DEBUG przez aplikację.

Poniższe opcje są obsługiwane w przypadku `SetSockOpt`. Typ określa typ danych, które zostały rozwiązane przez *lpOptionValue*.

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_BROADCAST|WARTOŚĆ LOGICZNA|Zezwalaj na transmisji komunikatów emisji w gnieździe.|
|SO_DEBUG|WARTOŚĆ LOGICZNA|Rekord, informacje o debugowaniu.|
|SO_DONTLINGER|WARTOŚĆ LOGICZNA|Nie blokuj `Close` oczekiwanie nie wysłane dane do wysłania. Ustawienie tej opcji jest równoznaczne z ustawieniem SO_LINGER z `l_onoff` należy ustawić na zero.|
|SO_DONTROUTE|WARTOŚĆ LOGICZNA|Nie trasy: wysyłanie bezpośrednio do interfejsu.|
|SO_KEEPALIVE|WARTOŚĆ LOGICZNA|Wyślij utrzymywania aktywności.|
|SO_LINGER|`struct LINGER`|Linger `Close` Jeśli niewysłane znajdują się dane.|
|SO_OOBINLINE|WARTOŚĆ LOGICZNA|Odbieranie danych poza pasmem w strumieniu danych normalny.|
|SO_RCVBUF|**int**|Określ rozmiar buforu dla odbiera.|
|SO_REUSEADDR|WARTOŚĆ LOGICZNA|Zezwalaj na gniazdo powiązać adres, który jest już używana. (Zobacz [powiązać](#bind).)|
|SO_SNDBUF|**int**|Określ rozmiar buforu dla wysyła.|
|TCP_NODELAY|WARTOŚĆ LOGICZNA|Wyłącza algorytm Nagle'a łączenie wysyłania.|

Opcje dystrybucji oprogramowania Berkeley (BSD) nie jest obsługiwane dla `SetSockOpt` są:

|Wartość|Typ|Znaczenie|
|-----------|----------|-------------|
|SO_ACCEPTCONN|WARTOŚĆ LOGICZNA|Nasłuchuje gniazda|
|SO_ERROR|**int**|Uzyskiwanie stanu błędu i usuń zaznaczenie.|
|SO_RCVLOWAT|**int**|Odbieranie znaku wodnym niskiego.|
|SO_RCVTIMEO|**int**|Limit czasu odbierania|
|SO_SNDLOWAT|**int**|Wyślij znaku wodnym niskiego.|
|SO_SNDTIMEO|**int**|Limitu czasu wysyłania.|
|SO_TYPE|**int**|Typ gniazda.|
|IP_OPTIONS||Ustaw pole opcje w nagłówku protokołu IP.|

##  <a name="shutdown"></a>  CAsyncSocket::ShutDown

Wywołanie tej funkcji elementu członkowskiego, aby wyłączyć wysyła, otrzymuje, lub obu w gniazda.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parametry

*nHow*<br/>
Flaga opisująca, jakie rodzaje operacji nie są już dozwolone, przy użyciu poniższych wyliczonych wartości:

- **odbiera = 0**

- **Wysyła = 1**

- **zarówno = 2**

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0 i konkretny kod błędu może być pobierany przez wywołanie [GetLastError](#getlasterror). Następujące błędy dotyczą tej funkcji elementu członkowskiego:

- Pomyślne A WSANOTINITIALISED [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed użyciem tego interfejsu API.

- Implementacja WSAENETDOWN Windows Sockets wykrył, że podsystem sieci nie powiodło się.

- WSAEINVAL *nHow* jest nieprawidłowy.

- Blokowanie operacji Windows Sockets WSAEINPROGRESS A jest w toku.

- WSAENOTCONN gniazda nie jest połączona (tylko SOCK_STREAM).

- WSAENOTSOCK deskryptor nie jest gniazda.

### <a name="remarks"></a>Uwagi

`ShutDown` jest używany dla wszystkich typów gniazd wyłączyć odbiór i/lub transmisji. Jeśli *nHow* wynosi 0, kolejne odbiera na gniazdo będzie niedozwolone. To nie ma wpływu na niższych warstwach protokołu.

Dla Transmission Control Protocol (TCP), okno TCP nie ulegną zmianie, a przychodzące dane zostaną zaakceptowane (ale nie potwierdzonego) wyczerpania okna. Dla protokołu UDP (User Datagram), datagramy przychodzące są zaakceptowane i Zakolejkowane. W żadnym wypadku nie zostanie pakiet ICMP błąd wygenerowany. Jeśli *nHow* wynosi 1, wysyła kolejnych są niedozwolone. Dla gniazda TCP FIN będą wysyłane. Ustawienie *nHow* 2 wyłącza zarówno wysyła i odbiera zgodnie z powyższym opisem.

Należy pamiętać, że `ShutDown` jest nie zamykaj gniazda, a zasobów podłączonych do gniazda nie zostanie zwolniona, aż do `Close` jest wywoływana. Aplikacja nie należy polegać na możliwość ponownego użycia gniazda, po jego zamknięciu. W szczególności implementacji Windows Sockets nie jest wymagany do obsługi użytkowania `Connect` na takie gniazda.

### <a name="example"></a>Przykład

  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).

##  <a name="socket"></a>  CASyncSocket::Socket

Przydziela dojścia do gniazda.

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
Maska bitów określający kombinację zdarzeń sieciowych, w których jest zainteresowana aplikacji.

- `FD_READ`: Chcesz otrzymać powiadomienie o gotowości do odczytu.

- `FD_WRITE`: Chcesz otrzymać powiadomienie o gotowości do zapisu.

- `FD_OOB`: Chcesz otrzymać powiadomienie o dostarczeniu danych poza pasmem.

- `FD_ACCEPT`: Chcesz otrzymać powiadomienie o połączeń przychodzących.

- `FD_CONNECT`: Chcesz otrzymać powiadomienie o zakończonych połączeń.

- `FD_CLOSE`: Chcesz otrzymać powiadomienie o zamknięcia gniazda.

*nProtocolType*<br/>
Protokół do użycia z gniazda, które są specyficzne dla rodziny wskazany adres.

*nAddressFormat*<br/>
Adres specyfikacji rodziny.

### <a name="return-value"></a>Wartość zwracana

Zwraca `TRUE` w przypadku powodzenia `FALSE` w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda przydziela dojścia do gniazda. Nie wywołuje [CAsyncSocket::Bind](#bind) powiązać gniazda określony adres, więc należy wywołać `Bind` później, aby powiązać gniazda z określonego adresu. Możesz użyć [CAsyncSocket::SetSockOpt](#setsockopt) można ustawić opcję gniazda, zanim jest powiązany.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
