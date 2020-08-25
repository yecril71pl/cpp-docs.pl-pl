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
ms.openlocfilehash: 507db77b525c526fe1cd47c7d75c34e15a6a0628
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834547"
---
# <a name="registry-data-exchange-macros"></a>Makra wymiany danych rejestru

Te makra wykonują operacje wymiany danych rejestru.

|Nazwa|Opis|
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Oznacza początek mapy wymiany danych rejestru.|
|[END_RDX_MAP](#end_rdx_map)|Oznacza koniec mapy wymiany danych rejestru.|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu CString.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu DWORD.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu używanie TCHAR.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlplus. h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a> BEGIN_RDX_MAP

Oznacza początek mapy wymiany danych rejestru.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Uwagi

Następujące makra są używane w mapie wymiany danych rejestru do odczytu i zapisu wpisów w rejestrze systemowym:

|Makro|Opis|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu BYTE.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu CString.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru z określoną zmienną członkowską typu używanie TCHAR.|

Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja członkowska o tej samej nazwie, która została utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinna być używana zawsze, gdy kod wymaga wymiany danych między rejestrem systemu a zmiennymi określonymi w mapie RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a> END_RDX_MAP

Oznacza koniec mapy wymiany danych rejestru.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a> RDX_BINARY

Kojarzy określony wpis rejestru z określoną zmienną członkowską typu BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kluczem*<br/>
Katalog główny klucza rejestru.

*podrzędne*<br/>
Podklucz rejestru.

*Pełna*<br/>
Klucz rejestru.

*członkiem*<br/>
Zmienna członkowska do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar (w bajtach) zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP, aby skojarzyć zmienną członkowską z danym wpisem rejestru. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja członkowska o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinna zostać użyta do przeprowadzenia wymiany danych między rejestrem systemu a zmiennymi składowymi na mapie RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a> RDX_CSTRING_TEXT

Kojarzy określony wpis rejestru z określoną zmienną członkowską typu CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kluczem*<br/>
Katalog główny klucza rejestru.

*podrzędne*<br/>
Podklucz rejestru.

*Pełna*<br/>
Klucz rejestru.

*członkiem*<br/>
Zmienna członkowska do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar (w bajtach) zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP, aby skojarzyć zmienną członkowską z danym wpisem rejestru. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja członkowska o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinna zostać użyta do przeprowadzenia wymiany danych między rejestrem systemu a zmiennymi składowymi na mapie RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a> RDX_DWORD

Kojarzy określony wpis rejestru z określoną zmienną członkowską typu DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kluczem*<br/>
Katalog główny klucza rejestru.

*podrzędne*<br/>
Podklucz rejestru.

*Pełna*<br/>
Klucz rejestru.

*członkiem*<br/>
Zmienna członkowska do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar (w bajtach) zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP, aby skojarzyć zmienną członkowską z danym wpisem rejestru. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja członkowska o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinna zostać użyta do przeprowadzenia wymiany danych między rejestrem systemu a zmiennymi składowymi na mapie RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a> RDX_TEXT

Kojarzy określony wpis rejestru z określoną zmienną członkowską typu używanie TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*kluczem*<br/>
Katalog główny klucza rejestru.

*podrzędne*<br/>
Podklucz rejestru.

*Pełna*<br/>
Klucz rejestru.

*członkiem*<br/>
Zmienna członkowska do skojarzenia z określonym wpisem rejestru.

*member_size*<br/>
Rozmiar (w bajtach) zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z makrami BEGIN_RDX_MAP i END_RDX_MAP, aby skojarzyć zmienną członkowską z danym wpisem rejestru. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)lub funkcja członkowska o tej samej nazwie, utworzona przez makra BEGIN_RDX_MAP i END_RDX_MAP, powinna zostać użyta do przeprowadzenia wymiany danych między rejestrem systemu a zmiennymi składowymi na mapie RDX.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
