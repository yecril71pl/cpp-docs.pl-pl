---
title: Funkcje globalne kontekstu urządzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac2e56e4b13f739f61df5b37ab70689784a39882
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077545"
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
