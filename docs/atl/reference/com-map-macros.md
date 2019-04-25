---
title: Makra mapy modelu COM
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245624"
---
# <a name="com-map-macros"></a>Makra mapy modelu COM

Te makra definiują mapy interfejsu COM.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Oznacza początek wpisy mapy interfejsu COM.|
|[END_COM_MAP](#end_com_map)|Oznacza koniec wpisy mapy interfejsu COM.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

Mapy interfejsu COM to mechanizm, który uwidacznia interfejsy na obiekt, do klienta za pośrednictwem `QueryInterface`.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa obiektu klasy, które wyświetlasz interfejsów znajduje się na.

### <a name="remarks"></a>Uwagi

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) zwraca tylko wskaźników dla interfejsów mapy interfejsu COM. Rozpoczynać mapie interfejsu makro BEGIN_COM_MAP, dodać wpisy dla wszystkich interfejsów sieci za pomocą [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) — makro lub jedna z jej wariantów i ukończyć mapy za pomocą [END_COM_MAP](#end_com_map) makra.

### <a name="example"></a>Przykład

Od ATL [BEEPER](../../overview/visual-cpp-samples.md) próbki:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

Kończy definicję mapy interfejsu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne mapy interfejsu COM](../../atl/reference/com-map-global-functions.md)
