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
ms.openlocfilehash: 8e5c22fe15ce0d930f81dd16673927d5299bf630
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396278"
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
|[CD2DRectF::CD2DRectF](#cd2drectf)|Przeciążone. Konstruuje `CD2DRectF` obiektu z `D2D1_RECT_F` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Zwraca **logiczna** wartość, która wskazuje, czy wyrażenie nie zawiera żadnych prawidłowych danych (NULL).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRectF::operator CRect](#operator_crect)|Konwertuje `CD2DRectF` do `CRect` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

Tworzy obiekt CD2DRectF z CRect obiektu.

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

*Rect*<br/>
prostokąta źródłowego

*fLeft*<br/>
Współrzędna lewej źródła

*fTop*<br/>
współrzędne źródła

*fRight*<br/>
Źródło bezpośrednio współrzędnych

*fBottom*<br/>
Współrzędna dolnej źródła

##  <a name="isnull"></a>  CD2DRectF::IsNull

Zwraca wartość logiczną wskazującą, czy wyrażenie nie zawiera żadnych prawidłowych danych (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli góry prostokąta, po lewej stronie, dolnej i odpowiednie wartości są równe 0; w przeciwnym razie wartość FALSE.

##  <a name="operator_crect"></a>  CD2DRectF::operator CRect

Konwertuje CD2DRectF CRect obiektu.

```
operator CRect();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta D2D.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
