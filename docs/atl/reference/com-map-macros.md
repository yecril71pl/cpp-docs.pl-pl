---
title: Makra mapy modelu COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69838a690fcdddc58194caf38e3666fef023222c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028054"
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

Od ATL [BEEPER](../../visual-cpp-samples.md) próbki:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

Kończy definicję mapy interfejsu COM.

```
END_COM_MAP()
```

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Funkcje globalne mapy interfejsu COM](../../atl/reference/com-map-global-functions.md)
