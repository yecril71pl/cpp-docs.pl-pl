---
title: Klasa CD2DPointF
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 7b9f6634e4b5980d8318557a8822549d226910b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559110"
---
# <a name="cd2dpointf-class"></a>Klasa CD2DPointF

Otoka dla `D2D1_POINT_2F`.

## <a name="syntax"></a>Składnia

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Przeciążone. Konstruuje `CD2DPointF` obiektu z `D2D1_POINT_2F` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|Konwertuje `CD2DPointF` do `CPoint` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

Tworzy obiekt CD2DPointF z CPoint obiektu.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
źródłowy punkt

*fX*<br/>
Źródło X

*Ro*<br/>
Źródło Y

##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint

Konwertuje CD2DPointF CPoint obiektu.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość punktu D2D.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
