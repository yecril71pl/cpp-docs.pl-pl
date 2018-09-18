---
title: Makra punktów połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b025e29c93cffe9c600646a2475f7e3230fd03
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039546"
---
# <a name="connection-point-macros"></a>Makra punktów połączenia

Te makra definiują mapy punktu połączenia i wpisy.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Oznacza początek wpisy mapy punktu połączenia.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Wprowadza punkty połączenia w mapie.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Podobnie jak CONNECTION_POINT_ENTRY ale pobiera wskaźnik do identyfikatora iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Oznacza koniec wpisy mapy punktu połączenia.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP

Oznacza początek wpisy mapy punktu połączenia.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy zawierającej punktów połączenia.

### <a name="remarks"></a>Uwagi

Uruchom mapy punktu połączenia z makr BEGIN_CONNECTION_POINT_MAP, dodać wpisy dla wszystkich punktów połączenia z [CONNECTION_POINT_ENTRY](#connection_point_entry) makro i wykonaj mapy za pomocą [END_CONNECTION_ POINT_MAP](#end_connection_point_map) makra.

Aby uzyskać więcej informacji na temat punktów połączenia ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY i CONNECTION_POINT_ENTRY_P

Wprowadza punkt połączenia dla określonego interfejsu w mapie punktu połączenia tak, aby był on dostępny.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu dodawany do mapy punktu połączenia. 

*piid*<br/>
[in] Wskaźnik do interfejsu są adde identyfikatora GUID.

### <a name="remarks"></a>Uwagi

Wpisy punktu połączenia na mapie są używane przez [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). Klasy zawierającej mapy punkt połączenia musi dziedziczyć `IConnectionPointContainerImpl`.

Rozpocznij mapy punktu połączenia z [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makro, dodać wpisy dla wszystkich punktów połączenia za pomocą makra CONNECTION_POINT_ENTRY, a następnie ukończ mapy za pomocą [END_CONNECTION_ POINT_MAP](#end_connection_point_map) makra.

Aby uzyskać więcej informacji na temat punktów połączenia ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP

Oznacza koniec wpisy mapy punktu połączenia.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Uwagi

Rozpocznij mapy punktu połączenia z [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) makro, dodać wpisy dla wszystkich punktów połączenia z [CONNECTION_POINT_ENTRY](#connection_point_entry) makro i ukończyć mapy za pomocą END_ Makro CONNECTION_POINT_MAP.

Aby uzyskać więcej informacji na temat punktów połączenia ATL, zobacz artykuł [punkty połączenia](../../atl/atl-connection-points.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne punktu połączenia](../../atl/reference/connection-point-global-functions.md)
