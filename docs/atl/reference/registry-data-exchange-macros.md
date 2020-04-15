---
title: Makra wymiany danych rejestru
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326068"
---
# <a name="registry-data-exchange-macros"></a>Makra wymiany danych rejestru

Te makra wykonują operacje wymiany danych rejestru.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Oznacza początek mapy wymiany danych rejestru.|
|[END_RDX_MAP](#end_rdx_map)|Oznacza koniec mapy wymiany danych rejestru.|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określoną zmienną członkowskie typu BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu CString.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu DWORD.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu TCHAR.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Oznacza początek mapy wymiany danych rejestru.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Uwagi

Następujące makra są używane na mapie wymiany danych rejestru do odczytu i zapisu wpisów w rejestrze systemowym:

|Makro|Opis|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określoną zmienną członkowskie typu BYTE.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu CString.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowną typu TCHAR.|

Funkcja [globalna RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja elementu członkowskiego o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinny być używane zawsze, gdy kod musi wymieniać dane między rejestrem systemowym a zmiennymi określonymi na mapie RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Oznacza koniec mapy wymiany danych rejestru.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Kojarzy określony wpis rejestru z określoną zmienną członkowskie typu BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*klucz główny*<br/>
Katalog główny klucza rejestru.

*Podklucz*<br/>
Podklucz rejestru.

*Valuename*<br/>
Klucz rejestru.

*Członkowskich*<br/>
Zmienna elementu członkowskiego do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej członkowskiej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP w celu skojarzenia zmiennej członkowskiej z danym wpisem rejestru. Funkcja [globalna RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja elementu członkowskiego o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinny być używane do wymiany danych między rejestrem systemowym a zmiennymi członkowskimi na mapie RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Kojarzy określony wpis rejestru z określoną zmienną członkowną typu CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*klucz główny*<br/>
Katalog główny klucza rejestru.

*Podklucz*<br/>
Podklucz rejestru.

*Valuename*<br/>
Klucz rejestru.

*Członkowskich*<br/>
Zmienna elementu członkowskiego do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej członkowskiej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP w celu skojarzenia zmiennej członkowskiej z danym wpisem rejestru. Funkcja [globalna RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja elementu członkowskiego o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinny być używane do wymiany danych między rejestrem systemowym a zmiennymi członkowskimi na mapie RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Kojarzy określony wpis rejestru z określoną zmienną członkowną typu DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*klucz główny*<br/>
Katalog główny klucza rejestru.

*Podklucz*<br/>
Podklucz rejestru.

*Valuename*<br/>
Klucz rejestru.

*Członkowskich*<br/>
Zmienna elementu członkowskiego do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej członkowskiej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP w celu skojarzenia zmiennej członkowskiej z danym wpisem rejestru. Funkcja [globalna RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja elementu członkowskiego o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinny być używane do wymiany danych między rejestrem systemowym a zmiennymi członkowskimi na mapie RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Kojarzy określony wpis rejestru z określoną zmienną członkowną typu TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*klucz główny*<br/>
Katalog główny klucza rejestru.

*Podklucz*<br/>
Podklucz rejestru.

*Valuename*<br/>
Klucz rejestru.

*Członkowskich*<br/>
Zmienna elementu członkowskiego do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej członkowskiej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP w celu skojarzenia zmiennej członkowskiej z danym wpisem rejestru. Funkcja [globalna RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja elementu członkowskiego o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinny być używane do wymiany danych między rejestrem systemowym a zmiennymi członkowskimi na mapie RDX.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Rejestracja danych rejestru](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
