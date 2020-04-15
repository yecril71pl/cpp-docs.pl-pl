---
title: Makra stanu obiektu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326179"
---
# <a name="object-status-macros"></a>Makra stanu obiektu

To makro ustawia flagi należące do formantów ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Używane w formanty ATL ActiveX, aby ustawić flagi OLEMISC.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Używane w formanty ATL ActiveX, aby ustawić flagi OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*miscstatus*<br/>
Wszystkie obowiązujące flagi OLEMISC.

### <a name="remarks"></a>Uwagi

To makro służy do ustawiania flag OLEMISC dla formantu ActiveX. Więcej informacji można znaleźć w [pliku IOleObject::GetMiscStatus.](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
