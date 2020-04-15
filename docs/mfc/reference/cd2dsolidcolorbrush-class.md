---
title: Klasa CD2DSolidColorBrush
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
ms.openlocfilehash: 5aa3d7688046b0c1b04983f2d27fe5579dd7c680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369056"
---
# <a name="cd2dsolidcolorbrush-class"></a>Klasa CD2DSolidColorBrush

Otoka dla ID2D1SolidColorBrush.

## <a name="syntax"></a>Składnia

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Przeciążone. Konstruuje obiekt CD2DSolidColorBrush.|
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|Destruktor. Wywoływane, gdy obiekt pędzla bryłowego D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DSolidColorBrush::Tworzenie](#create)|Tworzy cd2DSolidColorBrush. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Niszczy CD2DSolidColorBrush obiektu. (Zastępuje [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DSolidColorBrush::Get](#get)|Zwraca interfejs ID2D1SolidColorBrush|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Pobiera kolor pędzla jednolitego koloru|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Określa kolor tego pędzla z jednolitym kolorem|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush*](#operator_id2d1solidcolorbrush_star)|Zwraca interfejs ID2D1SolidColorBrush|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pędzel jednolity kolor.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Przechowuje wskaźnik do ID2D1SolidColorBrush obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

[Cd2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2DSolidColorBrush::~CD2DSolidColorBrush

Destruktor. Wywoływane, gdy obiekt pędzla bryłowego D2D jest niszczony.

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2DSolidColorBrush::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2DSolidColorBrush::CD2DSolidColorBrush

Konstruuje obiekt CD2DSolidColorBrush.

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
Wskaźnik do obiektu docelowego renderowania.

*color*<br/>
Wartości koloru pędzla na czerwono, zielono, niebiesko i alfa.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

*nAlpha (własówce)*<br/>
Krycie koloru pędzla.

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2DSolidColorBrush::Tworzenie

Tworzy cd2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2DSolidColorBrush::Destroy

Niszczy CD2DSolidColorBrush obiektu.

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2DSolidColorBrush::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2DSolidColorBrush::Get

Zwraca interfejs ID2D1SolidColorBrush

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1SolidColorBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2DSolidColorBrush::GetColor

Pobiera kolor pędzla jednolitego koloru

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Kolor tego pędzla jednolitego koloru

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid

Pędzel jednolity kolor.

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush

Przechowuje wskaźnik do ID2D1SolidColorBrush obiektu.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::operator ID2D1SolidColorBrush*

Zwraca interfejs ID2D1SolidColorBrush

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1SolidColorBrush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2DSolidColorBrush::SetColor

Określa kolor tego pędzla z jednolitym kolorem

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Kolor tego pędzla jednolitego koloru

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
