---
title: Funkcje globalne kontekstu urządzenia
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d2d25660083f074683a3f42f878497ce14a008b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833468"
---
# <a name="device-context-global-functions"></a>Funkcje globalne kontekstu urządzenia

Ta funkcja tworzy kontekst urządzenia dla danego urządzenia.

|Nazwa|Opis|
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Tworzy kontekst urządzenia.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a> AtlCreateTargetDC

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

Zwraca uchwyt do kontekstu urządzenia dla urządzenia określonego w `DVTARGETDEVICE` . Jeśli urządzenie nie zostanie określone, program zwraca dojście do domyślnego urządzenia wyświetlającego.

### <a name="remarks"></a>Uwagi

Jeśli struktura ma wartość NULL, a *używający HDC* ma wartość null, program tworzy kontekst urządzenia dla domyślnego urządzenia wyświetlającego.

Jeśli *używający HDC* nie ma wartości null i *PTD* ma wartość null, funkcja zwraca istniejące *używający HDC*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
