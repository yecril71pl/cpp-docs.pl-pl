---
title: Klasa CSocketAddr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 830b1087d0a4792b449c516ed12ad7e8a84b2a51
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="csocketaddr-class"></a>Klasa CSocketAddr
Ta klasa dostarcza metody do konwertowania nazwy hosta na adresy hosta, obsługa formatów protokołów IPv4 i IPV6.  
  
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
|[CSocketAddr::FindAddr](#findaddr)|Wywołaj tę metodę, aby przekonwertować podanej nazwy hosta jako adres hosta.|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Wywołanie tej metody można skonwertować nazwy hostów protokołu IPv4 jako adres hosta.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Wywołanie tej metody można skonwertować nazwy hosta IPv6 jako adres hosta.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Wywołanie tej metody do zwraca wskaźnik do elementu określonego w **addrinfo** listy.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Wywołaj tę metodę, aby zwracać wskaźnik do **addrinfo** listy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia adresu IP w wersji o niesprecyzowanym podejście do wyszukiwania adresów sieciowych dla systemu Windows sockets funkcje interfejsu API i gniazd otoki w bibliotekach.  
  
 Członkowie tej klasy, które są używane do wyszukiwania adresów sieciowych należy użyć funkcji Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Ta klasa obsługuje zarówno adresy IPv4 andIPv6 sieci.  
  
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
 Wywołaj tę metodę, aby przekonwertować podanej nazwy hosta jako adres hosta.  
  
```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Nazwa hosta lub adres IP kropkami.  
  
 *szPortOrServiceName*  
 Numer portu lub nazwy usługi na hoście.  
  
 `nPortNo`  
 Numer portu.  
  
 `flags`  
 0 lub kombinację AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.  
  
 *addr_family*  
 Rodzina (na przykład PF_INET) adresów.  
  
 `sock_type`  
 Typ gniazda (na przykład SOCK_STREAM).  
  
 *ai_proto*  
 Protokół (na przykład IPPROTO_IP lub IPPROTO_IPV6).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca niezerowy kod błędu systemu Windows gniazda, w przypadku awarii. Jeśli powodzenia obliczeniowej adresu są przechowywane w połączonej listy, który można odwoływać się przy użyciu `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Uwagi  
 Parametr nazwy hosta może być w formacie IPv4 lub IPv6. Ta metoda wywołuje funkcji Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) do wykonania konwersji.  
  
##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr  
 Wywołanie tej metody można skonwertować nazwy hostów protokołu IPv4 jako adres hosta.  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Nazwa hosta lub adres IP kropkami.  
  
 `nPortNo`  
 Numer portu.  
  
 `flags`  
 0 lub kombinację AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.  
  
 `sock_type`  
 Typ gniazda (na przykład SOCK_STREAM).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca niezerowy kod błędu systemu Windows gniazda, w przypadku awarii. Jeśli powodzenia obliczeniowej adresu są przechowywane w połączonej listy, który można odwoływać się przy użyciu `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje funkcji Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) do wykonania konwersji.  
  
##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr  
 Wywołanie tej metody można skonwertować nazwy hosta IPv6 jako adres hosta.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parametry  
 `szHost`  
 Nazwa hosta lub adres IP kropkami.  
  
 `nPortNo`  
 Numer portu.  
  
 `flags`  
 0 lub kombinację AI_PASSIVE, AI_CANONNAME lub AI_NUMERICHOST.  
  
 `sock_type`  
 Typ gniazda (na przykład SOCK_STREAM).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zero, jeśli adres jest obliczana pomyślnie. Zwraca niezerowy kod błędu systemu Windows gniazda, w przypadku awarii. Jeśli powodzenia obliczeniowej adresu są przechowywane w połączonej listy, który można odwoływać się przy użyciu `CSocketAddr::GetAddrInfoList` i `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje funkcji Win32 API [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) do wykonania konwersji.  
  
##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo  
 Wywołanie tej metody do zwraca wskaźnik do elementu określonego w **addrinfo** listy.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Odwołanie do określonego elementu w [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do **addrinfo** struktury odwołuje się `nIndex` w połączonej listy zawierający informacje o odpowiedzi o hoście.  
  
##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList  
 Wywołaj tę metodę, aby zwracać wskaźnik do **addrinfo** listy.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do listy połączonej z jedną lub więcej `addrinfo` struktury zawierające odpowiedzi informacje o hoście. Aby uzyskać więcej informacji, zobacz [struktury addrinfo](https://msdn.microsoft.com/library/windows/desktop/ms737530).
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
