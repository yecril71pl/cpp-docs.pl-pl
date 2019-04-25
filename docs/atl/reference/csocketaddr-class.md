---
title: CSocketAddr Class
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
ms.openlocfilehash: e94d92b11a7f200edb1815a0b384d0fc0428001f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277477"
---
# <a name="csocketaddr-class"></a>CSocketAddr Class

Ta klasa dostarcza metody do konwertowania nazwy hostów na adresy hosta, obsługa formatów IPv4 i IPV6.

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
|[CSocketAddr::FindAddr](#findaddr)|Wywołaj tę metodę, aby przekonwertować podanej nazwy hosta na adres hosta.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Wywołaj tę metodę można skonwertować nazwy hosta IPv4 adres hosta.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Wywołaj tę metodę można skonwertować nazwy hosta IPv6 adres hosta.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Wywołaj tę metodę, aby zwrócić wskaźnik do określonego elementu w `addrinfo` listy.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Wywołaj tę metodę, aby zwrócić wskaźnik do `addrinfo` listy.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia wersję adresu IP, że niezależny od podejścia do wyszukiwania adresów sieciowych do użytku z programem Windows sockets funkcje interfejsu API i otoki gniazda w bibliotekach.

Elementy członkowskie tej klasy, które są używane do wyszukiwania adresów sieciowych należy użyć funkcji Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Wersja ANSI lub UNICODE tej funkcji jest wywoływana w zależności od tego, czy kod jest kompilowany dla ANSI lub UNICODE.

Ta klasa obsługuje oba adresy IPv4 andIPv6 sieci.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsocket.h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

Konstruktor.

```
CSocketAddr();
```

### <a name="remarks"></a>Uwagi

Tworzy nową `CSocketAddr` obiektu i inicjuje połączonej listy zawierający informacje o odpowiedzi o hoście.

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

Wywołaj tę metodę, aby przekonwertować podanej nazwy hosta na adres hosta.

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
Nazwa hosta lub kropkowana adresu IP.

*szPortOrServiceName*<br/>
Numer portu lub nazwy usługi na hoście.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub kombinacji AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*addr_family*<br/>
Rodzina (na przykład PF_INET) adresów.

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

*ai_proto*<br/>
Protokół (na przykład IPPROTO_IP lub IPPROTO_IPV6).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca wartość różną od zera kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli operacja się powiedzie, adres obliczeniowe są przechowywane w połączonej listy, który można odwoływać się za pomocą `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Uwagi

Parametr nazwy hosta może być w formacie IPv4 lub IPv6. Ta metoda wywołuje funkcję Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) dokonać konwersji.

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

Wywołaj tę metodę można skonwertować nazwy hosta IPv4 adres hosta.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Nazwa hosta lub kropkowana adresu IP.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub kombinacji AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca wartość różną od zera kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli operacja się powiedzie, adres obliczeniowe są przechowywane w połączonej listy, który można odwoływać się za pomocą `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) dokonać konwersji.

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

Wywołaj tę metodę można skonwertować nazwy hosta IPv6 adres hosta.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*szHost*<br/>
Nazwa hosta lub kropkowana adresu IP.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub kombinacji AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (na przykład SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca wartość różną od zera kod błędu gniazda Windows w przypadku niepowodzenia. Jeśli operacja się powiedzie, adres obliczeniowe są przechowywane w połączonej listy, który można odwoływać się za pomocą `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję Win32 API [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) dokonać konwersji.

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

Wywołaj tę metodę, aby zwrócić wskaźnik do określonego elementu w `addrinfo` listy.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Odwołanie do określonego elementu w [addrinfo](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa) listy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `addrinfo` struktury odwołuje się *nIndex* połączonej liście zawierający informacje o odpowiedzi o hoście.

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

Wywołaj tę metodę, aby zwrócić wskaźnik do `addrinfo` listy.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do połączonej listy co najmniej jednego `addrinfo` struktury zawierające odpowiedzi informacje o hoście. Aby uzyskać więcej informacji, zobacz [struktury addrinfo](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa).

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
