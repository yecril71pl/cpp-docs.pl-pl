---
title: Makra obiektów przystawek
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
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325860"
---
# <a name="snap-in-object-macros"></a>Makra obiektów przystawek

Te makra zapewniają obsługę rozszerzeń przystawek.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Oznacza początek mapy klasy danych rozszerzenia przystawki dla obiektu przystawki.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Oznacza początek mapy paska narzędzi dla obiektu przyciągania.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Oznacza koniec mapy klasy danych rozszerzenia przystawki dla obiektu przystawki.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Oznacza koniec mapy paska narzędzi dla obiektu przyciągania.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Tworzy element członkowski danych dla klasy danych rozszerzenia przystawki.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Wprowadza klasę danych rozszerzenia przystawki do mapy klasy danych rozszerzenia przystawki obiektu Przystawka.|
|[PRZYSTAWKAMENUID](#snapinmenuid)|Deklaruje identyfikator menu kontekstowego używanego przez obiekt Przystawki.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Wprowadza pasek narzędzi na pasku narzędzi obiektu Przystawka.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza początek mapy klasy danych rozszerzenia przystawki.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
[w] Nazwa klasy danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Rozpocznij mapę rozszerzenia przystawki BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP makra, dodaj wpisy dla każdego z typów danych rozszerzenia przystawki za pomocą [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra i uzupełnij mapę [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makrą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

Deklaruje początek mapy identyfikatora paska narzędzi dla obiektu Przystawki.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[w] Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza koniec mapy klasy danych rozszerzenia przystawki.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Uwagi

Rozpocznij mapę rozszerzenia [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) przystawki BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP makra, dodaj wpisy dla każdego z typów danych przystawek rozszerzenia za pomocą [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra i uzupełnij mapę END_EXTENSION_SNAPIN_NODEINFO_MAP makra.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

Deklaruje koniec mapy identyfikatora paska narzędzi dla obiektu Przystawki.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[w] Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

Dodaje element członkowski danych do klasy danych rozszerzenia przystawki dla klasy pochodnej **ISnapInItemImpl.**

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parametry

*klasa danych*<br/>
[w] Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Ta klasa powinna być również wprowadzona do mapy klasy danych rozszerzenia przystawki. Rozpocznij mapę klasy danych [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) rozszerzenia przystawki BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP makra, dodaj wpisy dla każdego z typów danych rozszerzenia przystawek za pomocą [makra EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) i uzupełnij mapę [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makrą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

Dodaje klasę danych rozszerzenia przystawki do mapy klasy danych rozszerzenia przystawki.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parametry

*klasa danych*<br/>
[w] Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Rozpocznij mapę klasy danych [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) rozszerzenia przystawki BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP makra, dodaj wpisy dla każdego z typów danych rozszerzenia przystawek za pomocą makra EXTENSION_SNAPIN_NODEINFO_ENTRY i uzupełnij mapę [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makrą.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>PRZYSTAWKAMENUID

To makro służy do deklarowania zasobu menu kontekstowego obiektu Przystawka.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikuje menu kontekstowe obiektu Przystawka.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

To makro służy do wprowadzania identyfikatora paska narzędzi na mapie identyfikatora paska narzędzi przystawka.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
[w] Identyfikuje formant paska narzędzi.

### <a name="remarks"></a>Uwagi

Makro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) oznacza początek mapy identyfikatora paska narzędzi; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) makr oznacza koniec.

### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
