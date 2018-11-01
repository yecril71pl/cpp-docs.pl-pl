---
title: Makra stanu obiektów
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 9c4df80b2b9828077ec3738bc296f19aadf2df68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658955"
---
# <a name="object-status-macros"></a>Makra stanu obiektów

To makro ustawia flagi należących do kontrolki ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Używane w kontrolkach ActiveX biblioteki ATL, można ustawić flagi OLEMISC.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

Używane w kontrolkach ActiveX biblioteki ATL, można ustawić flagi OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*miscstatus*<br/>
Wszystkich odpowiednich OLEMISC flagi.

### <a name="remarks"></a>Uwagi

To makro jest używane do ustawiania flagi OLEMISC dla formantu ActiveX. Zapoznaj się [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) Aby uzyskać więcej informacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
