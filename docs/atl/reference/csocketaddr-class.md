---
title: Klasa CSocketAddr
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496345"
---
# <a name="csocketaddr-class"></a>Klasa CSocketAddr

Ta klasa zapewnia metody konwersji nazw hostów na adresy hostów obsługujące zarówno format IPv4, jak i IPV6.

## <a name="syntax"></a>Składnia

```
class CSocketAddr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Wywołaj tę metodę, aby przekonwertować podaną nazwę hosta na adres hosta.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Wywołaj tę metodę, aby skonwertować nazwę hosta IPv4 na adres hosta.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Wywołaj tę metodę, aby skonwertować nazwę hosta IPv6 na adres hosta.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Wywołaj tę metodę, aby zwrócić wskaźnik do określonego elementu na `addrinfo` liście.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Wywołaj tę metodę, aby zwrócić wskaźnik do `addrinfo` listy.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia podejście niezależny od w wersji IP dotyczące wyszukiwania adresów sieciowych do użycia z funkcjami interfejsu API usługi Windows Sockets i otokami gniazd w bibliotekach.

Elementy członkowskie tej klasy, które są używane do wyszukiwania adresów sieciowych, używają funkcji Win32 API [Getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Wersja ANSI lub UNICODE funkcji jest wywoływana w zależności od tego, czy kod jest kompilowany dla ANSI lub UNICODE.

Ta klasa obsługuje adresy sieciowe andIPv6 IPv4.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsocket. h

##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Konstruktor.

```
CSocketAddr();
```

### <a name="remarks"></a>Uwagi

Tworzy nowy `CSocketAddr` obiekt i inicjuje połączoną listę zawierającą informacje o odpowiedzi hosta.

##  <a name="findaddr"></a>CSocketAddr::FindAddr

Wywołaj tę metodę, aby przekonwertować podaną nazwę hosta na adres hosta.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Nazwa hosta lub kropkowany adres IP.

*szPortOrServiceName*<br/>
Numer portu lub nazwa usługi na hoście.

*nPortNo*<br/>
Numer portu.

*znaczników*<br/>
0 lub kombinacja elementów AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*addr_family*<br/>
Rodzina adresów (na przykład PF_INET).

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

*ai_proto*<br/>
Protokół (na przykład IPPROTO_IP lub IPPROTO_IPV6).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczany pomyślnie. Zwraca niezerową kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli to się powiedzie, obliczony adres jest przechowywany na liście połączonej, do `CSocketAddr::GetAddrInfoList` której `CSocketAddr::GetAddrInfo`można się odwoływać przy użyciu i.

### <a name="remarks"></a>Uwagi

Parametr nazwy hosta może mieć wartość w formacie IPv4 lub IPv6. Ta metoda wywołuje funkcję Win32 API [Getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) do wykonania konwersji.

##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Wywołaj tę metodę, aby skonwertować nazwę hosta IPv4 na adres hosta.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Nazwa hosta lub kropkowany adres IP.

*nPortNo*<br/>
Numer portu.

*znaczników*<br/>
0 lub kombinacja elementów AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczany pomyślnie. Zwraca niezerową kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli to się powiedzie, obliczony adres jest przechowywany na liście połączonej, do `CSocketAddr::GetAddrInfoList` której `CSocketAddr::GetAddrInfo`można się odwoływać przy użyciu i.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję Win32 API [Getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) do wykonania konwersji.

##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Wywołaj tę metodę, aby skonwertować nazwę hosta IPv6 na adres hosta.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Nazwa hosta lub kropkowany adres IP.

*nPortNo*<br/>
Numer portu.

*znaczników*<br/>
0 lub kombinacja elementów AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczany pomyślnie. Zwraca niezerową kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli to się powiedzie, obliczony adres jest przechowywany na liście połączonej, do `CSocketAddr::GetAddrInfoList` której `CSocketAddr::GetAddrInfo`można się odwoływać przy użyciu i.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję Win32 API [Getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) do wykonania konwersji.

##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Wywołaj tę metodę, aby zwrócić wskaźnik do określonego elementu na `addrinfo` liście.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Odwołanie do określonego elementu na liście [addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury, `addrinfo` do której odwołuje się *nIndex* na liście połączonej zawierającej informacje o odpowiedzi hosta.

##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Wywołaj tę metodę, aby zwrócić wskaźnik do `addrinfo` listy.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do połączonej listy co najmniej jednej `addrinfo` struktury zawierającej informacje o odpowiedzi hosta. Aby uzyskać więcej informacji, zobacz [addrinfo Structure](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
