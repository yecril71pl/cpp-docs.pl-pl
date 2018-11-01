---
title: Klasa CD2DBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 9e0be4b3b4f39d8fcf32f713bc8765d1f344babe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517887"
---
# <a name="cd2dbrush-class"></a>Klasa CD2DBrush

Otoka ID2D1Brush.

## <a name="syntax"></a>Składnia

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Tworzy obiekt CD2DBrush.|
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DBrush::Destroy](#destroy)|Niszczy obiekt CD2DBrush. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DBrush::Get](#get)|Zwraca ID2D1Brush interfejsu|
|[CD2DBrush::GetOpacity](#getopacity)|Pobiera stopień nieprzezroczystości to pędzla|
|[CD2DBrush::GetTransform](#gettransform)|Pobiera bieżący przekształcenie obiektu docelowego renderowania|
|[CD2DBrush::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Ustawia maksymalny stopień krycia to pędzla|
|[CD2DBrush::SetTransform](#settransform)|Stosuje określony przekształcenie do elementu docelowego renderowania, zastępując istniejące transformacji. Wszystkie kolejne operacje rysowania występują w obszaru przekształconych|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush *](#operator_id2d1brush_star)|Zwraca ID2D1Brush interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Przechowuje wskaźnik do obiektu ID2D1Brush.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Właściwości pędzla.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dbrush"></a>  CD2DBrush:: ~ CD2DBrush

Destruktor. Wywołuje się, kiedy niszczony jest obiekt pędzla D2D.

```
virtual ~CD2DBrush();
```

##  <a name="attach"></a>  CD2DBrush::attach

Dołącza istniejących zasobów interfejsu do obiektu.

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL.

##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush

Tworzy obiekt CD2DBrush.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*pBrushProperties*<br/>
Wskaźnik do nieprzezroczystość i przekształcanie pędzla.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="destroy"></a>  CD2DBrush::Destroy

Niszczy obiekt CD2DBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBrush::detach

Odłącza interfejsu zasobów z obiektu.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DBrush::Get

Zwraca ID2D1Brush interfejsu

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Brush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getopacity"></a>  CD2DBrush::GetOpacity

Pobiera stopień nieprzezroczystości to pędzla

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość z zakresu od 0 do 1, która wskazuje przezroczystość pędzla. Ta wartość jest stałe mnożnik liniowo skalowanej wartość alfa wszystkie piksele uzupełnione przez pędzla. Wartość nieprzezroczystości są zablokowane za pomocą w zakresie od 0 do 1 przed są mnożone ze sobą.

##  <a name="gettransform"></a>  CD2DBrush::GetTransform

Pobiera bieżący przekształcenie obiektu docelowego renderowania

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parametry

*transform*<br/>
Gdy zostanie zwrócona, zawiera przekształcenie bieżącego obiektu docelowego renderowania. Ten parametr jest przekazywany niezainicjowany.

##  <a name="isvalid"></a>  CD2DBrush::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush

Przechowuje wskaźnik do obiektu ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties

Właściwości pędzla.

```
CD2DBrushProperties* m_pBrushProperties;
```

##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::operator ID2D1Brush *

Zwraca ID2D1Brush interfejsu

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Brush lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="setopacity"></a>  CD2DBrush::SetOpacity

Ustawia maksymalny stopień krycia to pędzla

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parametry

*Nieprzezroczystość*<br/>
Wartość z zakresu od 0 do 1, która wskazuje przezroczystość pędzla. Ta wartość jest stałe mnożnik liniowo skalowanej wartość alfa wszystkie piksele uzupełnione przez pędzla. Wartość nieprzezroczystości są zablokowane za pomocą w zakresie od 0 do 1 przed są mnożone ze sobą.

##  <a name="settransform"></a>  CD2DBrush::SetTransform

Stosuje określony przekształcenie do elementu docelowego renderowania, zastępując istniejące transformacji. Wszystkie kolejne operacje rysowania występują w obszaru przekształconych.

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parametry

*transform*<br/>
Przekształcenie do zastosowania do elementu docelowego renderowania

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
