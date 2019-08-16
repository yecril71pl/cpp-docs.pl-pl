---
title: Funkcje globalne kontekstu urządzenia
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496097"
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia

Ta funkcja tworzy kontekst urządzenia dla danego urządzenia.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|

##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Tworzy kontekst urządzenia dla urządzenia określonego w strukturze [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) .

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*używający HDC*<br/>
podczas Istniejące dojście kontekstu urządzenia lub wartość NULL.

*ptd*<br/>
podczas Wskaźnik do `DVTARGETDEVICE` struktury zawierającej informacje o urządzeniu docelowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do kontekstu urządzenia dla urządzenia określonego w `DVTARGETDEVICE`. Jeśli urządzenie nie zostanie określone, program zwraca dojście do domyślnego urządzenia wyświetlającego.

### <a name="remarks"></a>Uwagi

Jeśli struktura ma wartość NULL, a *używający HDC* ma wartość null, program tworzy kontekst urządzenia dla domyślnego urządzenia wyświetlającego.

Jeśli *używający HDC* nie ma wartości null i *PTD* ma wartość null, funkcja zwraca istniejące *używający HDC*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)
