---
title: Klasa CD2DBitmapBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: 1569039db8c1f85d3091282b55d7eda253444deb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294411"
---
# <a name="cd2dbitmapbrush-class"></a>Klasa CD2DBitmapBrush

Otoka ID2D1BitmapBrush.

## <a name="syntax"></a>Składnia

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Przeciążone. Tworzy obiekt CD2DBitmapBrush z pliku.|
|[CD2DBitmapBrush::~CD2DBitmapBrush](#dtor)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt D2D bitmap pędzla.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DBitmapBrush::Create](#create)|Tworzy CD2DBitmapBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Niszczy obiekt CD2DBitmapBrush. (Przesłania [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DBitmapBrush::Get](#get)|Zwraca ID2D1BitmapBrush interfejsu|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Pobiera źródło mapy bitowej, używającej tego pędzla do malowania|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Pobiera metodę, za pomocą którego pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Pobiera metodę, za pomocą którego pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Pobiera metodę interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Określa źródło mapy bitowej, które korzysta z tego pędzla do malowania|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Określa, jak pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Określa, jak pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Określa tryb interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicjuje obiekt|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Zwraca ID2D1BitmapBrush interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Przechowuje wskaźnik do obiektu CD2DBitmap.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Przechowuje wskaźnik do obiektu ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Mapa bitowa właściwości pędzla.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="dtor"></a>  CD2DBitmapBrush:: ~ CD2DBitmapBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt D2D bitmap pędzla.

```
virtual ~CD2DBitmapBrush();
```

##  <a name="attach"></a>  CD2DBitmapBrush::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush

Tworzy obiekt CD2DBitmapBrush.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*pBitmapBrushProperties*<br/>
Wskaźnik do trybów rozszerzenie i trybu interpolacji pędzla mapy bitowej.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

*uiResID*<br/>
Identyfikatora zasobu zasobu.

*lpszType*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający typ zasobu.

*sizeDest*<br/>
Rozmiar docelowej mapy bitowej.

*lpszImagePath*<br/>
Wskaźnik na ciąg zakończony znakiem null, który zawiera nazwę pliku.

##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit

Inicjuje obiekt

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parametry

*pBitmapBrushProperties*<br/>
Wskaźnik do właściwości pędzla mapy bitowej.

##  <a name="create"></a>  CD2DBitmapBrush::Create

Tworzy CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy

Niszczy obiekt CD2DBitmapBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmapBrush::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DBitmapBrush::Get

Zwraca ID2D1BitmapBrush interfejsu

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap

Pobiera źródło mapy bitowej, używającej tego pędzla do malowania

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu CD2DBitmap lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX

Pobiera metodę, za pomocą którego pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która określa, jak pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej

##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY

Pobiera metodę, za pomocą którego pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która określa, jak pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej

##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode

Pobiera metodę interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Metoda interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe

##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap

Przechowuje wskaźnik do obiektu CD2DBitmap.

```
CD2DBitmap* m_pBitmap;
```

##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush

Przechowuje wskaźnik do obiektu ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties

Mapa bitowa właściwości pędzla.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::operator ID2D1BitmapBrush *

Zwraca ID2D1BitmapBrush interfejsu

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap

Określa źródło mapy bitowej, które korzysta z tego pędzla do malowania

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Źródła mapy bitowej stosowaną do pędzla

##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX

Określa, jak pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parametry

*extendModeX*<br/>
Wartość, która określa, jak pędzla kafelków w poziomie tych obszarów, które wykraczać poza jego mapy bitowej

##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY

Określa, jak pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parametry

*extendModeY*<br/>
Wartość, która określa, jak pędzla kafelków w pionie tych obszarów, które wykraczać poza jego mapy bitowej

##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode

Określa tryb interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parametry

*interpolationMode*<br/>
Tryb interpolacji związanych z mapy bitowej pędzla jest skalowany lub obrócono pionowe

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
