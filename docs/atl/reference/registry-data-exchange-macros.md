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
ms.openlocfilehash: c1a746487b799979cd83f2900a0f7a12d21a6837
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524860"
---
# <a name="registry-data-exchange-macros"></a>Makra wymiany danych rejestru

Te makra wykonywanie operacji wymiany danych rejestru.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Oznacza początek mapy wymiany danych rejestru.|
|[END_RDX_MAP](#end_rdx_map)|Oznacza koniec mapy wymiany danych rejestru.|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu CString.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu DWORD.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu TCHAR.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlplus.h

##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP

Oznacza początek mapy wymiany danych rejestru.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Uwagi

Następujące makra są używane w mapie wymiany danych rejestru, aby odczytywać i zapisywać wpisy w rejestrze systemu:

|Macro|Opis|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu BYTE.|
|[RDX_DWORD](#rdx_dword)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu CString.|
|[RDX_TEXT](#rdx_text)|Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu TCHAR.|

Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcji składowej o takiej samej nazwie, utworzone przez BEGIN_RDX_MAP i END_RDX_MAP makra, należy używać zawsze wtedy, gdy kod musi wymianę danych między rejestru systemowego i określone w mapowaniu RDX zmienne.

##  <a name="end_rdx_map"></a>  END_RDX_MAP

Oznacza koniec mapy wymiany danych rejestru.

```
END_RDX_MAP
```

##  <a name="rdx_binary"></a>  RDX_BINARY

Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*KLUCZ_GŁÓWNY*<br/>
Głównego klucza rejestru.

*podklucza*<br/>
Podklucz rejestru.

*VALUENAME*<br/>
Klucz rejestru.

*Element członkowski*<br/>
Zmiennej składowej do skojarzenia z określony wpis rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z BEGIN_RDX_MAP i END_RDX_MAP makra, aby skojarzyć zmienną składową z wpisu rejestru danego. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcji składowej o takiej samej nazwie, utworzone przez BEGIN_RDX_MAP i END_RDX_MAP makra, powinny być używane do wykonania wymiany danych między rejestru systemowego i zmienne Członkowskie na mapie RDX.

##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT

Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*KLUCZ_GŁÓWNY*<br/>
Głównego klucza rejestru.

*podklucza*<br/>
Podklucz rejestru.

*VALUENAME*<br/>
Klucz rejestru.

*Element członkowski*<br/>
Zmiennej składowej do skojarzenia z określony wpis rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z BEGIN_RDX_MAP i END_RDX_MAP makra, aby skojarzyć zmienną składową z wpisu rejestru danego. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcji składowej o takiej samej nazwie, utworzone przez BEGIN_RDX_MAP i END_RDX_MAP makra, powinny być używane do wykonania wymiany danych między rejestru systemowego i zmienne Członkowskie na mapie RDX.

##  <a name="rdx_dword"></a>  RDX_DWORD

Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*KLUCZ_GŁÓWNY*<br/>
Głównego klucza rejestru.

*podklucza*<br/>
Podklucz rejestru.

*VALUENAME*<br/>
Klucz rejestru.

*Element członkowski*<br/>
Zmiennej składowej do skojarzenia z określony wpis rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z BEGIN_RDX_MAP i END_RDX_MAP makra, aby skojarzyć zmienną składową z wpisu rejestru danego. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcji składowej o takiej samej nazwie, utworzone przez BEGIN_RDX_MAP i END_RDX_MAP makra, powinny być używane do wykonania wymiany danych między rejestru systemowego i zmienne Członkowskie na mapie RDX.

##  <a name="rdx_text"></a>  RDX_TEXT

Kojarzy określony wpis rejestru przy użyciu zmiennej określonego elementu członkowskiego typu TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parametry

*KLUCZ_GŁÓWNY*<br/>
Głównego klucza rejestru.

*podklucza*<br/>
Podklucz rejestru.

*VALUENAME*<br/>
Klucz rejestru.

*Element członkowski*<br/>
Zmiennej składowej do skojarzenia z określony wpis rejestru.

*member_size*<br/>
Rozmiar w bajtach zmiennej składowej.

### <a name="remarks"></a>Uwagi

To makro jest używane w połączeniu z BEGIN_RDX_MAP i END_RDX_MAP makra, aby skojarzyć zmienną składową z wpisu rejestru danego. Funkcja globalna [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), lub funkcji składowej o takiej samej nazwie, utworzone przez BEGIN_RDX_MAP i END_RDX_MAP makra, powinny być używane do wykonania wymiany danych między rejestru systemowego i zmienne Członkowskie na mapie RDX.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)

