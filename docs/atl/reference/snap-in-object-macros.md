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
ms.openlocfilehash: 7e006a17ad480ea79f6aeec224278815c8c3f164
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835197"
---
# <a name="snap-in-object-macros"></a>Makra obiektów przystawek

Te makra zapewniają obsługę rozszerzeń przystawek.

|Nazwa|Opis|
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Oznacza początek mapy klas danych rozszerzenia przystawki dla obiektu przystawki.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Oznacza początek mapy paska narzędzi dla obiektu przystawki.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Oznacza koniec mapy klas danych rozszerzenia przystawki dla obiektu przystawki.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Oznacza koniec mapy paska narzędzi dla obiektu przystawki.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Tworzy element członkowski danych dla klasy danych rozszerzenia przystawki.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Wprowadza klasę danych rozszerzenia przystawki do mapy klas danych rozszerzenia przystawki obiektu przystawki.|
|[SNAPINMENUID](#snapinmenuid)|Deklaruje identyfikator menu kontekstowego używanego przez obiekt przystawki.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Wprowadza pasek narzędzi do mapy paska narzędzi obiektu przystawki.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsnap. h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a> BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza początek mapy klas danych rozszerzenia przystawki.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parametry

*nazwą*<br/>
podczas Nazwa klasy danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Uruchom mapę rozszerzenia przystawki przy użyciu makra BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, Dodaj wpisy dla każdego typu danych rozszerzenia przystawki z makrem [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) i wypełnij mapę za pomocą makra [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a> BEGIN_SNAPINTOOLBARID_MAP

Deklaruje początek mapowania identyfikatora paska narzędzi dla obiektu przystawki.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
podczas Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a> END_EXTENSION_SNAPIN_NODEINFO_MAP

Oznacza koniec mapy klas danych rozszerzenia przystawki.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Uwagi

Uruchom mapę rozszerzenia przystawki przy użyciu makra [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , Dodaj wpisy dla każdego z typów danych przystawki rozszerzenia za pomocą makra [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) i wypełnij mapę za pomocą makra END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a> END_SNAPINTOOLBARID_MAP

Deklaruje koniec mapy identyfikatora paska narzędzi dla obiektu przystawki.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parametry

*_class*<br/>
podczas Określa klasę obiektu przystawki.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a> EXTENSION_SNAPIN_DATACLASS

Dodaje element członkowski danych do klasy danych rozszerzenia przystawki dla klasy pochodnej **ISnapInItemImpl**.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
podczas Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Tę klasę należy również wprowadzić do mapy klas danych rozszerzenia przystawki. Rozpocznij mapowanie klas danych rozszerzenia przystawki przy użyciu makra [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , Dodaj wpisy dla każdego typu danych rozszerzenia przystawki z makrem [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) i wypełnij mapę za pomocą makra [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a> EXTENSION_SNAPIN_NODEINFO_ENTRY

Dodaje klasę danych rozszerzenia przystawki do mapy klas danych rozszerzenia przystawki.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
podczas Klasa danych rozszerzenia przystawki.

### <a name="remarks"></a>Uwagi

Rozpocznij mapowanie klas danych rozszerzenia przystawki przy użyciu makra [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) , Dodaj wpisy dla każdego typu danych rozszerzenia przystawki z makrem EXTENSION_SNAPIN_NODEINFO_ENTRY i wypełnij mapę za pomocą makra [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a> SNAPINMENUID

To makro służy do deklarowania zasobu menu kontekstowego obiektu przystawki.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikuje menu kontekstowe obiektu przystawki.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a> SNAPINTOOLBARID_ENTRY

To makro służy do wprowadzania identyfikatora paska narzędzi do mapy identyfikatora paska narzędzi obiektu przystawki.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
podczas Identyfikuje formant Toolbar.

### <a name="remarks"></a>Uwagi

Makro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) oznacza początek mapy paska narzędzi. makro [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) oznacza koniec.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
