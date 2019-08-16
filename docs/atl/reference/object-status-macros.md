---
title: Makra stanu obiektu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: dc50825d6b6e74dc263a097e86d8ea0d42989825
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495319"
---
# <a name="object-status-macros"></a>Makra stanu obiektu

To makro ustawia flagi należące do kontrolek ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Używane w kontrolkach ActiveX ATL do ustawiania flag OLEMISC.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Używane w kontrolkach ActiveX ATL do ustawiania flag OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*miscstatus*<br/>
Wszystkie odpowiednie flagi OLEMISC.

### <a name="remarks"></a>Uwagi

To makro służy do ustawiania flag OLEMISC dla kontrolki ActiveX. Aby uzyskać więcej informacji, zobacz [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
