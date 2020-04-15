---
title: Makra map COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326602"
---
# <a name="com-map-macros"></a>Makra map COM

Te makra definiują mapy interfejsu COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Oznacza początek wpisów mapy interfejsu COM.|
|[END_COM_MAP](#end_com_map)|Oznacza koniec wpisów mapy interfejsu COM.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

Mapa COM to mechanizm, który udostępnia interfejsy obiektu `QueryInterface`klientowi za pośrednictwem .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa obiektu klasy, na który są uwidacznianie interfejsów.

### <a name="remarks"></a>Uwagi

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) zwraca tylko wskaźniki dla interfejsów na mapie COM. Uruchom mapę interfejsu BEGIN_COM_MAP makra, dodaj wpisy dla każdego interfejsu z [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) makra lub jednego z jego wariantów i uzupełnij mapę [END_COM_MAP](#end_com_map) makra.

### <a name="example"></a>Przykład

Z próbki ATL [BEEPER:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

Kończy definicję mapy interfejsu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne map com map](../../atl/reference/com-map-global-functions.md)
