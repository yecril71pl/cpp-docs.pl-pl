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
ms.openlocfilehash: aca9606271040e5c5c9aee81be0a08b64cf2bab7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369129"
---
# <a name="cd2dradialgradientbrush-class"></a>Klasa CD2DRadialGradientBrush

Otoka dla ID2D1RadialGradientBrush.

## <a name="syntax"></a>Składnia

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Konstruuje obiekt CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Wywoływane, gdy obiekt pędzla gradientu promieniowego D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DRadialGradientBrush::Tworzenie](#create)|Tworzy dysk CD2DRadialGradientBrush. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Niszczy CD2DRadialGradientBrush obiektu. (Zastępuje [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DRadialGradientBrush::Get](#get)|Zwraca interfejs ID2D1RadialGradientBrush|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Pobiera środek elips gradientu|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Pobiera przesunięcie początku gradientu względem środka elipsy gradientu|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Pobiera x-promień elipsy gradientu|
|[CD2DRadialGradientBrush::GetRadiusy](#getradiusy)|Pobiera promień y elipsy gradientu|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Określa środek elipsy gradientu w przestrzeni współrzędnych pędzla|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Określa odsunięcie początku gradientu względem środka elipsy gradientu|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla|
|[CD2DRadialGradientBrush::SetRadiusy](#setradiusy)|Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*](#operator_id2d1radialgradientbrush_star)|Zwraca interfejs ID2D1RadialGradientBrush|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Wskaźnik do ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Środek, odsunięcie początku gradientu oraz x-radius i y-radius gradientu pędzla.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[Cd2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush::~CD2DRadialGradientBrush

Destruktor. Wywoływane, gdy obiekt pędzla gradientu promieniowego D2D jest niszczony.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Konstruuje obiekt CD2DLinearGradientBrush.

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
Wskaźnik do obiektu docelowego renderowania.

*gradientStops*<br/>
Wskaźnik do tablicy struktur D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Wartość większa lub równa 1, która określa liczbę przystanków gradientu w gradientStops tablicy.

*Właściwości radialgradientbrushproperties*<br/>
Środek, odsunięcie początku gradientu oraz x-radius i y-radius gradientu pędzla.

*colorInterpolationGamma*<br/>
Miejsce, w którym wykonywana jest interpolacja kolorów między przystankami gradientu.

*extendMode (rozszerzanie trybu)*<br/>
Zachowanie gradientu poza [0,1] znormalizowany zakres.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Tworzenie

Tworzy dysk CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy

Niszczy CD2DRadialGradientBrush obiektu.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Get

Zwraca interfejs ID2D1RadialGradientBrush

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1RadialGradientBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter

Pobiera środek elips gradientu

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Wartość zwracana

Środek elipsy gradientu. Wartość ta jest wyrażona w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset

Pobiera przesunięcie początku gradientu względem środka elipsy gradientu

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Wartość zwracana

Przesunięcie początku gradientu od środka elipsy gradientu. Wartość ta jest wyrażona w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX

Pobiera x-promień elipsy gradientu

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Wartość zwracana

Promień x elipsy gradientu. Wartość ta jest wyrażona w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusy

Pobiera promień y elipsy gradientu

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Wartość zwracana

Promień elipsy gradientu. Wartość ta jest wyrażona w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush

Wskaźnik do ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Środek, odsunięcie początku gradientu oraz x-radius i y-radius gradientu pędzla.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*

Zwraca interfejs ID2D1RadialGradientBrush

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1RadialGradientBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter

Określa środek elipsy gradientu w przestrzeni współrzędnych pędzla

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Środek elipsy gradientu w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset

Określa odsunięcie początku gradientu względem środka elipsy gradientu

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parametry

*gradientOriginOffset*<br/>
Przesunięcie początku gradientu od środka elipsy gradientu

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX

Określa promień x elipsy gradientu w przestrzeni współrzędnych pędzla

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parametry

*promieńX*<br/>
Promień x elipsy gradientu. Ta wartość znajduje się w przestrzeni współrzędnych pędzla

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusy

Określa promień y elipsy gradientu w przestrzeni współrzędnych pędzla

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parametry

*promień*<br/>
Promień elipsy gradientu. Ta wartość znajduje się w przestrzeni współrzędnych pędzla

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
