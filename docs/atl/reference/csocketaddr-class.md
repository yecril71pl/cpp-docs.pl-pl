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
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330679"
---
# <a name="csocketaddr-class"></a>Klasa CSocketAddr

Ta klasa zawiera metody konwertowania nazw hostów na adresy hostów, obsługujące zarówno formaty IPv4, jak i IPV6.

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
|[CSocketAddr::FindAddr](#findaddr)|Wywołanie tej metody, aby przekonwertować podoną nazwę hosta na adres hosta.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Wywołanie tej metody, aby przekonwertować nazwę hosta IPv4 na adres hosta.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Wywołanie tej metody, aby przekonwertować nazwę hosta IPv6 na adres hosta.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Wywołanie tej metody, aby zwrócić wskaźnik `addrinfo` do określonego elementu na liście.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Wywołanie tej metody, aby `addrinfo` powrócić wskaźnik do listy.|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia podejście niezależnego od wersji IP do wyszukiwania adresów sieciowych do użytku z funkcjami interfejsu API gniazd systemu Windows i otokami gniazd w bibliotekach.

Członkowie tej klasy, którzy są używane do wyszukiwania adresów sieciowych, używają funkcji interfejsu API Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Wersja ANSI lub UNICODE funkcji jest wywoływana w zależności od tego, czy kod jest kompilowany dla ANSI lub UNICODE.

Ta klasa obsługuje zarówno adresy sieciowe IPv4, jak i IPv6.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Konstruktor.

```
CSocketAddr();
```

### <a name="remarks"></a>Uwagi

Tworzy nowy `CSocketAddr` obiekt i inicjuje połączoną listę zawierającą informacje o odpowiedzi na temat hosta.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr

Wywołanie tej metody, aby przekonwertować podoną nazwę hosta na adres hosta.

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

*SzHost (szHost)*<br/>
Nazwa hosta lub adres IP kropkowane.

*szPortorServiceName (Nazwa usługi szPortorServiceName)*<br/>
Numer portu lub nazwa usługi na hoście.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub połączenie AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*addr_family*<br/>
Rodzina adresów (np. PF_INET).

*sock_type*<br/>
Typ gniazda (np. SOCK_STREAM).

*ai_proto*<br/>
protokołu (takiego jak IPPROTO_IP lub IPPROTO_IPV6).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli adres został pomyślnie obliczony. Zwraca kod błędu niezerowego gniazda systemu Windows w przypadku awarii. Jeśli się powiedzie, obliczony adres jest przechowywany na `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`połączonej liście, do którego można się odwoływać, za pomocą i .

### <a name="remarks"></a>Uwagi

Parametr nazwy hosta może być w formacie IPv4 lub IPv6. Ta metoda wywołuje [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) funkcji interfejsu API Win32 do wykonania konwersji.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Wywołanie tej metody, aby przekonwertować nazwę hosta IPv4 na adres hosta.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*SzHost (szHost)*<br/>
Nazwa hosta lub adres IP kropkowane.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub połączenie AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (np. SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli adres został pomyślnie obliczony. Zwraca kod błędu niezerowego gniazda systemu Windows w przypadku awarii. Jeśli się powiedzie, obliczony adres jest przechowywany na `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`połączonej liście, do którego można się odwoływać, za pomocą i .

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) funkcji interfejsu API Win32 do wykonania konwersji.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Wywołanie tej metody, aby przekonwertować nazwę hosta IPv6 na adres hosta.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parametry

*SzHost (szHost)*<br/>
Nazwa hosta lub adres IP kropkowane.

*nPortNo*<br/>
Numer portu.

*flagi*<br/>
0 lub połączenie AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.

*sock_type*<br/>
Typ gniazda (np. SOCK_STREAM).

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero, jeśli adres został pomyślnie obliczony. Zwraca kod błędu niezerowego gniazda systemu Windows w przypadku awarii. Jeśli się powiedzie, obliczony adres jest przechowywany na `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`połączonej liście, do którego można się odwoływać, za pomocą i .

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) funkcji interfejsu API Win32 do wykonania konwersji.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Wywołanie tej metody, aby zwrócić wskaźnik `addrinfo` do określonego elementu na liście.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Odwołanie do określonego elementu na liście [addrinfo.](/windows/win32/api/ws2def/ns-ws2def-addrinfow)

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `addrinfo` struktury, do którego odwołuje się *nIndex* na połączonej liście zawierającej informacje o odpowiedzi o hoście.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Wywołanie tej metody, aby `addrinfo` powrócić wskaźnik do listy.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do połączonej listy `addrinfo` jednej lub więcej struktur zawierających informacje o odpowiedzi na temat hosta. Aby uzyskać więcej informacji, zobacz [addrinfo structure](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
