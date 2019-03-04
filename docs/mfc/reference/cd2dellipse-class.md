---
title: Klasa CD2DEllipse
ms.date: 11/04/2016
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 3abf0736884840be7bdcfcd55cb18a0bc8e69195
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270837"
---
# <a name="cd2dellipse-class"></a>Klasa CD2DEllipse

Otoka dla `D2D1_ELLIPSE`.

## <a name="syntax"></a>Składnia

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Przeciążone. Konstruuje `CD2DEllipse` obiektu z `D2D1_ELLIPSE` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

Tworzy obiekt CD2DEllipse z CD2DRectF obiektu.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
prostokąta źródłowego

*ellipse*<br/>
Elipsa źródła

*ptCenter*<br/>
Punktu centralnego elipsy.

*sizeRadius*<br/>
Promień X i Y promień elipsy.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
