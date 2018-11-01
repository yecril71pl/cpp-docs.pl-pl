---
title: Klasa CD2DRadialGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: fbdc6e6b9e7ffff1f14da79ed207644b518910fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564336"
---
# <a name="cd2dradialgradientbrush-class"></a>Klasa CD2DRadialGradientBrush

Otoka ID2D1RadialGradientBrush.

## <a name="syntax"></a>Składnia

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Tworzy obiekt CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt RadialGradientBrush D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DRadialGradientBrush::Create](#create)|Tworzy CD2DRadialGradientBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Niszczy obiekt CD2DRadialGradientBrush. (Przesłania [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DRadialGradientBrush::Get](#get)|Zwraca ID2D1RadialGradientBrush interfejsu|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Pobiera środek elipsy gradientu|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Pobiera przesunięcie źródło gradientu względem Centrum elipsy gradientu|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Pobiera promień x elipsy gradientu|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Pobiera promień y elipsy gradientu|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Określa środek gradientu elipsę w przestrzeni współrzędnych pędzla|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Określa przesunięcie źródło gradientu względem Centrum elipsy gradientu|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Zwraca ID2D1RadialGradientBrush interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Wskaźnik do ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Centrum, przesunięcie źródło gradientu i x-radius oraz promień y pędzla użytkownika gradientu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dradialgradientbrush"></a>  CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt RadialGradientBrush D2D.

```
virtual ~CD2DRadialGradientBrush();
```

##  <a name="attach"></a>  CD2DRadialGradientBrush::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush

Tworzy obiekt CD2DLinearGradientBrush.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
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

*RadialGradientBrushProperties*<br/>
Centrum, przesunięcie źródło gradientu i x-radius oraz promień y pędzla użytkownika gradientu.

*colorInterpolationGamma*<br/>
Miejsca, które są oznaczone kolorem odbywa się interpolacji między ograniczniki gradientu.

*extendMode*<br/>
Zachowanie gradientu poza zakresem [0,1] znormalizowana.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DRadialGradientBrush::Create

Tworzy CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy

Niszczy obiekt CD2DRadialGradientBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DRadialGradientBrush::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DRadialGradientBrush::Get

Zwraca ID2D1RadialGradientBrush interfejsu

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1RadialGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter

Pobiera środek elipsy gradientu

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Wartość zwracana

Środek gradientu elipsy. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla

##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset

Pobiera przesunięcie źródło gradientu względem Centrum elipsy gradientu

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Wartość zwracana

Przesunięcie źródło gradientu z Centrum gradientu elipsy. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla

##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX

Pobiera promień x elipsy gradientu

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Wartość zwracana

Promień x elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla

##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY

Pobiera promień y elipsy gradientu

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Wartość zwracana

Promień y elipsy gradientu. Ta wartość jest wyrażona w przestrzeni współrzędnych pędzla

##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush

Wskaźnik do ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Centrum, przesunięcie źródło gradientu i x-radius oraz promień y pędzla użytkownika gradientu.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *

Zwraca ID2D1RadialGradientBrush interfejsu

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1RadialGradientBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter

Określa środek gradientu elipsę w przestrzeni współrzędnych pędzla

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Środek gradientu elipsy, przestrzeni współrzędnych pędzla

##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset

Określa przesunięcie źródło gradientu względem Centrum elipsy gradientu

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parametry

*gradientOriginOffset*<br/>
Przesunięcie źródło gradientu z Centrum elipsy gradientu

##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX

Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parametry

*radiusX*<br/>
Promień x elipsy gradientu. Ta wartość jest przestrzeni współrzędnych pędzla

##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY

Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parametry

*radiusY*<br/>
Promień y elipsy gradientu. Ta wartość jest przestrzeni współrzędnych pędzla

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
