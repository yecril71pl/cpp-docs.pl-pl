---
title: Makra punktu połączenia
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331494"
---
# <a name="connection-point-macros"></a>Makra punktu połączenia

Te makra definiują mapy i wpisy punktów połączenia.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Oznacza początek wpisów mapy punktu połączenia.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Wprowadza punkty połączenia do mapy.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobne do CONNECTION_POINT_ENTRY ale ma wskaźnik do iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Oznacza koniec wpisów mapy punktu połączenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Oznacza początek wpisów mapy punktu połączenia.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy zawierającej punkty połączenia.

### <a name="remarks"></a>Uwagi

Rozpocznij mapę punktu połączenia od makra BEGIN_CONNECTION_POINT_MAP, dodaj wpisy dla każdego punktu połączenia do [makra CONNECTION_POINT_ENTRY](#connection_point_entry) i uzupełnij mapę [END_CONNECTION_POINT_MAP](#end_connection_point_map) makra.

Aby uzyskać więcej informacji o punktach połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY i CONNECTION_POINT_ENTRY_P

Wprowadza punkt połączenia dla określonego interfejsu do mapy punktu połączenia, dzięki czemu można uzyskać do niego dostęp.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID interfejsu dodawany do mapy punktu połączenia.

*piid*<br/>
[w] Wskaźnik do identyfikatora GUID interfejsu jest adde.

### <a name="remarks"></a>Uwagi

Wpisy punktu połączenia na mapie są używane przez [iConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Klasa zawierająca mapę punktu połączenia `IConnectionPointContainerImpl`musi dziedziczyć z .

Rozpocznij mapę punktu połączenia od [makra BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) dodaj wpisy dla każdego punktu połączenia do makra CONNECTION_POINT_ENTRY i uzupełnij mapę [END_CONNECTION_POINT_MAP](#end_connection_point_map) makra.

Aby uzyskać więcej informacji o punktach połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Oznacza koniec wpisów mapy punktu połączenia.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Uwagi

Rozpocznij mapę punktu połączenia od [makra BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) dodaj wpisy dla każdego punktu połączenia do [makra CONNECTION_POINT_ENTRY](#connection_point_entry) i uzupełnij mapę END_CONNECTION_POINT_MAP makrą.

Aby uzyskać więcej informacji o punktach połączenia w atl, zobacz artykuł [Punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne punktu połączenia](../../atl/reference/connection-point-global-functions.md)
