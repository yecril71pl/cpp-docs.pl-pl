---
title: Funkcje globalne kontekstu urządzenia
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: 25ceae897d3cc845ab06fd4d898c87518b15eacb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551206"
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia

Ta funkcja tworzy kontekst urządzenia dla danego urządzenia.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Tworzy kontekst urządzenia dla urządzenia określonego w [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) struktury.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*elementu hdc*<br/>
[in] Istniejący uchwyt kontekstu urządzenia, lub wartość NULL.

*ptd*<br/>
[in] Wskaźnik do `DVTARGETDEVICE` strukturę, która zawiera informacje o urządzeniu docelowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt kontekst urządzenia dla urządzenia określonego w `DVTARGETDEVICE`. Jeśli urządzenie nie zostanie określona, zwraca uchwyt do domyślnego ekranu urządzenia.

### <a name="remarks"></a>Uwagi

Jeśli struktura ma wartość NULL i *elementu hdc* ma wartość NULL, tworzy kontekst urządzenia dla urządzenia wyświetlającego domyślne.

Jeśli *elementu hdc* nie ma wartości NULL i *ptd* ma wartość NULL, funkcja zwraca istniejące *elementu hdc*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
