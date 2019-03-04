---
title: Klasa CD2DGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: f49a3a1a1aaebed47b05bf003926379c6f0b8102
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290979"
---
# <a name="cd2dgradientbrush-class"></a>Klasa CD2DGradientBrush

Klasa bazowa CD2DLinearGradientBrush i klasy CD2DRadialGradientBrush.

## <a name="syntax"></a>Składnia

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Tworzy obiekt CD2DGradientBrush.|
|[CD2DGradientBrush::~CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla gradientów D2D.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Niszczy obiekt CD2DGradientBrush. (Przesłania [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Tablica struktury D2D1_GRADIENT_STOP.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|Miejsca, które są oznaczone kolorem odbywa się interpolacji między ograniczniki gradientu.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Zachowanie gradientu poza zakresem [0,1] znormalizowana.|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Wskaźnik do tablicy D2D1_GRADIENT_STOP struktur.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dgradientbrush"></a>  CD2DGradientBrush:: ~ CD2DGradientBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla gradientów D2D.

```
virtual ~CD2DGradientBrush();
```

##  <a name="cd2dgradientbrush"></a>  CD2DGradientBrush::CD2DGradientBrush

Tworzy obiekt CD2DGradientBrush.

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*gradientStops*<br/>
Wskaźnik do tablicy D2D1_GRADIENT_STOP struktur.

*gradientStopsCount*<br/>
Wartość większa niż lub równa 1, która określa liczbę ograniczniki gradientu w tablicy gradientStops.

*colorInterpolationGamma*<br/>
Miejsca, które są oznaczone kolorem odbywa się interpolacji między ograniczniki gradientu.

*extendMode*<br/>
Zachowanie gradientu poza zakresem [0,1] znormalizowana.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="destroy"></a>  CD2DGradientBrush::Destroy

Niszczy obiekt CD2DGradientBrush.

```
virtual void Destroy();
```

##  <a name="m_argradientstops"></a>  CD2DGradientBrush::m_arGradientStops

Tablica struktury D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

##  <a name="m_colorinterpolationgamma"></a>  CD2DGradientBrush::m_colorInterpolationGamma

Miejsca, które są oznaczone kolorem odbywa się interpolacji między ograniczniki gradientu.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

##  <a name="m_extendmode"></a>  CD2DGradientBrush::m_extendMode

Zachowanie gradientu poza zakresem [0,1] znormalizowana.

```
D2D1_EXTEND_MODE m_extendMode;
```

##  <a name="m_pgradientstops"></a>  CD2DGradientBrush::m_pGradientStops

Wskaźnik do tablicy D2D1_GRADIENT_STOP struktur.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
