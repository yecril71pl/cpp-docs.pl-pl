---
title: Makra punktów połączenia
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 6c716ad85ecb458b4be418a7e8554687dd19f3d8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833520"
---
# <a name="connection-point-macros"></a>Makra punktów połączenia

Te makra definiują mapy punktów połączenia i wpisy.

|Makro|Opis|
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Oznacza początek wpisów mapy punktu połączenia.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Wprowadza punkty połączenia do mapy.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobnie jak CONNECTION_POINT_ENTRY, ale Pobiera wskaźnik do IID.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Oznacza koniec wpisów mapy punktu połączenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a> BEGIN_CONNECTION_POINT_MAP

Oznacza początek wpisów mapy punktu połączenia.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy zawierającej punkty połączenia.

### <a name="remarks"></a>Uwagi

Uruchom mapę punktu połączenia za pomocą makra BEGIN_CONNECTION_POINT_MAP, Dodaj wpisy dla każdego z punktów połączenia z makrem [CONNECTION_POINT_ENTRY](#connection_point_entry) i wypełnij mapę za pomocą makra [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a> CONNECTION_POINT_ENTRY i CONNECTION_POINT_ENTRY_P

Wprowadza punkt połączenia dla określonego interfejsu do mapy punktów połączenia, aby można było uzyskać do niego dostęp.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID interfejsu dodawanego do mapy punktu połączenia.

*piid*<br/>
podczas Wskaźnik na identyfikator GUID interfejsu, który jest ADDE.

### <a name="remarks"></a>Uwagi

Wpisy punktu połączenia w mapie są używane przez [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Klasa zawierająca mapę punktu połączenia musi dziedziczyć po elemencie `IConnectionPointContainerImpl` .

Uruchom mapę punktu połączenia za pomocą makra [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , Dodaj wpisy dla każdego z punktów połączenia z makrem CONNECTION_POINT_ENTRY i wypełnij mapę za pomocą makra [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a> END_CONNECTION_POINT_MAP

Oznacza koniec wpisów mapy punktu połączenia.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Uwagi

Uruchom mapę punktu połączenia za pomocą makra [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , Dodaj wpisy dla każdego z punktów połączenia z makrem [CONNECTION_POINT_ENTRY](#connection_point_entry) i wypełnij mapę za pomocą makra END_CONNECTION_POINT_MAP.

Aby uzyskać więcej informacji na temat punktów połączenia w ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne punktu połączenia](../../atl/reference/connection-point-global-functions.md)
