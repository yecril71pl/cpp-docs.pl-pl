---
title: Makra stanu obiektów
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: cb5ff6d7570b03b32852fc450f58043446f721f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198177"
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

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
