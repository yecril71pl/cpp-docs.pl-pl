---
title: CD2DSolidColorBrush Class
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: f225198193443c11d0294010a5fb71858514c81e
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565415"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush Class

Otoka ID2D1SolidColorBrush.

## <a name="syntax"></a>Składnia

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Przeciążone. Tworzy obiekt CD2DSolidColorBrush.|
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::Attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DSolidColorBrush::Create](#create)|Tworzy CD2DSolidColorBrush. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Niszczy obiekt CD2DSolidColorBrush. (Przesłania [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DSolidColorBrush::Get](#get)|Zwraca ID2D1SolidColorBrush interfejsu|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Pobiera kolor pędzel pełnego koloru|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Określa kolor tego pędzel pełnego koloru|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Zwraca ID2D1SolidColorBrush interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pełny kolor pędzla.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Przechowuje wskaźnik do obiektu ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::~CD2DSolidColorBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla D2D.

```
virtual ~CD2DSolidColorBrush();
```

##  <a name="attach"></a>  CD2DSolidColorBrush::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::CD2DSolidColorBrush

Tworzy obiekt CD2DSolidColorBrush.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*Kolor*<br/>
Wartości czerwony, zielony, niebieski i alfa kolor pędzla.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

*nAlpha*<br/>
Nieprzezroczystość kolor pędzla.

##  <a name="create"></a>  CD2DSolidColorBrush::Create

Tworzy CD2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DSolidColorBrush::Destroy

Niszczy obiekt CD2DSolidColorBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DSolidColorBrush::Detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DSolidColorBrush::Get

Zwraca ID2D1SolidColorBrush interfejsu

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1SolidColorBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getcolor"></a>  CD2DSolidColorBrush::GetColor

Pobiera kolor pędzel pełnego koloru

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor ten pędzel pełnego koloru

##  <a name="m_colorsolid"></a>  CD2DSolidColorBrush::m_colorSolid

Pełny kolor pędzla.

```
D2D1_COLOR_F m_colorSolid;
```

##  <a name="m_psolidcolorbrush"></a>  CD2DSolidColorBrush::m_pSolidColorBrush

Przechowuje wskaźnik do obiektu ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

##  <a name="operator_id2d1solidcolorbrush_star"></a>  CD2DSolidColorBrush::operator ID2D1SolidColorBrush *

Zwraca ID2D1SolidColorBrush interfejsu

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1SolidColorBrush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setcolor"></a>  CD2DSolidColorBrush::SetColor

Określa kolor tego pędzel pełnego koloru

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Kolor ten pędzel pełnego koloru

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
