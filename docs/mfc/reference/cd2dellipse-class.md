---
title: Klasa CD2DEllipse
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369259"
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
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Przeciążone. Konstruuje `CD2DEllipse` obiekt `D2D1_ELLIPSE` z obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse::CD2DEllipse

Konstruuje obiekt CD2DEllipse z obiektu CD2DRectF.

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
prostokąt źródłowy

*ellipse*<br/>
elipsa źródłona

*ptCenter (centrum)*<br/>
Punkt środkowy elipsy.

*rozmiarRadius*<br/>
Promień X i Promień Y elipsy.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
