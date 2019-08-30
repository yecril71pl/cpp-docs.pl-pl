---
title: Klasa CD2DPointU
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 6289d33aa0672d1ee423d91b11527dccfc868da7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177177"
---
# <a name="cd2dpointu-class"></a>Klasa CD2DPointU

Otoka dla `D2D1_POINT_2U`.

## <a name="syntax"></a>Składnia

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Przeciążone. Konstruuje `D2D1_POINT_2U` obiekt zobiektu.`CD2DPointU`|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointU:: operator CPoint](#operator_cpoint)|Konwertuje `CD2DPointU` na`CPoint` obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget. h

##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU

Konstruuje obiekt CD2DPointU z obiektu CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
punkt źródłowy

*uX*<br/>
Źródło X

*uY*<br/>
Źródło Y

##  <a name="operator_cpoint"></a>CD2DPointU:: operator CPoint

Konwertuje CD2DPointU na obiekt CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość punktu D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
