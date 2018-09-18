---
title: Makra stanu obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b684d66a96a7a3a7d7d60a1b107792c2061ce57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086606"
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
