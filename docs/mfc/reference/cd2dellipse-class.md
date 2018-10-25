---
title: Klasa CD2DEllipse | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
dev_langs:
- C++
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93fc2b788d450b591ebd20be49f25133c95f22b6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052858"
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

*Elipsa*<br/>
Elipsa źródła

*ptCenter*<br/>
Punktu centralnego elipsy.

*sizeRadius*<br/>
Promień X i Y promień elipsy.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
