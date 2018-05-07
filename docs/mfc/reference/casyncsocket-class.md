---
title: Casyncsocket — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5eaefa40be2a6cf1d57326c2135d848fa08dbc87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="casyncsocket-class"></a>Casyncsocket — klasa
Reprezentuje gniazda systemu Windows — punkt końcowy komunikacji sieciowej.  
  
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
|[CAsyncSocket::Attach](#attach)|Dołącza do uchwytu gniazda `CAsyncSocket` obiektu.|  
|[CAsyncSocket::Bind](#bind)|Kojarzy adresu lokalnego z gniazda.|  
|[CAsyncSocket::Close](#close)|Zamyka gniazdo.|  
|[CAsyncSocket::Connect](#connect)|Ustanawia połączenie gniazda elementu równorzędnego.|  
|[CAsyncSocket::Create](#create)|Tworzy gniazda.|  
|[CAsyncSocket::Detach](#detach)|Odłącza uchwytu gniazda z `CAsyncSocket` obiektu.|  
|[CAsyncSocket::FromHandle](#fromhandle)|Zwraca wskaźnik do `CAsyncSocket` obiektu podane dojście gniazda.|  
|[CAsyncSocket::GetLastError](#getlasterror)|Pobiera stan błędu Ostatnia operacja, która nie powiodła się.|  
|[CAsyncSocket::GetPeerName](#getpeername)|Pobiera adres gniazda równorzędnej, do którego jest podłączony gniazda.|  
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Pobiera adres gniazda równorzędnej gniazda jest połączony (dojść adresów IPv6).|  
|[CAsyncSocket::GetSockName](#getsockname)|Pobiera nazwę lokalnego dla gniazda.|  
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Pobiera nazwę lokalnego dla gniazda (dojść adresów IPv6).|  
|[CAsyncSocket::GetSockOpt](#getsockopt)|Pobiera opcję gniazda.|  
|[CAsyncSocket::IOCtl](#ioctl)|Określa tryb gniazda.|  
|[CAsyncSocket::Listen](#listen)|Ustanawia nasłuchuje przychodzących żądań połączenia gniazda.|  
|[CAsyncSocket::Receive](#receive)|Odbiera dane z gniazda.|  
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Odbiera datagram i przechowuje adres źródłowy.|  
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Odbiera datagram i przechowuje adresu źródłowego (dojść adresów IPv6).|  
|[CAsyncSocket::Send](#send)|Wysyła dane do połączenia gniazda.|  
|[CAsyncSocket::SendTo](#sendto)|Wysyła dane do określonego miejsca docelowego.|  
|[CAsyncSocket::SendToEx](#sendtoex)|Wysyła dane do określonego miejsca docelowego (dojść adresów IPv6).|  
|[CAsyncSocket::SetSockOpt](#setsockopt)|Ustawia opcję gniazda.|  
|[CAsyncSocket::ShutDown](#shutdown)|Wyłącza **wysyłania** i/lub **Receive** wywołuje dla gniazda.|  
|[CASyncSocket::Socket](#socket)|Przydziela uchwyt gniazda.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncSocket::OnAccept](#onaccept)|Powiadamia nasłuchiwania gniazda, który może zaakceptować oczekujących żądań połączenia, wywołując **Akceptuj**.|  
|[CAsyncSocket::OnClose](#onclose)|Powiadamia gniazda, który połączony gniazda zostało zamknięte.|  
|[CAsyncSocket::OnConnect](#onconnect)|Powiadamia połączenia gniazda, że próba połączenia została zakończona, czy pomyślnie, lub błędu.|  
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Powiadamia gniazda odbierania, Brak danych poza pasmem w gnieździe zwykle pilnych wiadomości.|  
|[CAsyncSocket::OnReceive](#onreceive)|Powiadamia nasłuchiwania gniazda jest dane mają zostać pobrane przez wywołanie metody **Receive**.|  
|[CAsyncSocket::OnSend](#onsend)|Powiadamia gniazdo, że przesyłania danych przez wywołanie metody **wysyłania**.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncSocket::operator =](#operator_eq)|Przypisuje nową wartość do `CAsyncSocket` obiektu.|  
|[CAsyncSocket::operator GNIAZDA](#operator_socket)|Użyj tego operatora, aby pobrać **GNIAZDA** uchwyt `CAsyncSocket` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAsyncSocket::m_hSocket](#m_hsocket)|Wskazuje **GNIAZDA** dojście dołączony do tego `CAsyncSocket` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `CAsyncSocket` hermetyzuje gniazda funkcje interfejsu API systemu Windows, zapewniając abstrakcję zorientowane obiektowo dla programistów, którzy mają być używane w połączeniu z MFC Windows Sockets.  
  
 Ta klasa opiera się na założeniu, że rozumiesz komunikacji sieciowej. Jesteś odpowiedzialny za obsługę blokuje różnice kolejności bajtów i konwersje między Unicode i znaków wielobajtowych Ustaw ciągi znaków (MBCS). Wygodniejsze interfejs, który zarządza tych problemów, zobacz klasy [CSocket —](../../mfc/reference/csocket-class.md).  
  
 Do używania `CAsyncSocket` obiektów, wywołaj jego konstruktora, następnie wywołaj [Utwórz](#create) funkcja służąca do tworzenia podstawowej uchwyt gniazda (typu `SOCKET`), z wyjątkiem zaakceptowane gniazda. Połączenie gniazda serwera [nasłuchiwania](#listen) funkcji członkowskiej i połączenia gniazda klienta [Connect](#connect) funkcji członkowskiej. Gniazda serwera powinny wywoływać [Akceptuj](#accept) funkcja po otrzymaniu żądania połączenia. Użyj pozostałe `CAsyncSocket` funkcje przeprowadzenie komunikacji między gniazda. Po zakończeniu zniszczyć `CAsyncSocket` obiektu, jeśli został on utworzony na stercie; destruktor automatycznie wywołuje [Zamknij](#close) funkcji. `SOCKET` — Typ danych jest opisana w artykule [Windows Sockets: tła](../../mfc/windows-sockets-background.md).  
  
> [!NOTE]
>  Korzystając z gniazda MFC w dodatkowej wątków w aplikacji statycznie połączone MFC, należy wywołać `AfxSocketInit` w każdym wątku, który używa sockets zainicjować biblioteki gniazd. Domyślnie `AfxSocketInit` jest wywoływany tylko w podstawowym wątku.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu klasy CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) i pokrewne artykuły., jak również [interfejsu API systemu Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAsyncSocket`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsock.h  
  
##  <a name="accept"></a>  CAsyncSocket::Accept  
 Wywołanie tej funkcji Członkowskich do akceptowania połączeń na gnieździe.  
  
```  
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,  
    SOCKADDR* lpSockAddr = NULL,  
    int* lpSockAddrLen = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rConnectedSocket`  
 Odwołanie identyfikowanie nowe gniazdo, który jest dostępny dla połączenia.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która odbiera adres połączenia gniazda, znane w sieci. Formacie `lpSockAddr` argument zależy od rodziny adresów, nawiązane, gdy utworzono gniazda. Jeśli `lpSockAddr` i/lub `lpSockAddrLen` są równe **NULL**, zwracana jest żadnych informacji dotyczących adresu zdalnego zaakceptowane gniazda.  
  
 `lpSockAddrLen`  
 Wskaźnik do długości adresu w `lpSockAddr` w bajtach. `lpSockAddrLen` Jest wynik wartości parametru: początkowo powinien on zawierać ilość miejsca, do których prowadzą `lpSockAddr`; przy powrocie będzie zawierać rzeczywista długość (w bajtach) zwrócony adres.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument jest za mały (mniejszą niż rozmiar [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury).  
  
- **WSAEINPROGRESS** blokowania wywołanie Windows Sockets jest w toku.  
  
- **WSAEINVAL** `Listen` nie jest wywoływane przed zaakceptować.  
  
- **WSAEMFILE** kolejka jest pusta po wejściu do akceptowania i deskryptorów nie są dostępne.  
  
- `WSAENOBUFS` Brak miejsca w buforze jest dostępna.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP** przywoływanego gniazda nie jest typem, który obsługuje usługę nawiązaniem połączenia.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i połączenia nie są obecne mają być akceptowane.  
  
### <a name="remarks"></a>Uwagi  
 Ta procedura wyodrębnia pierwszego połączenia w kolejce oczekujących połączeń, tworzy nowe gniazdo z tymi samymi właściwościami co tego gniazda i dołącza go do `rConnectedSocket`. Jeśli żadne oczekujące połączenia znajdują się w kolejce, **Akceptuj** zwraca zero i `GetLastError` zwraca błąd. Zaakceptowane gniazda ( *rConnectedSocket)* nie można zaakceptować więcej połączeń. Oryginalny gniazda pozostaje otwarty i nasłuchuje.  
  
 Argument `lpSockAddr` jest parametr wynik, który jest wypełniane adres gniazda połączenia, ponieważ znana warstwy komunikacji. **Zaakceptuj** jest używane z typami gniazda opartego na połączeniach, taką jak **SOCK_STREAM**.  
  
##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect  
 Wywołanie tej funkcji Członkowskich żądania powiadamianie o zdarzeniach dla gniazda.  
  
```  
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lEvent`  
 Maski, który określa kombinację zdarzenia sieci, w których jest zainteresowana aplikacji.  
  
- **FD_READ** chcesz otrzymywać powiadomienia o gotowości do odczytu.  
  
- **FD_WRITE** chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.  
  
- **FD_OOB** chcesz otrzymywać powiadomienia o dostarczeniu danych poza pasmem.  
  
- **FD_ACCEPT** chcesz otrzymywać powiadomienia o połączeń przychodzących.  
  
- **FD_CONNECT** chcesz otrzymywać powiadomienia o wyników połączenia.  
  
- **FD_CLOSE** chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEINVAL** wskazuje, że jeden z określonych parametrów jest nieprawidłowy.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do określania, jakie funkcje MFC wywołania zwrotnego powiadomień zostanie wywołana dla gniazda. `AsyncSelect` automatycznie ustawia tryb nieblokujących tego gniazda. Aby uzyskać więcej informacji, zobacz artykuł [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="attach"></a>  CAsyncSocket::Attach  
 Wywołanie tej funkcji Członkowskich, aby dołączyć `hSocket` dojścia do `CAsyncSocket` obiektu.  
  
```  
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Zawiera dojścia do gniazda.  
  
 `lEvent`  
 Maski, który określa kombinację zdarzenia sieci, w których jest zainteresowana aplikacji.  
  
- **FD_READ** chcesz otrzymywać powiadomienia o gotowości do odczytu.  
  
- **FD_WRITE** chcesz otrzymywać powiadomienia, gdy dane są dostępne do odczytu.  
  
- **FD_OOB** chcesz otrzymywać powiadomienia o dostarczeniu danych poza pasmem.  
  
- **FD_ACCEPT** chcesz otrzymywać powiadomienia o połączeń przychodzących.  
  
- **FD_CONNECT** chcesz otrzymywać powiadomienia o wyników połączenia.  
  
- **FD_CLOSE** chcesz otrzymywać powiadomienia, gdy gniazdo zostało zamknięte przez element równorzędny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie.  
  
### <a name="remarks"></a>Uwagi  
 **GNIAZDA** dojścia jest przechowywany w obiekcie [m_hSocket](#m_hsocket) element członkowski danych.  
  
##  <a name="bind"></a>  CAsyncSocket::Bind  
 Wywołanie tej funkcji Członkowskich do skojarzenia z gniazda adresu lokalnego.  
  
```  
BOOL Bind(
    UINT nSocketPort,  
    LPCTSTR lpszSocketAddress = NULL);

 
BOOL Bind (
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Port identyfikowanie aplikacji gniazda.  
  
 `lpszSocketAddress`  
 Adres sieciowy jest liczbą kropkami, takie jak "128.56.22.8". Przekazywanie **NULL** ciągu dla tego parametru oznacza **CAsyncSocket** wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która zawiera adres do przypisania do tego gniazda.  
  
 `nSockAddrLen`  
 Długość adresu w `lpSockAddr` w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEADDRINUSE** określony adres jest już używana. (Zobacz **SO_REUSEADDR** gniazda opcję w obszarze [SetSockOpt](#setsockopt).)  
  
- **WSAEFAULT** `nSockAddrLen` argument jest za mały (mniejszą niż rozmiar [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury).  
  
- **WSAEINPROGRESS** blokowania wywołanie Windows Sockets jest w toku.  
  
- **WSAEAFNOSUPPORT** rodziny określony adres nie jest obsługiwany przez ten port.  
  
- **WSAEINVAL** gniazda jest już powiązany adres.  
  
- `WSAENOBUFS` Za mało buforów, zbyt wiele połączeń.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 Ta procedura jest używana na datagram odłączony lub gniazda strumienia przed kolejnych **Connect** lub `Listen` wywołania. Zanim będzie mógł akceptować żądania połączenia, nasłuchiwania gniazda serwera należy wybrać numer portu i poinformuj Windows Sockets przez wywołanie metody **powiązać**. **Powiąż** ustanawia skojarzenie lokalne (liczba adres i port hosta) gniazda przez przypisanie nazwę lokalnego gniazda bez nazwy.  
  
##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket  
 Tworzy obiekt do pustego gniazda.  
  
```  
CAsyncSocket();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, należy wywołać jej **Utwórz** funkcji członkowskiej, aby utworzyć **GNIAZDA** danych struktury i powiąż jego adres. (Po stronie serwera komunikacji usługi Windows Sockets, gdy nasłuchiwania gniazda tworzy gniazda do użycia w **Akceptuj** wywołanie, nie zostanie wywołana **Utwórz** dla tego gniazda.)  
  
##  <a name="close"></a>  CAsyncSocket::Close  
 Zamyka gniazdo.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zwalnia deskryptora gniazda, aby dalsze odwołania do niego zakończy się niepowodzeniem z powodu błędu **WSAENOTSOCK**. Jeśli to jest ostatnie odwołanie do podstawowej gniazda, skojarzone nazewnictwa informacje i dane w kolejce zostaną odrzucone. Obiekt gniazda wywołania destruktora **Zamknij** dla Ciebie.  
  
 Dla `CAsyncSocket`, ale nie dla `CSocket`, semantykę **Zamknij** dotyczy opcji gniazda **SO_LINGER** i **SO_DONTLINGER**. Aby uzyskać więcej informacji, zobacz funkcji członkowskiej `GetSockOpt`.  
  
##  <a name="connect"></a>  CAsyncSocket::Connect  
 Wywołanie tej funkcji Członkowskich nawiązać połączenie z strumienia odłączony lub gniazda do przesyłania datagramów.  
  
```  
BOOL Connect(
    LPCTSTR lpszHostAddress,  
    UINT nHostPort);

 
BOOL Connect(
    const SOCKADDR* lpSockAddr,  
    int nSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHostAddress`  
 Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa komputera, takich jak "pod adresem" lub liczbą kropkami, takie jak "128.56.22.8".  
  
 `nHostPort`  
 Port identyfikowanie aplikacji gniazda.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która zawiera adres połączenia gniazda.  
  
 `nSockAddrLen`  
 Długość adresu w `lpSockAddr` w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Jeśli oznacza to kod błędu **WSAEWOULDBLOCK**, a aplikacja korzysta z możliwym do zastąpienia wywołań zwrotnych, aplikacja będzie odbierać `OnConnect` komunikatu po zakończeniu operacji nawiązywania połączenia. Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEADDRINUSE** określony adres jest już używana.  
  
- **WSAEINPROGRESS** blokowania wywołanie Windows Sockets jest w toku.  
  
- **WSAEADDRNOTAVAIL** określony adres nie jest dostępny z komputera lokalnego.  
  
- **WSAEAFNOSUPPORT** adresów w określonej rodzinie nie można używać z tego gniazda.  
  
- **WSAECONNREFUSED** próby nawiązania połączenia zostało odrzucone.  
  
- **WSAEDESTADDRREQ** wymagany jest adres docelowy.  
  
- **WSAEFAULT** `nSockAddrLen` argument jest nieprawidłowy.  
  
- **WSAEINVAL** hosta nieprawidłowy adres.  
  
- **WSAEISCONN** gniazda jest już połączony.  
  
- **WSAEMFILE** nie więcej deskryptorów plików są dostępne.  
  
- **WSAENETUNREACH** sieci jest nieosiągalny z tego hosta w tym momencie.  
  
- `WSAENOBUFS` Brak miejsca w buforze jest dostępna. Nie można połączyć gniazda.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAETIMEDOUT** próba połączenia przekroczyła limit czasu bez ustanawiania połączenia.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i nie można wykonać połączenia natychmiast.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli gniazda jest niezwiązany, unikatowe wartości są przypisane do lokalnych skojarzenia przez system i gniazda jest oznaczony jako powiązana. Należy pamiętać, że jeśli pole adresu struktury nazwy jest samych zer, **Connect** , którą będzie zwracać zera. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError` funkcję elementu członkowskiego.  
  
 Dla gniazda strumieni (typ **SOCK_STREAM**), zainicjowaniu aktywnego połączenia z hostem obcego. Po pomyślnym zakończeniu wywołania gniazda gniazda jest gotowy do wysyłania i odbierania danych.  
  
 Dla gniazda datagramów (typ **SOCK_DGRAM**), ustawiono domyślnej lokalizacji docelowej, które będą używane w kolejnych **wysyłania** i **Receive** wywołania.  
  
##  <a name="create"></a>  CAsyncSocket::Create  
 Wywołanie **Utwórz** funkcji członkowskiej po konstruowania obiektu gniazda, aby utworzyć gniazda systemu Windows i dołączyć go.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Dobrze znanego portu do użycia z gniazda lub 0, jeśli chcesz Windows Sockets, aby wybrać port.  
  
 `nSocketType`  
 **SOCK_STREAM** lub **SOCK_DGRAM**.  
  
 `lEvent`  
 Maski, który określa kombinację zdarzenia sieci, w których jest zainteresowana aplikacji.  
  
- **FD_READ** chcesz otrzymywać powiadomienia o gotowości do odczytu.  
  
- **FD_WRITE** chcesz otrzymywać powiadomienia o gotowości do zapisu.  
  
- **FD_OOB** chcesz otrzymywać powiadomienia o dostarczeniu danych poza pasmem.  
  
- **FD_ACCEPT** chcesz otrzymywać powiadomienia o połączeń przychodzących.  
  
- **FD_CONNECT** chcesz otrzymywać powiadomienia o ukończone połączenia.  
  
- **FD_CLOSE** chcesz otrzymywać powiadomienia o zamknięcia gniazda.  
  
 *lpszSockAddress*  
 Wskaźnik do ciąg zawierający adres sieciowy połączone gniazdo, liczbę kropkami, na przykład "128.56.22.8". Przekazywanie **NULL** ciągu dla tego parametru oznacza **CAsyncSocket** wystąpienia powinna nasłuchiwać aktywność klienta na wszystkich interfejsach sieciowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEAFNOSUPPORT** rodziny określony adres nie jest obsługiwane.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEMFILE** nie więcej deskryptorów plików są dostępne.  
  
- `WSAENOBUFS` Brak miejsca w buforze jest dostępna. Nie można utworzyć gniazda.  
  
- **WSAEPROTONOSUPPORT** określony port nie jest obsługiwane.  
  
- **WSAEPROTOTYPE** określony port jest niewłaściwego typu dla tego gniazda.  
  
- **WSAESOCKTNOSUPPORT** podanego typu gniazda nie jest obsługiwana w tej rodzinie adresów.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** wywołania [gniazda](#socket) i w razie powodzenia wywołuje [powiązać](#bind) można powiązać gniazda do określonego adresu. Obsługiwane są następujące typy gniazda:  
  
- **SOCK_STREAM** zapewnia sekwencjonowania, strumienie bajtów niezawodne, pełny dupleks, opartego na połączeniach. Używa Transmission Control Protocol (TCP) dla systemów z rodziny adresu internetowego.  
  
- **SOCK_DGRAM** obsługuje datagramy są pakiety bez połączenia, zawodne stała długość maksymalną (zazwyczaj jest to mała). Używa protokołu UDP (User Datagram) dla systemów z rodziny adresu internetowego.  
  
    > [!NOTE]
    >  **Akceptuj** funkcji członkowskiej przyjmuje odwołanie do nowy, pusty `CSocket` obiektu jako jego parametr. Należy utworzyć ten obiekt przed wywołaniem **Akceptuj**. Należy pamiętać, że jeśli ten obiekt gniazda trafia zakresu, zamyka połączenie. Nie wywołuj **Utwórz** dla tego nowego obiektu gniazda.  
  
> [!IMPORTANT]
> **Utwórz** jest **nie** wątkowo.  Wywołujesz go w środowisku wielowątkowych go może zostać przywołane jednocześnie przez inne wątki, należy chronić każdego wywołania elementu mutex lub innych lock synchronizacji.  
  
 Aby uzyskać więcej informacji na temat gniazd strumienia i datagram, zobacz artykuły [Windows Sockets: tła](../../mfc/windows-sockets-background.md) i [Windows Sockets: porty i adresy gniazd](../../mfc/windows-sockets-ports-and-socket-addresses.md) i [interfejsu API systemu Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="detach"></a>  CAsyncSocket::Detach  
 Wywołanie tej funkcji członkowskich można odłączyć **GNIAZDA** obsługi w `m_hSocket` element członkowski danych z `CAsyncSocket` obiektu i ustawić `m_hSocket` do **NULL**.  
  
```  
SOCKET Detach();
```  
  
##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle  
 Zwraca wskaźnik do `CAsyncSocket` obiektu.  
  
```  
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Zawiera dojścia do gniazda.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CAsyncSocket` obiekt, lub **NULL** w przypadku nie `CAsyncSocket` obiekt dołączony do `hSocket`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy **GNIAZDA** obsługi, jeśli `CAsyncSocket` obiekt nie jest dołączony do uchwytu, zwraca funkcja członkowska **NULL**.  
  
##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError  
 Wywołanie tej funkcji członkowskich można uzyskać stanu błędu Ostatnia operacja, która nie powiodła się.  
  
```  
static int PASCAL GetLastError();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości zwracanej wskazuje kod błędu dla ostatniej procedury interfejsu API systemu Windows Sockets wykonywane przez tego wątku.  
  
### <a name="remarks"></a>Uwagi  
 Gdy funkcja określonym elementem członkowskim wskazuje, że wystąpił błąd, `GetLastError` powinna być wywoływana pobrać odpowiednią błąd kodu. Zobacz opis funkcji poszczególnych elementów członkowskich listę kodów błędów dotyczy.  
  
 Aby uzyskać więcej informacji o kodach błędów, zobacz [interfejsu API systemu Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName  
 Wywołanie tej funkcji elementu członkowskiego, aby uzyskać adres gniazda równorzędnej, do którego jest podłączony tego gniazda.  
  
```  
BOOL GetPeerName(
    CString& rPeerAddress,  
    UINT& rPeerPort);

 
BOOL GetPeerName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `rPeerAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rPeerPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która uzyskuje nazwę gniazda elementu równorzędnego.  
  
 `lpSockAddrLen`  
 Wskaźnik do długości adresu w `lpSockAddr` w bajtach. Przy powrocie `lpSockAddrLen` argument zawiera rzeczywisty rozmiar `lpSockAddr` zwracany w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument nie jest wystarczająco duży.  
  
- **WSAEINPROGRESS** blokowania wywołanie Windows Sockets jest w toku.  
  
- **WSAENOTCONN** gniazda nie jest połączona.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::GetPeerNameEx](#getpeernameex).  
  
##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx  
 Wywołanie tej funkcji elementu członkowskiego, aby uzyskać adres gniazda równorzędnej tego gniazda jest połączony (dojść adresów IPv6).  
  
```  
BOOL GetPeerNameEx(
    CString& rPeerAddress,  
    UINT& rPeerPort);
```  
  
### <a name="parameters"></a>Parametry  
 `rPeerAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rPeerPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument nie jest wystarczająco duży.  
  
- **WSAEINPROGRESS** blokowania wywołanie Windows Sockets jest w toku.  
  
- **WSAENOTCONN** gniazda nie jest połączona.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [CAsyncSocket::GetPeerName](#getpeername) z tą różnicą, że obsługuje ona IPv6 dotyczy również jako starszych protokołów.  
  
##  <a name="getsockname"></a>  CAsyncSocket::GetSockName  
 Wywołanie tej funkcji Członkowskich uzyskać nazwy lokalnego dla gniazda.  
  
```  
BOOL GetSockName(
    CString& rSocketAddress,  
    UINT& rSocketPort);

 
BOOL GetSockName(
    SOCKADDR* lpSockAddr,  
    int* lpSockAddrLen);
```  
  
### <a name="parameters"></a>Parametry  
 `rSocketAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rSocketPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury, która odbiera adres gniazda.  
  
 `lpSockAddrLen`  
 Wskaźnik do długości adresu w `lpSockAddr` w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument nie jest wystarczająco duży.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEINVAL** gniazda nie został powiązany w adresie **powiązać**.  
  
### <a name="remarks"></a>Uwagi  
 To wywołanie jest szczególnie przydatne, gdy **Connect** nawiązano połączenie bez to **powiązać** najpierw; to wywołanie zawiera jedynym sposobem, w którym można określić skojarzenie lokalne, która została ustawiona przez System.  
  
 Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::GetSockNameEx](#getsocknameex)  
  
##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx  
 Wywołanie tej funkcji Członkowskich uzyskać nazwy lokalnego dla gniazda (dojść adresów IPv6).  
  
```  
BOOL GetSockNameEx(
    CString& rSocketAddress,  
    UINT& rSocketPort);
```  
  
### <a name="parameters"></a>Parametry  
 `rSocketAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rSocketPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument nie jest wystarczająco duży.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEINVAL** gniazda nie został powiązany w adresie **powiązać**.  
  
### <a name="remarks"></a>Uwagi  
 To wywołanie jest taka sama jak [CAsyncSocket::GetSockName](#getsockname) z tą różnicą, że obsługuje ona IPv6 dotyczy również jako starszych protokołów.  
  
 To wywołanie jest szczególnie przydatne, gdy **Connect** nawiązano połączenie bez to **powiązać** najpierw; to wywołanie zawiera jedynym sposobem, w którym można określić skojarzenie lokalne, która została ustawiona przez System.  
  
##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt  
 Wywołanie tej funkcji członkowskich można pobrać opcji gniazda.  
  
```  
BOOL GetSockOpt(
    int nOptionName,  
    void* lpOptionValue,  
    int* lpOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptionName`  
 Opcja gniazda, dla którego ma być pobrana wartość.  
  
 `lpOptionValue`  
 Wskaźnik do buforu, w której jest zwracana wartość żądana opcji. Wartość skojarzoną z wybraną opcję jest zwracany w buforze `lpOptionValue`. Liczba całkowita wskazywana przez `lpOptionLen` pierwotnie musi zawierać rozmiaru buforu w bajtach; i na powrót, zostanie ustawiony rozmiar wartości zwracanej. Dla **SO_LINGER**, będzie to rozmiar `LINGER` struktury; dla wszystkich innych opcji będą rozmiar **BOOL** lub `int`, w zależności od opcji. Zobacz listę opcji i ich rozmiary w sekcji uwag.  
  
 `lpOptionLen`  
 Wskaźnik do rozmiaru `lpOptionValue` buforu w bajtach.  
  
 `nLevel`  
 Poziom, w którym zdefiniowano opcję; są tylko obsługiwane poziomy **SOL_SOCKET** i **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Jeśli nigdy nie ustawiono opcję z `SetSockOpt`, następnie `GetSockOpt` zwraca wartość domyślną opcji. Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpOptionLen` argument był nieprawidłowy.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOPROTOOPT** opcją jest nieznany lub nieobsługiwany. W szczególności **SO_BROADCAST** nie jest obsługiwana w sockets typu **SOCK_STREAM**, podczas gdy **SO_ACCEPTCONN**, **SO_DONTLINGER**,  **SO_KEEPALIVE**, **SO_LINGER**, i **SO_OOBINLINE** nie są obsługiwane w sockets typu **SOCK_DGRAM**.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 `GetSockOpt` pobiera bieżącą wartość opcji gniazda skojarzone z gniazdem dowolnego typu, w dowolnym stanie i zapisuje wynik w `lpOptionValue`. Opcje wpływających na funkcjonowanie gniazda, takich jak routing pakietów, przeniesienia danych poza pasmem i tak dalej.  
  
 Poniższe opcje są obsługiwane w przypadku `GetSockOpt`. Typ określa typ danych dotyczy `lpOptionValue`. **TCP_NODELAY** opcja używa poziomu **IPPROTO_TCP**; Użyj innych opcji poziomu **SOL_SOCKET**.  
  
|Wartość|Typ|Znaczenie|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Nasłuchuje gniazda.|  
|**SO_BROADCAST**|**BOOL**|Gniazda jest skonfigurowany do przekazywania komunikatów rozgłaszanych.|  
|**SO_DEBUG**|**BOOL**|Debugowanie jest włączone.|  
|**SO_DONTLINGER**|**BOOL**|Jeśli PRAWDA, **SO_LINGER** opcja jest wyłączona.|  
|**SO_DONTROUTE**|**BOOL**|Routing jest wyłączony.|  
|**SO_ERROR**|`int`|Pobierz stan błędu i wyczyść.|  
|**SO_KEEPALIVE**|**BOOL**|Utrzymywania aktywności są przesyłane.|  
|**SO_LINGER**|**Struktura LINGER**|Zwraca bieżące opcje linger.|  
|**SO_OOBINLINE**|**BOOL**|Dane poza pasmem są odbierane w strumieniu danych normalnego.|  
|**SO_RCVBUF**|`int`|Rozmiar buforu dla odbiera.|  
|**SO_REUSEADDR**|**BOOL**|Gniazda może być powiązana z adresu, który jest już używana.|  
|**SO_SNDBUF**|`int`|Rozmiar buforu dla wysyła.|  
|**SO_TYPE**|`int`|Typ gniazda (na przykład **SOCK_STREAM**).|  
|**TCP_NODELAY**|**BOOL**|Wyłącza algorytm Nagle'a łączenie wysyłania.|  
  
 Opcje dystrybucji oprogramowania Berkeley (BSD) nie jest obsługiwane dla `GetSockOpt` są:  
  
|Wartość|Typ|Znaczenie|  
|-----------|----------|-------------|  
|**SO_RCVLOWAT**|`int`|Odbieranie znaku wodnym niskiego poziomu.|  
|**SO_RCVTIMEO**|`int`|Odbieranie limitu czasu.|  
|**SO_SNDLOWAT**|`int`|Wyślij znaku wodnym niskiego poziomu.|  
|**SO_SNDTIMEO**|`int`|Limitu czasu wysyłania.|  
|**IP_OPTIONS**||Pobierz opcje w nagłówku protokołu IP.|  
|**TCP_MAXSEG**|`int`|Pobierz TCP maksymalny rozmiar segmentu.|  
  
 Wywoływanie `GetSockOpt` z nieobsługiwaną opcję spowoduje z kodem błędu **WSAENOPROTOOPT** zostały zwrócone z `GetLastError`.  
  
##  <a name="ioctl"></a>  CAsyncSocket::IOCtl  
 Wywołanie tej funkcji Członkowskich do sterowania trybem gniazda.  
  
```  
BOOL IOCtl(
    long lCommand,  
    DWORD* lpArgument);
```  
  
### <a name="parameters"></a>Parametry  
 `lCommand`  
 Polecenie do wykonania w gnieździe.  
  
 `lpArgument`  
 Wskaźnik do parametru `lCommand`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEINVAL** `lCommand` nie jest prawidłowe polecenie lub `lpArgument` nie jest dopuszczalne parametrem `lCommand`, lub polecenie nie ma zastosowania do typu gniazda dostarczony.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 Tej procedury można w dowolnym gnieździe w dowolnym stanie. Służy do pobierania lub pobrać parametry operacyjne skojarzone z gniazda, niezależnie od podsystemu protokołu i łączności. Obsługiwane są następujące polecenia:  
  
- **FIONBIO** Włącz lub wyłącz tryb nieblokujących w gnieździe. `lpArgument` Parametr wskazuje na `DWORD`, która jest różna od zera, jeśli tryb nieblokujących ma zostać włączona i zero, jeśli jest wyłączona. Jeśli `AsyncSelect` został wystawiony dla gniazda, a następnie próby użycia **IOCtl** ustawić gniazda tryb blokowania zakończy się niepowodzeniem z **WSAEINVAL**. Aby ustawić gniazda tryb blokowania i zapobiec **WSAEINVAL** błędu aplikacji należy najpierw wyłączyć `AsyncSelect` przez wywołanie metody `AsyncSelect` z `lEvent` parametru równa 0, następnie wywołaj **IOCtl** .  
  
- **FIONREAD** określić maksymalną liczbę bajtów, które mogą być odczytywane z jednym **Receive** wywoływać z tego gniazda. `lpArgument` Parametr wskazuje na `DWORD` w którym **IOCtl** zapisuje wynik. W przypadku tego gniazda typu **SOCK_STREAM**, **FIONREAD** zwraca łączną ilość danych, które mogą być odczytywane w jednej **Receive**; zwykle jest to suma dane w kolejce na gniazda. W przypadku tego gniazda typu **SOCK_DGRAM**, **FIONREAD** zwraca rozmiar datagramu pierwszy umieszczonych w kolejce na gniazda.  
  
- **SIOCATMARK** ustalić, czy wszystkie dane poza pasmem została przeczytana. Dotyczy to tylko gniazda typu **SOCK_STREAM** został skonfigurowany do odbioru w wierszu danych poza pasmem ( **SO_OOBINLINE**). Jeśli żadne dane poza pasmem oczekuje na odczytywanie, operacja zwraca różną od zera. W przeciwnym razie zwraca wartość 0, a następne **Receive** lub `ReceiveFrom` wykonywane na gniazda pobierze niektórych lub wszystkich danych poprzedzających "znakiem"; należy użyć aplikacji **SIOCATMARK** operacji Ustal, czy pozostaje żadnych danych. W przypadku normalnych danych poprzedzających "pilnych" danych (poza pasmem), będą odbierane w kolejności. (Należy pamiętać, że **Receive** lub `ReceiveFrom` nigdy nie będzie mieszać poza pasmem i normalne danych w tym samym wywołaniu.) `lpArgument` Parametr wskazuje na `DWORD` w którym **IOCtl** zapisuje wynik.  
  
 Ta funkcja jest podzbiorem **ioctl()** w Berkeley gniazda. W szczególności, nie ma żadnego polecenia, który jest odpowiednikiem **FIOASYNC**, podczas gdy **SIOCATMARK** polecenia wyłącznie gniazdo na poziomie, który jest obsługiwany.  
  
##  <a name="listen"></a>  CAsyncSocket::Listen  
 Wywołanie tej funkcji Członkowskich do nasłuchiwania przychodzących żądań połączenia.  
  
```  
BOOL Listen(int nConnectionBacklog = 5);
```  
  
### <a name="parameters"></a>Parametry  
 *nConnectionBacklog*  
 Maksymalna długość, do której może zwiększyć kolejka oczekujących połączeń. Prawidłowy zakres to od 1 do 5.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEADDRINUSE** została podjęta próba nasłuchiwania adresu w użyciu.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEINVAL** gniazda nie został powiązany z **powiązać** lub jest już połączony.  
  
- **WSAEISCONN** gniazda jest już połączony.  
  
- **WSAEMFILE** nie więcej deskryptorów plików są dostępne.  
  
- `WSAENOBUFS` Brak miejsca w buforze jest dostępna.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP** przywoływanego gniazda nie jest typu, który obsługuje `Listen` operacji.  
  
### <a name="remarks"></a>Uwagi  
 Do akceptowania połączeń, gniazda utworzenia z **Utwórz**, zaległości dla połączeń przychodzących jest określany za pomocą `Listen`, i następnie połączenia są akceptowane z **Akceptuj**. `Listen` ma zastosowanie tylko do gniazd, które obsługują połączenia, to znaczy typu **SOCK_STREAM**. Tego gniazda są umieszczane w trybie "pasywnym" gdzie połączenia przychodzące są potwierdzone i przez proces w kolejce oczekujących akceptacji.  
  
 Ta funkcja zwykle jest używana przez serwery (lub dowolnej aplikacji, która potrzebuje do akceptowania połączeń) który może mieć więcej niż jedno żądanie połączenia naraz: Jeśli żądanie połączenia z pełną kolejką, klient zostanie zwrócony błąd ze wskazaniem  **WSAECONNREFUSED**.  
  
 `Listen` próby nadal działają racjonalne, gdy brak dostępnych portów (deskryptory). Dopóki kolejki jest opróżniany akceptował połączenia. Jeśli porty staną się dostępne, nowsze wywołanie `Listen` lub **Akceptuj** uzupełnienie kolejki do bieżącego lub ostatniego "zaległości,", jeśli to możliwe i wznowienia nasłuchiwania przychodzących połączeń.  
  
##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket  
 Zawiera **GNIAZDA** obsługi dla gniazda hermetyzowany to `CAsyncSocket` obiektu.  
  
```  
SOCKET m_hSocket;  
```  
  
##  <a name="onaccept"></a>  CAsyncSocket::OnAccept  
 Wywoływane przez platformę, by powiadomić gniazdo nasłuchiwania, który może zaakceptować oczekujących żądań połączenia, wywołując [Akceptuj](#accept) funkcję elementu członkowskiego.  
  
```  
virtual void OnAccept(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczy `OnAccept` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onclose"></a>  CAsyncSocket::OnClose  
 Wywoływane przez platformę, by powiadomić tego gniazda, że zamknięto połączone gniazdo w procesie.  
  
```  
virtual void OnClose(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnClose` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAECONNRESET** połączenie zostało zresetowane przez strony zdalnej.  
  
- **WSAECONNABORTED** połączenie zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onconnect"></a>  CAsyncSocket::OnConnect  
 Wywoływane przez platformę, by powiadomić tego połączenia gniazda, że jego zakończyła się próba połączenia, czy pomyślnie z błędami.  
  
```  
virtual void OnConnect(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnConnect` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAEADDRINUSE** określony adres jest już używana.  
  
- **WSAEADDRNOTAVAIL** określony adres nie jest dostępny z komputera lokalnego.  
  
- **WSAEAFNOSUPPORT** adresów w określonej rodzinie nie można używać z tego gniazda.  
  
- **WSAECONNREFUSED** wymuszone odrzucono próby nawiązania połączenia.  
  
- **WSAEDESTADDRREQ** wymagany jest adres docelowy.  
  
- **WSAEFAULT** `lpSockAddrLen` argument jest nieprawidłowy.  
  
- **WSAEINVAL** gniazda jest już powiązany adres.  
  
- **WSAEISCONN** gniazda jest już połączony.  
  
- **WSAEMFILE** nie więcej deskryptorów plików są dostępne.  
  
- **WSAENETUNREACH** sieci jest nieosiągalny z tego hosta w tym momencie.  
  
- `WSAENOBUFS` Brak miejsca w buforze jest dostępna. Nie można połączyć gniazda.  
  
- **WSAENOTCONN** gniazda nie jest połączona.  
  
- **WSAENOTSOCK** deskryptora jest plikiem, nie gniazda.  
  
- **WSAETIMEDOUT** próby nawiązania połączenia upłynął limit czasu bez ustanawiania połączenia.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W [CSocket —](../../mfc/reference/csocket-class.md), `OnConnect` nigdy nie została wywołana funkcja powiadomień. Dla połączeń, należy po prostu wywołać **Connect**, który zwróci po zakończeniu połączenia (pomyślnie lub błąd). Sposób obsługi powiadomień połączenia jest szczegółów implementacji MFC.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]  
  
##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData  
 Wywoływane przez platformę, by powiadomić gniazda odbierania, które wysyłania gniazda ma do wysłania dane poza pasmem.  
  
```  
virtual void OnOutOfBandData(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnOutOfBandData` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Dane poza pasmem są logicznie niezależny kanału, który jest skojarzony z każdej pary połączenia gniazda typu **SOCK_STREAM**. Kanał jest zazwyczaj używany do wysyłania pilnych danych.  
  
 MFC obsługuje dane poza pasmem, ale użytkownicy klasy `CAsyncSocket` są niezalecane korzystanie z niego. Jest prostszy sposób utworzyć drugi gniazda przekazywania tych danych. Aby uzyskać więcej informacji na temat danych poza pasmem, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
##  <a name="onreceive"></a>  CAsyncSocket::OnReceive  
 Wywoływane przez platformę, by powiadomić tego gniazda, Brak danych w buforze, który można pobrać przez wywołanie metody **Receive** funkcję elementu członkowskiego.  
  
```  
virtual void OnReceive(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnReceive` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]  
  
##  <a name="onsend"></a>  CAsyncSocket::OnSend  
 Wywoływane przez platformę, by powiadomić gniazdo, czy teraz przesyłania danych przez wywołanie metody **wysyłania** funkcję elementu członkowskiego.  
  
```  
virtual void OnSend(int nErrorCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nErrorCode`  
 Ostatni błąd gniazda. Następujące kody błędów dotyczą `OnSend` funkcji członkowskiej:  
  
- **0** funkcja została wykonana pomyślnie.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: powiadomienia dotyczące gniazd](../../mfc/windows-sockets-socket-notifications.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]  
  
##  <a name="operator_eq"></a>  CAsyncSocket::operator =  
 Przypisuje nową wartość do `CAsyncSocket` obiektu.  
  
```  
void operator=(const CAsyncSocket& rSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `rSrc`  
 Odwołanie do istniejącej `CAsyncSocket` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby skopiować istniejące `CAsyncSocket` obiektu do innego `CAsyncSocket` obiektu.  
  
##  <a name="operator_socket"></a>  CAsyncSocket::operator GNIAZDA  
 Użyj tego operatora, aby pobrać **GNIAZDA** uchwyt `CAsyncSocket` obiektu.  
  
```  
operator SOCKET() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia dojście **GNIAZDA** obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Dojście służy do bezpośredniego wywoływania interfejsów API systemu Windows.  
  
##  <a name="receive"></a>  CAsyncSocket::Receive  
 Wywołanie funkcji członkowskiej na odbieranie danych z gniazda.  
  
```  
virtual int Receive(
    void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Bufor dla danych przychodzących.  
  
 `nBufLen`  
 Długość `lpBuf` w bajtach.  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_PEEK** wglądu przychodzących danych. Dane są kopiowane do buforu, ale nie zostanie usunięta z kolejki wejściowej.  
  
- **MSG_OOB** Przetwarzaj dane poza pasmem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, **Receive** zwraca liczbę bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAENOTCONN** gniazda nie jest połączona.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania **Receive** w gnieździe po `ShutDown` została wywołana z `nHow` równa 0 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i **Receive** Operacja spowodowałaby zablokowanie.  
  
- **WSAEMSGSIZE** datagram była zbyt duża, aby zmieścić ją w buforze określona i została obcięta.  
  
- **WSAEINVAL** gniazda nie został powiązany z **powiązać**.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do połączonych strumienia lub gniazda do przesyłania datagramów i jest używany do odczytu danych przychodzących.  
  
 Dla gniazda typu **SOCK_STREAM**, jak te informacje, które jest obecnie dostępna zgodnie z rozmiarem dostarczonego buforu jest zwracany. Jeśli skonfigurowano gniazda do odbioru w wierszu danych poza pasmem (opcja gniazda **SO_OOBINLINE**) i dane poza pasmem są nieprzeczytana, zostaną zwrócone dane tylko poza pasmem. Aplikacja może używać **IOCtlSIOCATMARK** opcji lub [OnOutOfBandData](#onoutofbanddata) ustalenie, czy wszystkie dane więcej poza pasmem pozostaje do odczytu.  
  
 Dla gniazda do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, zgodnie z rozmiarem dostarczonego buforu. Jeśli datagram jest większe od dostarczonego buforu, bufor jest wypełniony pierwsza część datagram, nadmiarowe dane zostaną utracone, a **Receive** zwraca wartość **SOCKET_ERROR** z kodem błędu ustawioną **WSAEMSGSIZE**. Jeśli dane przychodzące są niedostępne w gnieździe wartość **SOCKET_ERROR** jest zwrócił kod błędu ustawioną **WSAEWOULDBLOCK**. [Zdarzenia OnReceive](#onreceive) funkcja wywołania zwrotnego może służyć do określenia, kiedy dociera do większej ilości danych.  
  
 Jeśli gniazda jest typu **SOCK_STREAM** i strony zdalnej została zamknięta połączenia bezpiecznie, **Receive** zostanie zakończony i natychmiast 0 bajtów. Jeśli połączenie zostało zresetowane, **Receive** zakończy się niepowodzeniem z powodu błędu **WSAECONNRESET**.  
  
 **Odbieranie** powinna być wywoływana tylko raz dla każdej godziny [CAsyncSocket::OnReceive](#onreceive) jest wywoływana.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom  
 Wywołanie tej funkcji Członkowskich otrzymywanie datagram i przechowywać źródłowego adresu w [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury lub `rSocketAddress`.  
  
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
 `lpBuf`  
 Bufor dla danych przychodzących.  
  
 `nBufLen`  
 Długość `lpBuf` w bajtach.  
  
 `rSocketAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rSocketPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która przechowuje adresu źródłowego po powrocie.  
  
 `lpSockAddrLen`  
 Wskaźnik do długości adresu źródłowego w `lpSockAddr` w bajtach.  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_PEEK** wglądu przychodzących danych. Dane są kopiowane do buforu, ale nie zostanie usunięta z kolejki wejściowej.  
  
- **MSG_OOB** Przetwarzaj dane poza pasmem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, `ReceiveFrom` zwraca liczbę bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody `GetLastError`. Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument był nieprawidłowy: `lpSockAddr` bufor jest zbyt mały, aby pomieścić adres elementu równorzędnego.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEINVAL** gniazda nie został powiązany z **powiązać**.  
  
- **WSAENOTCONN** gniazda nie jest połączony ( **SOCK_STREAM** tylko).  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania `ReceiveFrom` w gnieździe po `ShutDown` została wywołana z `nHow` równa 0 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i `ReceiveFrom` Operacja spowodowałaby zablokowanie.  
  
- **WSAEMSGSIZE** datagram była zbyt duża, aby zmieścić ją w buforze określona i została obcięta.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do odczytywania przychodzących danych w gnieździe (prawdopodobnie połączonych) i przechwytywać adres, z którego dane zostały wysłane.  
  
 Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::ReceiveFromEx](#receivefromex).  
  
 Dla gniazda typu **SOCK_STREAM**, jak te informacje, które jest obecnie dostępna zgodnie z rozmiarem dostarczonego buforu jest zwracany. Jeśli skonfigurowano gniazda do odbioru w wierszu danych poza pasmem (opcja gniazda **SO_OOBINLINE**) i dane poza pasmem są nieprzeczytana, zostaną zwrócone dane tylko poza pasmem. Aplikacja może używać **IOCtlSIOCATMARK** opcji lub `OnOutOfBandData` ustalenie, czy wszystkie dane więcej poza pasmem pozostaje do odczytu. `lpSockAddr` i `lpSockAddrLen` parametry są ignorowane w przypadku **SOCK_STREAM** gniazda.  
  
 Dla gniazda do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, zgodnie z rozmiarem dostarczonego buforu. Jeśli datagram jest większe od dostarczonego buforu, bufor jest wypełniony pierwsza część wiadomości, nadmiarowe dane zostaną utracone, a `ReceiveFrom` zwraca wartość **SOCKET_ERROR** z kodem błędu ustawioną  **WSAEMSGSIZE**.  
  
 Jeśli `lpSockAddr` jest różna od zera, a gniazda jest typu **SOCK_DGRAM**, adres sieciowy gniazda, w której wysyłane dane są kopiowane do odpowiadającego [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury. Wartość wskazywana przez `lpSockAddrLen` zainicjowano rozmiar tej struktury i jest zmodyfikowany na powrót do rzeczywistego rozmiaru adres przechowywane. Jeśli dane przychodzące są niedostępne w gnieździe, `ReceiveFrom` wywołania oczekuje na dane do odbierania, chyba że jest gniazda nieblokujących. W tym przypadku wartość **SOCKET_ERROR** jest zwrócił kod błędu ustawioną **WSAEWOULDBLOCK**. `OnReceive` Wywołania zwrotnego może służyć do określenia, kiedy dociera do większej ilości danych.  
  
 Jeśli gniazda jest typu **SOCK_STREAM** i strony zdalnej została zamknięta połączenia bezpiecznie, `ReceiveFrom` zostanie zakończony i natychmiast 0 bajtów.  
  
##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx  
 Wywołanie tej funkcji Członkowskich otrzymywanie datagram i przechowywać źródłowego adresu w [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury lub `rSocketAddress` (obsługuje adresy IPv6).  
  
```  
int ReceiveFromEx(
    void* lpBuf,  
    int nBufLen,  
    CString& rSocketAddress,  
    UINT& rSocketPort,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Bufor dla danych przychodzących.  
  
 `nBufLen`  
 Długość `lpBuf` w bajtach.  
  
 `rSocketAddress`  
 Odwołanie do `CString` obiekt, który odbiera kropkowanej numer adresu IP.  
  
 `rSocketPort`  
 Odwołanie do **UINT** który przechowuje portu.  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_PEEK** wglądu przychodzących danych. Dane są kopiowane do buforu, ale nie zostanie usunięta z kolejki wejściowej.  
  
- **MSG_OOB** Przetwarzaj dane poza pasmem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, `ReceiveFromEx` zwraca liczbę bajtów. Jeśli połączenie zostało zamknięte, zwraca wartość 0. W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody `GetLastError`. Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpSockAddrLen` argument był nieprawidłowy: `lpSockAddr` bufor jest zbyt mały, aby pomieścić adres elementu równorzędnego.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEINVAL** gniazda nie został powiązany z **powiązać**.  
  
- **WSAENOTCONN** gniazda nie jest połączony ( **SOCK_STREAM** tylko).  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania `ReceiveFromEx` w gnieździe po `ShutDown` została wywołana z `nHow` równa 0 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i `ReceiveFromEx` Operacja spowodowałaby zablokowanie.  
  
- **WSAEMSGSIZE** datagram była zbyt duża, aby zmieścić ją w buforze określona i została obcięta.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do odczytywania przychodzących danych w gnieździe (prawdopodobnie połączonych) i przechwytywać adres, z którego dane zostały wysłane.  
  
 Ta funkcja jest taka sama jak [CAsyncSocket::ReceiveFrom](#receivefrom) z tą różnicą, że obsługuje ona IPv6 dotyczy również jako starszych protokołów.  
  
 Dla gniazda typu **SOCK_STREAM**, jak te informacje, które jest obecnie dostępna zgodnie z rozmiarem dostarczonego buforu jest zwracany. Jeśli skonfigurowano gniazda do odbioru w wierszu danych poza pasmem (opcja gniazda **SO_OOBINLINE**) i dane poza pasmem są nieprzeczytana, zostaną zwrócone dane tylko poza pasmem. Aplikacja może używać **IOCtlSIOCATMARK** opcji lub `OnOutOfBandData` ustalenie, czy wszystkie dane więcej poza pasmem pozostaje do odczytu. `lpSockAddr` i `lpSockAddrLen` parametry są ignorowane w przypadku **SOCK_STREAM** gniazda.  
  
 Dla gniazda do przesyłania datagramów dane są wyodrębniane z pierwszego datagram umieszczonych w kolejce, zgodnie z rozmiarem dostarczonego buforu. Jeśli datagram jest większe od dostarczonego buforu, bufor jest wypełniony pierwsza część wiadomości, nadmiarowe dane zostaną utracone, a `ReceiveFromEx` zwraca wartość **SOCKET_ERROR** z kodem błędu ustawioną  **WSAEMSGSIZE**.  
  
 Jeśli `lpSockAddr` jest różna od zera, a gniazda jest typu **SOCK_DGRAM**, adres sieciowy gniazda, w której wysyłane dane są kopiowane do odpowiadającego [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury. Wartość wskazywana przez `lpSockAddrLen` zainicjowano rozmiar tej struktury i jest zmodyfikowany na powrót do rzeczywistego rozmiaru adres przechowywane. Jeśli dane przychodzące są niedostępne w gnieździe, `ReceiveFromEx` wywołania oczekuje na dane do odbierania, chyba że jest gniazda nieblokujących. W tym przypadku wartość **SOCKET_ERROR** jest zwrócił kod błędu ustawioną **WSAEWOULDBLOCK**. `OnReceive` Wywołania zwrotnego może służyć do określenia, kiedy dociera do większej ilości danych.  
  
 Jeśli gniazda jest typu **SOCK_STREAM** i strony zdalnej została zamknięta połączenia bezpiecznie, `ReceiveFromEx` zostanie zakończony i natychmiast 0 bajtów.  
  
##  <a name="send"></a>  CAsyncSocket::Send  
 Wywołanie tej funkcji Członkowskich do wysyłania danych na połączone gniazdo.  
  
```  
virtual int Send(
    const void* lpBuf,  
    int nBufLen,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Bufor zawierający dane będą przesyłane.  
  
 `nBufLen`  
 Długość danych w `lpBuf` w bajtach.  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_DONTROUTE** Określa, że dane nie powinien podlegać routingu. Dostawca usługi Windows Sockets można zignorować tę flagę.  
  
- **MSG_OOB** wysyłania danych poza pasmem ( **SOCK_STREAM** tylko).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, **wysyłania** zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazanych przez `nBufLen`.) W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEACCES** żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEFAULT** `lpBuf` argument nie jest prawidłową część przestrzeni adresowej użytkownika.  
  
- **WSAENETRESET** musi można zresetować połączenia, ponieważ implementacja Windows Sockets go porzucić.  
  
- `WSAENOBUFS` Implementacja Windows Sockets raporty zakleszczenie buforu.  
  
- **WSAENOTCONN** gniazda nie jest połączona.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania **wysyłania** w gnieździe po `ShutDown` została wywołana z `nHow` ustawioną wartość 1 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i uniemożliwiają żądanej operacji.  
  
- **WSAEMSGSIZE** gniazda jest typu **SOCK_DGRAM**, datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.  
  
- **WSAEINVAL** gniazda nie został powiązany z **powiązać**.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
### <a name="remarks"></a>Uwagi  
 **Wyślij** służy do zapisywania danych wychodzących na połączonych strumienia lub datagram gniazda. Dla gniazda do przesyłania datagramów, należy zadbać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez **iMaxUdpDg** element [WSADATA](../../mfc/reference/wsadata-structure.md) zwrócony przez strukturę `AfxSocketInit`. Jeśli dane są zbyt długie, aby automatycznie przekazywać podstawowy protokół błąd **WSAEMSGSIZE** jest zwracany za pomocą `GetLastError`, i są przesyłane żadne dane.  
  
 Należy pamiętać, że dla datagramu gniazda pomyślne zakończenie **wysyłania** nie wskazuje, że dane zostało pomyślnie dostarczone.  
  
 Na `CAsyncSocket` obiektów typu **SOCK_STREAM**, liczba zapisanych bajtów może być między 1 a żądanej długości, w zależności od dostępności buforu na hostach lokalne i obce.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAsyncSocket::OnSend](#onsend).  
  
##  <a name="sendto"></a>  CAsyncSocket::SendTo  
 Wywołanie funkcji członkowskiej z wysyłania danych do określonego miejsca docelowego.  
  
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
 `lpBuf`  
 Bufor zawierający dane będą przesyłane.  
  
 `nBufLen`  
 Długość danych w `lpBuf` w bajtach.  
  
 `nHostPort`  
 Port identyfikowanie aplikacji gniazda.  
  
 `lpszHostAddress`  
 Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa komputera, takich jak "pod adresem" lub liczbą kropkami, takie jak "128.56.22.8".  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_DONTROUTE** Określa, że dane nie powinien podlegać routingu. Dostawca usługi Windows Sockets można zignorować tę flagę.  
  
- **MSG_OOB** wysyłania danych poza pasmem ( **SOCK_STREAM** tylko).  
  
 `lpSockAddr`  
 Wskaźnik do [SOCKADDR](../../mfc/reference/sockaddr-structure.md) strukturę, która zawiera adres gniazda docelowego.  
  
 `nSockAddrLen`  
 Długość adresu w `lpSockAddr` w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, `SendTo` zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazanych przez `nBufLen`.) W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEACCES** żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEFAULT** `lpBuf` lub `lpSockAddr` parametry nie są częścią przestrzeni adresowej użytkowników lub `lpSockAddr` argument jest za mały (mniejszą niż rozmiar [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury).  
  
- **WSAEINVAL** nazwa hosta jest nieprawidłowa.  
  
- **WSAENETRESET** musi można zresetować połączenia, ponieważ implementacja Windows Sockets go porzucić.  
  
- `WSAENOBUFS` Implementacja Windows Sockets raporty zakleszczenie buforu.  
  
- **WSAENOTCONN** gniazda nie jest połączony ( **SOCK_STREAM** tylko).  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania `SendTo` w gnieździe po `ShutDown` została wywołana z `nHow` ustawioną wartość 1 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i uniemożliwiają żądanej operacji.  
  
- **WSAEMSGSIZE** gniazda jest typu **SOCK_DGRAM**, datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
- **WSAEADDRNOTAVAIL** określony adres nie jest dostępny z komputera lokalnego.  
  
- **WSAEAFNOSUPPORT** adresów w określonej rodzinie nie można używać z tego gniazda.  
  
- **WSAEDESTADDRREQ** wymagany jest adres docelowy.  
  
- **WSAENETUNREACH** sieci jest nieosiągalny z tego hosta w tym momencie.  
  
### <a name="remarks"></a>Uwagi  
 `SendTo` jest używany na sockets datagram lub strumienia i służy do zapisywania danych wychodzących dla gniazda. Dla gniazda do przesyłania datagramów, należy zadbać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez **iMaxUdpDg** element [WSADATA](../../mfc/reference/wsadata-structure.md) struktury wypełnia [ Afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby automatycznie przekazywać podstawowy protokół błąd **WSAEMSGSIZE** jest zwracany, i są przesyłane żadne dane.  
  
 Należy pamiętać, że pomyślne zakończenie `SendTo` nie wskazuje, że dane zostało pomyślnie dostarczone.  
  
 `SendTo` jest używana tylko na **SOCK_DGRAM** gniazda do wysłania datagramu do określonych gniazda identyfikowane przez `lpSockAddr` parametru.  
  
 Aby wysłać emisji (na **SOCK_DGRAM** tylko), adres w `lpSockAddr` parametr powinien być skonstruowany przy użyciu specjalnego adresu IP **INADDR_BROADCAST** (zdefiniowany w nagłówku Windows Sockets Plik WINSOCK. H) wraz z numer portu zamierzone. Lub, jeśli `lpszHostAddress` parametr jest **NULL**, gniazda jest skonfigurowany do emisji. Nie jest zazwyczaj wskazane dla datagramu emisji przekracza rozmiar, w którym fragmentacji może wystąpić, co oznacza, że część datagramów (z wyjątkiem nagłówki) nie może przekraczać 512 bajtów.  
  
 Aby obsługiwać adresy IPv6, należy użyć [CAsyncSocket::SendToEx](#sendtoex).  
  
##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx  
 Wywołanie funkcji członkowskiej z wysyłania danych do określonego miejsca docelowego (dojść adresów IPv6).  
  
```  
int SendToEx(
    const void* lpBuf,  
    int nBufLen,  
    UINT nHostPort,  
    LPCTSTR lpszHostAddress = NULL,  
    int nFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Bufor zawierający dane będą przesyłane.  
  
 `nBufLen`  
 Długość danych w `lpBuf` w bajtach.  
  
 `nHostPort`  
 Port identyfikowanie aplikacji gniazda.  
  
 `lpszHostAddress`  
 Adres sieciowy gniazda, do którego jest podłączony tego obiektu: Nazwa komputera, takich jak "pod adresem" lub liczbą kropkami, takie jak "128.56.22.8".  
  
 `nFlags`  
 Określa sposób, w którym jest nawiązane połączenie. Semantyka tej funkcji są określane za pomocą opcji gniazda i `nFlags` parametru. Drugie jest tworzony przez połączenie żadnego z następujących wartości z języka C++ `OR` operator:  
  
- **MSG_DONTROUTE** Określa, że dane nie powinien podlegać routingu. Dostawca usługi Windows Sockets można zignorować tę flagę.  
  
- **MSG_OOB** wysyłania danych poza pasmem ( **SOCK_STREAM** tylko).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli nie występują błędy, `SendToEx` zwraca całkowitą liczbę znaków wysyłane. (Należy pamiętać, że może to być mniejsza niż liczba wskazanych przez `nBufLen`.) W przeciwnym razie wartość **SOCKET_ERROR** jest zwracany, i określonego kodu błędu może być pobierane przez wywołanie metody [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEACCES** żądany adres jest adresem emisji, ale nie ustawiono flagi odpowiednie.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEFAULT** `lpBuf` lub `lpSockAddr` parametry nie są częścią przestrzeni adresowej użytkowników lub `lpSockAddr` argument jest za mały (mniejszą niż rozmiar [SOCKADDR](../../mfc/reference/sockaddr-structure.md) struktury).  
  
- **WSAEINVAL** nazwa hosta jest nieprawidłowa.  
  
- **WSAENETRESET** musi można zresetować połączenia, ponieważ implementacja Windows Sockets go porzucić.  
  
- `WSAENOBUFS` Implementacja Windows Sockets raporty zakleszczenie buforu.  
  
- **WSAENOTCONN** gniazda nie jest połączony ( **SOCK_STREAM** tylko).  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
- **WSAEOPNOTSUPP MSG_OOB** został określony, ale gniazda nie jest typu **SOCK_STREAM**.  
  
- **WSAESHUTDOWN** gniazda została zamknięta; nie jest możliwe do wywołania `SendToEx` w gnieździe po `ShutDown` została wywołana z `nHow` ustawioną wartość 1 lub 2.  
  
- **WSAEWOULDBLOCK** gniazda jest oznaczony jako nieblokujących i uniemożliwiają żądanej operacji.  
  
- **WSAEMSGSIZE** gniazda jest typu **SOCK_DGRAM**, datagram jest większy niż maksymalna obsługiwana przez implementację Windows Sockets.  
  
- **WSAECONNABORTED** obwodu wirtualnego zostało przerwane z powodu przekroczenia limitu czasu lub inne awarii.  
  
- **WSAECONNRESET** obwodu wirtualnego zostało zresetowane przez strony zdalnej.  
  
- **WSAEADDRNOTAVAIL** określony adres nie jest dostępny z komputera lokalnego.  
  
- **WSAEAFNOSUPPORT** adresów w określonej rodzinie nie można używać z tego gniazda.  
  
- **WSAEDESTADDRREQ** wymagany jest adres docelowy.  
  
- **WSAENETUNREACH** sieci jest nieosiągalny z tego hosta w tym momencie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak [CAsyncSocket::SendTo](#sendto) z tą różnicą, że obsługuje ona IPv6 dotyczy również jako starszych protokołów.  
  
 `SendToEx` jest używany na sockets datagram lub strumienia i służy do zapisywania danych wychodzących dla gniazda. Dla gniazda do przesyłania datagramów, należy zadbać, aby nie przekracza maksymalny rozmiar pakietów IP podsieci źródłowej określonej przez **iMaxUdpDg** element [WSADATA](../../mfc/reference/wsadata-structure.md) struktury wypełnia [ Afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit). Jeśli dane są zbyt długie, aby automatycznie przekazywać podstawowy protokół błąd **WSAEMSGSIZE** jest zwracany, i są przesyłane żadne dane.  
  
 Należy pamiętać, że pomyślne zakończenie `SendToEx` nie wskazuje, że dane zostało pomyślnie dostarczone.  
  
 `SendToEx` jest używana tylko na **SOCK_DGRAM** gniazda do wysłania datagramu do określonych gniazda identyfikowane przez `lpSockAddr` parametru.  
  
 Aby wysłać emisji (na **SOCK_DGRAM** tylko), adres w `lpSockAddr` parametr powinien być skonstruowany przy użyciu specjalnego adresu IP **INADDR_BROADCAST** (zdefiniowany w nagłówku Windows Sockets Plik WINSOCK. H) wraz z numer portu zamierzone. Lub, jeśli `lpszHostAddress` parametr jest **NULL**, gniazda jest skonfigurowany do emisji. Nie jest zazwyczaj wskazane dla datagramu emisji przekracza rozmiar, w którym fragmentacji może wystąpić, co oznacza, że część datagramów (z wyjątkiem nagłówki) nie może przekraczać 512 bajtów.  
  
##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt  
 Wywołanie tej funkcji elementu członkowskiego, aby ustawić opcję gniazda.  
  
```  
BOOL SetSockOpt(
    int nOptionName,  
    const void* lpOptionValue,  
    int nOptionLen,  
    int nLevel = SOL_SOCKET);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptionName`  
 Opcja gniazda, dla którego ma być ustawiona wartość.  
  
 `lpOptionValue`  
 Wskaźnik do buforu, w którym znajduje się wartość żądana opcji.  
  
 `nOptionLen`  
 Rozmiar `lpOptionValue` buforu w bajtach.  
  
 `nLevel`  
 Poziom, w którym zdefiniowano opcję; są tylko obsługiwane poziomy **SOL_SOCKET** i **IPPROTO_TCP**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEFAULT** `lpOptionValue` nie jest prawidłową część przestrzeni adresowej procesu.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAEINVAL** `nLevel` nie jest prawidłowy, i informacje w `lpOptionValue` jest nieprawidłowy.  
  
- **WSAENETRESET** połączenia został przekroczony podczas **SO_KEEPALIVE** jest ustawiona.  
  
- **WSAENOPROTOOPT** opcją jest nieznany lub nieobsługiwany. W szczególności **SO_BROADCAST** nie jest obsługiwana w sockets typu **SOCK_STREAM**, podczas gdy **SO_DONTLINGER**, **SO_KEEPALIVE**,  **SO_LINGER**, i **SO_OOBINLINE** nie są obsługiwane w sockets typu **SOCK_DGRAM**.  
  
- **WSAENOTCONN** połączenie zostało podczas resetowania **SO_KEEPALIVE** jest ustawiona.  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 `SetSockOpt` Ustawia bieżącą wartość opcji gniazda skojarzone z gniazdem dowolnego typu, w dowolnym stanie. Chociaż opcje może istnieć na różnych poziomach protokołu, tej specyfikacji tylko definiuje opcje, które istnieją na poziomie najwyższym "gniazda". Opcje wpływających na funkcjonowanie gniazda, takie jak czy przyspieszonego odebraniu danych w strumieniu danych normalne, czy wiadomości emisji mogą być wysyłane w gnieździe i tak dalej.  
  
 Istnieją dwa typy opcji gniazda: opcje logiczna włączyć lub wyłączyć funkcję lub zachowania i opcje, które wymagają wartość całkowitą lub struktury. Aby włączyć opcję Boolean, `lpOptionValue` wskazuje niezerowej liczby całkowitej. Aby wyłączyć opcję `lpOptionValue` wskazuje na liczbę całkowitą równą zero. `nOptionLen` powinna być równa **sizeof(BOOL)** opcji Boolean. Inne opcje `lpOptionValue` wskazuje całkowitą lub struktura zawierająca wymaganą wartość w przypadku opcji i `nOptionLen` jest to liczba całkowita lub struktury.  
  
 **SO_LINGER** formanty akcję wykonywaną, gdy niewysłane danych znajduje się w kolejce na gnieździe i **zamknąć** funkcja jest wywoływana, aby zamknąć gniazda.  
  
 Domyślnie nie można powiązać gniazda (zobacz [powiązać](#bind)) do lokalnego adresu, który jest już używana. Czasem jednak może być pożądane "ponowne użycie" adresu w ten sposób. Ponieważ każdy połączenie jest unikatowo identyfikowana przez kombinację adresów lokalnych i zdalnych, nie jest problemy z o dwóch gniazdach powiązany z tego samego adresu lokalnego tak długo, jak zdalne adresy są różne.  
  
 Informowanie implementacji usługi Windows Sockets który **powiązać** wywołania dla gniazda nie powinny być niedozwolone, ponieważ żądany adres jest już używany przez inny gniazda, należy ustawić aplikacji **SO_REUSEADDR**gniazda opcji dla gniazda przed wystawieniem **powiązać** wywołania. Należy pamiętać, interpretację opcję tylko w czasie **powiązać** wywołania: jest konieczne (ale nieszkodliwe) można ustawić opcję dla gniazda, które nie może być powiązane z istniejącego adresu i ustawiania lub resetowania opcji po **Powiązać** wywołania nie ma wpływu na to lub inne gniazda.  
  
 Aplikacja może zażądać, że implementacja Windows Sockets korzystanie z pakietów "keep-alive" w przypadku połączeń protokołu Transmission Control Protocol (TCP) dzięki włączeniu **SO_KEEPALIVE** gniazda opcji. Implementacja Windows Sockets muszą nie obsługują utrzymywania aktywności: Jeśli tak, dokładne semantyki są specyficzne dla implementacji, ale powinna być zgodna z sekcji 4.2.3.6 specyfikacji RFC 1122: "wymagania dotyczące hostów internetowych — warstwy komunikacji." Jeśli połączenie zostało przerwane w wyniku "utrzymywania aktywności" Kod błędu: **WSAENETRESET** jest zwracana do żadnych wywołań w toku w gnieździe, i kolejnych wywołań zakończy się niepowodzeniem z **WSAENOTCONN**.  
  
 **TCP_NODELAY** opcja powoduje wyłączenie algorytmu Nagle'a. Aby zmniejszyć liczbę małe pakiety wysyłane przez hosta przez buforowanie niepotwierdzonych wysyłania danych do czasu w pełnym rozmiarze pakiecie mogą być wysyłane jest używany algorytm Nagle'a. Jednak w niektórych aplikacjach tego algorytmu może utrudniać wydajności, i **TCP_NODELAY** można ją wyłączyć. Nie należy ustawiać zapisywania aplikacji **TCP_NODELAY** chyba, że wpływ tej czynności jest przejrzyste i odpowiednie, ponieważ ustawienie **TCP_NODELAY** może mieć znaczący wpływ na wydajność sieci . **TCP_NODELAY** jest to jedyny obsługiwany opcję gniazda, która korzysta z poziomu **IPPROTO_TCP**; Użyj innych opcji poziomu **SOL_SOCKET**.  
  
 Niektóre implementacje dostaw Windows Sockets output informacji o debugowaniu, jeśli **SO_DEBUG** opcja została ustawiona przez aplikację.  
  
 Poniższe opcje są obsługiwane w przypadku `SetSockOpt`. Typ określa typ danych dotyczy `lpOptionValue`.  
  
|Wartość|Typ|Znaczenie|  
|-----------|----------|-------------|  
|**SO_BROADCAST**|**BOOL**|Zezwalaj na przekazywania komunikatów rozgłaszanych w gnieździe.|  
|**SO_DEBUG**|**BOOL**|Rekord informacji o debugowaniu.|  
|**SO_DONTLINGER**|**BOOL**|Nie należy blokować **Zamknij** oczekiwania nie wysłane dane do wysłania. Ta opcja jest odpowiednikiem ustawienia **SO_LINGER** z **l_onoff** ustawić na zero.|  
|**SO_DONTROUTE**|**BOOL**|Nie trasy: Wyślij bezpośrednio do interfejsu.|  
|**SO_KEEPALIVE**|**BOOL**|Wyślij utrzymywania aktywności.|  
|**SO_LINGER**|**Struktura LINGER**|Linger **Zamknij** Jeśli niewysłane danych jest obecny.|  
|**SO_OOBINLINE**|**BOOL**|Odbieranie danych poza pasmem w strumieniu danych normalnego.|  
|**SO_RCVBUF**|`int`|Określ rozmiar buforu dla odbiera.|  
|**SO_REUSEADDR**|**BOOL**|Zezwalaj na gniazdo może być powiązane z adresu, który jest już używana. (Zobacz [powiązać](#bind).)|  
|**SO_SNDBUF**|`int`|Określ rozmiar buforu wysyła.|  
|**TCP_NODELAY**|**BOOL**|Wyłącza algorytm Nagle'a łączenie wysyłania.|  
  
 Opcje dystrybucji oprogramowania Berkeley (BSD) nie jest obsługiwane dla `SetSockOpt` są:  
  
|Wartość|Typ|Znaczenie|  
|-----------|----------|-------------|  
|**SO_ACCEPTCONN**|**BOOL**|Nasłuchuje gniazda|  
|**SO_ERROR**|`int`|Pobierz stan błędu i usuń zaznaczenie.|  
|**SO_RCVLOWAT**|`int`|Odbieranie znaku wodnym niskiego poziomu.|  
|**SO_RCVTIMEO**|`int`|Odbieranie limitu czasu|  
|**SO_SNDLOWAT**|`int`|Wyślij znaku wodnym niskiego poziomu.|  
|**SO_SNDTIMEO**|`int`|Limitu czasu wysyłania.|  
|**SO_TYPE**|`int`|Typ gniazda.|  
|**IP_OPTIONS**||Ustaw opcje pole w nagłówku protokołu IP.|  
  
##  <a name="shutdown"></a>  CAsyncSocket::ShutDown  
 Wywołanie tej funkcji członkowskiej, aby wyłączyć wysyła, otrzymuje, lub na gniazda.  
  
```  
BOOL ShutDown(int nHow = sends);
```  
  
### <a name="parameters"></a>Parametry  
 `nHow`  
 Flaga, która opisuje jakie rodzaje operacji nie będzie dozwolone, przy użyciu następujących wartości:  
  
- **odbiera = 0**  
  
- **Wysyła = 1**  
  
- **zarówno = 2**  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość 0, a kod błędu można pobranej poprzez wywołanie [GetLastError](#getlasterror). Do funkcji członkowskiej Zastosuj następujące błędy:  
  
- **WSANOTINITIALISED** pomyślnie [afxsocketinit —](../../mfc/reference/application-information-and-management.md#afxsocketinit) musi wystąpić przed zastosowaniem tego interfejsu API.  
  
- **WSAENETDOWN** implementacja Windows Sockets wykrył, że podsystem sieci nie powiodło się.  
  
- **WSAEINVAL** `nHow` jest nieprawidłowy.  
  
- **WSAEINPROGRESS** operacji blokowania Windows Sockets jest w toku.  
  
- **WSAENOTCONN** gniazda nie jest połączony ( **SOCK_STREAM** tylko).  
  
- **WSAENOTSOCK** deskryptor nie jest gniazda.  
  
### <a name="remarks"></a>Uwagi  
 `ShutDown` jest używany na wszystkich typach gniazd wyłączyć odbieranie i/lub transmisji. Jeśli `nHow` wynosi 0, kolejne odbiera na gniazdo będzie niedozwolone. To nie ma wpływu na niższych warstwach protokołu.  
  
 Dla protokołu TCP (Transmission Control), okno TCP nie ulega zmianie i dane przychodzące będą akceptowane (ale nie potwierdzonego) wyczerpania okna. Datagramy przychodzące dla protokołu UDP (User Datagram), są akceptowane i umieszczonych w kolejce. W żadnym przypadku nie będzie można wygenerować pakiet błąd ICMP. Jeśli `nHow` 1, wysyła kolejne są niedozwolone. Dla gniazda TCP zostaną przesłane w wynikach wyszukiwania. Ustawienie `nHow` 2 powoduje wyłączenie zarówno wysyła i odbiera zgodnie z powyższym opisem.  
  
 Należy pamiętać, że `ShutDown` jest nie Zamknij gniazda i zasoby dołączony do gniazda nie zostanie zwolniona do **zamknąć** jest wywoływana. Aplikacja nie należy polegać na możliwość ponownego użycia gniazda po jego zamknięciu. W szczególności implementacji usługi Windows Sockets nie jest wymagany do obsługi użycia **Connect** na takie gniazda.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAsyncSocket::OnReceive](#onreceive).  
  
##  <a name="socket"></a>  CASyncSocket::Socket  
 Przydziela uchwyt gniazda.  
  
```  
BOOL Socket(
    int nSocketType = SOCK_STREAM,  
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,  
    int nProtocolType = 0,  
    int nAddressFormat = PF_INET);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketType`  
 Określa `SOCK_STREAM` lub `SOCK_DGRAM`.  
  
 `lEvent`  
 Maski, który określa kombinację zdarzenia sieci, w których aplikacja jest zainteresowana.  
  
- `FD_READ`: Chcesz otrzymywać powiadomienia o gotowości do odczytu.  
  
- `FD_WRITE`: Chcesz otrzymywać powiadomienia o gotowości do zapisu.  
  
- `FD_OOB`: Chcesz otrzymywać powiadomienia o dostarczeniu danych poza pasmem.  
  
- `FD_ACCEPT`: Chcesz otrzymywać powiadomienia o połączeń przychodzących.  
  
- `FD_CONNECT`: Chcesz otrzymywać powiadomienia o ukończone połączenia.  
  
- `FD_CLOSE`: Chcesz otrzymywać powiadomienia o zamknięcia gniazda.  
  
 `nProtocolType`  
 Protokół do użycia z gniazda specyficzne dla rodziny wskazany adres.  
  
 `nAddressFormat`  
 Adres specyfikacji rodziny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` w przypadku powodzenia `FALSE` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przydziela uchwyt gniazda. Nie wywołuje [CAsyncSocket::Bind](#bind) można powiązać gniazda z określonym adresem, więc należy wywołać `Bind` później, aby powiązać gniazda z określonego adresu. Można użyć [CAsyncSocket::SetSockOpt](#setsockopt) można ustawić opcji gniazda przed jest powiązany.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CSocket — klasa](../../mfc/reference/csocket-class.md)   
 [Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
