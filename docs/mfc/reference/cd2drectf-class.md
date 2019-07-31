---
title: Klasa CD2DRectF
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682401"
---
# <a name="cd2drectf-class"></a>Klasa CD2DRectF

Otoka dla `D2D1_RECT_F`.

## <a name="syntax"></a>Składnia

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Przeciążone. Konstruuje `D2D1_RECT_F` obiekt z obiektu. `CD2DRectF`|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF:: IsNull](#isnull)|Zwraca wartość **logiczną** wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|Konwertuje `CD2DRectF` na`CRect` obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget. h

##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF

Konstruuje obiekt CD2DRectF z obiektu CRect.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
prostokąt źródłowy

*fLeft*<br/>
lewa Współrzędna źródła

*fTop*<br/>
Górna Współrzędna źródła

*fRight*<br/>
Współrzędna prawej strony źródłowej

*fBottom*<br/>
Dolna współrzędna źródła

##  <a name="isnull"></a>CD2DRectF:: IsNull

Zwraca wartość logiczną wskazującą, czy wyrażenie nie zawiera prawidłowych danych (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli górny, lewy, dolny i prawy wartości są równe 0; w przeciwnym razie FALSE.

##  <a name="operator_crect"></a>CD2DRectF:: operator CRect

Konwertuje CD2DRectF na obiekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
