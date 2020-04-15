---
title: Klasa CD2DLinearGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: 6c488d66962f26b6ca9b8c63cb387fc75191085a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369198"
---
# <a name="cd2dlineargradientbrush-class"></a>Klasa CD2DLinearGradientBrush

Otoka dla ID2D1LinearGradientBrush.

## <a name="syntax"></a>Składnia

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Konstruuje obiekt CD2DLinearGradientBrush.|
|[CD2DLinearGradientBrush::~CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Wywoływany, gdy obiekt pędzla gradientu liniowego D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DLinearGradientBrush::Utwórz](#create)|Tworzy dysk CD2DLinearGradientBrush. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush: :Destroja](#destroy)|Niszczy obiekt CD2DLinearGradientBrush. (Zastępuje [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DLinearGradientBrush::Get](#get)|Zwraca interfejs ID2D1LinearGradientBrush|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Pobiera współrzędne końcowe gradientu liniowego|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Pobiera współrzędne początkowe gradientu liniowego|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Ustawia współrzędne końcowe gradientu liniowego w przestrzeni współrzędnych pędzla|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Ustawia współrzędne początkowe gradientu liniowego w przestrzeni współrzędnych pędzla|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*](#operator_id2d1lineargradientbrush_star)|Zwraca interfejs ID2D1LinearGradientBrush|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Punkty początkowe i końcowe gradientu.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Wskaźnik do pędzla ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[Cd2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush::~CD2DLinearGradientBrush

Destruktor. Wywoływany, gdy obiekt pędzla gradientu liniowego D2D jest niszczony.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush

Konstruuje obiekt CD2DLinearGradientBrush.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*Właściwości lineargradientbrushproperties*<br/>
Punkty początkowe i końcowe gradientu.

*colorInterpolationGamma*<br/>
Miejsce, w którym wykonywana jest interpolacja kolorów między przystankami gradientu.

*extendMode (rozszerzanie trybu)*<br/>
Zachowanie gradientu poza [0,1] znormalizowany zakres.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Utwórz

Tworzy dysk CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush: :Destroja

Niszczy obiekt CD2DLinearGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get

Zwraca interfejs ID2D1LinearGradientBrush

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1LinearGradientBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint

Pobiera współrzędne końcowe gradientu liniowego

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

Końcowe współrzędne dwuwymiarowe gradientu liniowego w przestrzeni współrzędnych pędzla

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint

Pobiera współrzędne początkowe gradientu liniowego

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

Początkowe współrzędne dwuwymiarowe gradientu liniowego w przestrzeni współrzędnych pędzla

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Punkty początkowe i końcowe gradientu.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush

Wskaźnik do pędzla ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*

Zwraca interfejs ID2D1LinearGradientBrush

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1LinearGradientBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint

Ustawia współrzędne końcowe gradientu liniowego w przestrzeni współrzędnych pędzla

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Końcowe współrzędne dwuwymiarowe gradientu liniowego w przestrzeni współrzędnych pędzla

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint

Ustawia współrzędne początkowe gradientu liniowego w przestrzeni współrzędnych pędzla

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Początkowe współrzędne dwuwymiarowe gradientu liniowego w przestrzeni współrzędnych pędzla

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
