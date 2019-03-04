---
title: Makra obiektu przystawki
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: b75dd04bed4895d722939d1bf9c0a6dfff2126e0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292609"
---
# <a name="snap-in-object-macros"></a>Makra obiektu przystawki

Te makra zapewniają obsługę rozszerzeń przystawek.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Oznacza początek mapowanie rozszerzenia przystawki danych klasy dla obiektu przystawki.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Oznacza początek mapy narzędzi dla obiektu przystawki.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Oznacza koniec mapowanie rozszerzenia przystawki danych klasy dla obiektu przystawki.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Oznacza koniec mapy narzędzi dla obiektu przystawki.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Tworzy element członkowski danych dla klasy danych rozszerzenia przystawki.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Wprowadza klasy danych rozszerzenia przystawki do mapowania klas danych rozszerzenia przystawki obiektu przystawki.|
|[SNAPINMENUID](#snapinmenuid)|Deklaruje identyfikator z menu kontekstowego używane przez obiekt przystawki.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Wprowadza pasek narzędzi w mapie narzędzi obiektu przystawki.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap.h

##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza początek przystawkę rozszerzenia mapowania klasy danych.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parametry

*classname*<br/>
[in] Nazwa klasy danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Start mapy przystawkę rozszerzenia za pomocą makra BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, dodać wpisy dla każdego z typów danych w przystawce rozszerzenia za pomocą [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makro i wykonaj mapy za pomocą [ END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP

Deklaruje początku mapy identyfikator narzędzi dla obiektu przystawki.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[in] Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza koniec przystawkę rozszerzenia mapowania klasy danych.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Uwagi

Uruchom przystawkę rozszerzenia mapy za pomocą [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, dodać wpisy dla wszystkich typów danych przystawki rozszerzenia za pomocą [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra i ukończyć mapy za pomocą makra END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP

Deklaruje koniec mapy identyfikator narzędzi dla obiektu przystawki.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[in] Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS

Dodaje element członkowski danych do rozszerzenia przystawki klasy danych dla **ISnapInItemImpl**-klasy pochodnej.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
[in] Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Ta klasa stosuje się do mapy klasy przystawki rozszerzenia danych. Uruchom rozszerzenie przystawki mapę klasy danych za pomocą [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, dodać wpisy dla każdego z typów danych w przystawce rozszerzenia za pomocą [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)makro i wykonaj mapy za pomocą [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY

Dodaje klasę danych rozszerzenia przystawki do mapowania klas danych rozszerzenia przystawki.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
[in] Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Uruchom rozszerzenie przystawki mapę klasy danych za pomocą [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makro, dodać wpisy dla każdego z typów danych w przystawce rozszerzenia za pomocą makra EXTENSION_SNAPIN_NODEINFO_ENTRY, a następnie ukończ mapy za pomocą [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="snapinmenuid"></a>  SNAPINMENUID

Użyj tego makra, aby zadeklarować zasobów menu kontekstowe obiektu przystawki.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Określa menu kontekstowe obiektu przystawki.

##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY

Użyj tego makra, aby wprowadzić identyfikator narzędzi do przystawki obiektu narzędzi identyfikator mapy.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Identyfikuje formant paska narzędzi.

### <a name="remarks"></a>Uwagi

[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) — makro oznacza początek mapy identyfikator narzędzi; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) — makro oznacza koniec.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
