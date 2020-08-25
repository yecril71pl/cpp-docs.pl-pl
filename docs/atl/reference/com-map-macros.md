---
title: Makra mapy modelu COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 100402e17ca1bee5f338c37f2315fbc4898a713e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833585"
---
# <a name="com-map-macros"></a>Makra mapy modelu COM

Te makra definiują mapy interfejsów COM.

|Makro|Opis|
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Oznacza początek wpisów mapy interfejsu COM.|
|[END_COM_MAP](#end_com_map)|Oznacza koniec wpisów mapy interfejsu COM.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="begin_com_map"></a><a name="begin_com_map"></a> BEGIN_COM_MAP

Mapa COM jest mechanizmem, który uwidacznia interfejsy na obiekcie dla klienta za pomocą programu `QueryInterface` .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa obiektu klasy, na którym są ujawniane interfejsy.

### <a name="remarks"></a>Uwagi

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) zwraca tylko wskaźniki dla interfejsów w mapie com. Rozpocznij mapowanie interfejsu za pomocą makra BEGIN_COM_MAP, Dodaj wpisy dla każdego z interfejsów przy użyciu makra [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) lub jednego z jego wariantów i wypełnij mapę za pomocą makra [END_COM_MAP](#end_com_map) .

### <a name="example"></a>Przykład

Z przykładu [sygnału dźwiękowego](../../overview/visual-cpp-samples.md) ATL:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a> END_COM_MAP

Zamyka definicję mapy interfejsu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globalne funkcje mapowania modelu COM](../../atl/reference/com-map-global-functions.md)
