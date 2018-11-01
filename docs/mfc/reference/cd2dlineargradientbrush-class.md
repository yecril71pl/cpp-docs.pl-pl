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
ms.openlocfilehash: 03c370be5bcfc61e1dd398604f27313d3de15f8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635828"
---
# <a name="cd2dlineargradientbrush-class"></a>Klasa CD2DLinearGradientBrush

Otoka ID2D1LinearGradientBrush.

## <a name="syntax"></a>Składnia

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Tworzy obiekt CD2DLinearGradientBrush.|
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt LinearGradientBrush D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DLinearGradientBrush::Create](#create)|Tworzy CD2DLinearGradientBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Niszczy obiekt CD2DLinearGradientBrush. (Przesłania [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DLinearGradientBrush::Get](#get)|Zwraca ID2D1LinearGradientBrush interfejsu|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Pobiera końcowy współrzędne gradientu liniowego|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Pobiera początkowy współrzędne gradientu liniowego|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Ustawia współrzędne końcowy gradientu liniowego w przestrzeni współrzędnych pędzla|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Ustawia współrzędne początkowy gradientu liniowego w przestrzeni współrzędnych pędzla|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|Zwraca ID2D1LinearGradientBrush interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Punkt początkowy i końcowy gradientu.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Wskaźnik do ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dlineargradientbrush"></a>  CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt LinearGradientBrush D2D.

```
virtual ~CD2DLinearGradientBrush();
```

##  <a name="attach"></a>  CD2DLinearGradientBrush::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::CD2DLinearGradientBrush

Tworzy obiekt CD2DLinearGradientBrush.

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
Wskaźnik do elementu docelowego renderowania.

*gradientStops*<br/>
Wskaźnik do tablicy D2D1_GRADIENT_STOP struktur.

*gradientStopsCount*<br/>
Wartość większa niż lub równa 1, która określa liczbę ograniczniki gradientu w tablicy gradientStops.

*LinearGradientBrushProperties*<br/>
Punkt początkowy i końcowy gradientu.

*colorInterpolationGamma*<br/>
Miejsca, które są oznaczone kolorem odbywa się interpolacji między ograniczniki gradientu.

*extendMode*<br/>
Zachowanie gradientu poza zakresem [0,1] znormalizowana.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DLinearGradientBrush::Create

Tworzy CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DLinearGradientBrush::Destroy

Niszczy obiekt CD2DLinearGradientBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLinearGradientBrush::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DLinearGradientBrush::Get

Zwraca ID2D1LinearGradientBrush interfejsu

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1LinearGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getendpoint"></a>  CD2DLinearGradientBrush::GetEndPoint

Pobiera końcowy współrzędne gradientu liniowego

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

Końcowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla

##  <a name="getstartpoint"></a>  CD2DLinearGradientBrush::GetStartPoint

Pobiera początkowy współrzędne gradientu liniowego

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

Począwszy od dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla

##  <a name="m_lineargradientbrushproperties"></a>  CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Punkt początkowy i końcowy gradientu.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

##  <a name="m_plineargradientbrush"></a>  CD2DLinearGradientBrush::m_pLinearGradientBrush

Wskaźnik do ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

##  <a name="operator_id2d1lineargradientbrush_star"></a>  CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *

Zwraca ID2D1LinearGradientBrush interfejsu

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1LinearGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setendpoint"></a>  CD2DLinearGradientBrush::SetEndPoint

Ustawia współrzędne końcowy gradientu liniowego w przestrzeni współrzędnych pędzla

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Końcowy dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla

##  <a name="setstartpoint"></a>  CD2DLinearGradientBrush::SetStartPoint

Ustawia współrzędne początkowy gradientu liniowego w przestrzeni współrzędnych pędzla

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Począwszy od dwuwymiarowe współrzędne gradientu liniowego w przestrzeni współrzędnych pędzla

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
