---
title: Klasa CD2DGradientBrush
ms.date: 03/27/2019
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
ms.openlocfilehash: 861bc32382737bd6482a3d51eb8470bf834e8508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369228"
---
# <a name="cd2dgradientbrush-class"></a>Klasa CD2DGradientBrush

Klasa podstawowa cd2dlineargradientbrush i CD2DRadialGradientBrush klasy.

## <a name="syntax"></a>Składnia

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Konstruuje obiekt CD2DGradientBrush.|
|[CD2DGradientBrush::~CD2DGradientBrush](#_dtorcd2dgradientbrush)|Destruktor. Wywoływane, gdy obiekt pędzla gradientu D2D jest niszczony.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Niszczy obiekt CD2DGradientBrush. (Zastępuje [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Tablica struktur D2D1_GRADIENT_STOP.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|Miejsce, w którym wykonywana jest interpolacja kolorów między przystankami gradientu.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Zachowanie gradientu poza [0,1] znormalizowany zakres.|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Wskaźnik do tablicy struktur D2D1_GRADIENT_STOP.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[Cd2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a>CD2DGradientBrush::~CD2DGradientBrush

Destruktor. Wywoływane, gdy obiekt pędzla gradientu D2D jest niszczony.

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a>CD2DGradientBrush::CD2DGradientBrush

Konstruuje obiekt CD2DGradientBrush.

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
Wskaźnik do obiektu docelowego renderowania.

*gradientStops*<br/>
Wskaźnik do tablicy struktur D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Wartość większa lub równa 1, która określa liczbę przystanków gradientu w gradientStops tablicy.

*colorInterpolationGamma*<br/>
Miejsce, w którym wykonywana jest interpolacja kolorów między przystankami gradientu.

*extendMode (rozszerzanie trybu)*<br/>
Zachowanie gradientu poza [0,1] znormalizowany zakres.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a>CD2DGradientBrush::Destroy

Niszczy obiekt CD2DGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a>CD2DGradientBrush::m_arGradientStops

Tablica struktur D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a>CD2DGradientBrush::m_colorInterpolationGamma

Miejsce, w którym wykonywana jest interpolacja kolorów między przystankami gradientu.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a>CD2DGradientBrush::m_extendMode

Zachowanie gradientu poza [0,1] znormalizowany zakres.

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a>CD2DGradientBrush::m_pGradientStops

Wskaźnik do tablicy struktur D2D1_GRADIENT_STOP.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
