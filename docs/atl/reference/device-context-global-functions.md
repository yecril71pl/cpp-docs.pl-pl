---
title: Funkcje globalne kontekstu urządzenia
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330151"
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia

Ta funkcja tworzy kontekst urządzenia dla danego urządzenia.

|||
|-|-|
|[AtlCreateTargetDC (AtlCreateTargetDC)](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreateTargetDC (AtlCreateTargetDC)

Tworzy kontekst urządzenia dla urządzenia określonego w strukturze [DVTARGETDEVICE.](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
[w] Istniejący uchwyt kontekstu urządzenia lub NULL.

*Ptd*<br/>
[w] Wskaźnik do `DVTARGETDEVICE` struktury, który zawiera informacje o urządzeniu docelowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do kontekstu urządzenia `DVTARGETDEVICE`dla urządzenia określonego w pliku . Jeśli żadne urządzenie nie jest określone, zwraca uchwyt do domyślnego urządzenia wyświetlającego.

### <a name="remarks"></a>Uwagi

Jeśli struktura ma wartość NULL, a *hdc* ma wartość NULL, tworzy kontekst urządzenia dla domyślnego urządzenia wyświetlającego.

Jeśli *hdc* nie ma wartości NULL, a *ptd* ma wartość NULL, funkcja zwraca istniejący *hdc*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
