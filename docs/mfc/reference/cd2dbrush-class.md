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
ms.openlocfilehash: 536d84fe2c2f68d62490e1ce2b65085426762e87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754196"
---
# <a name="cd2dbrush-class"></a>Klasa CD2DBrush

Otoka dla ID2D1Brush.

## <a name="syntax"></a>Składnia

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Konstruuje obiekt CD2DBrush.|
|[CD2DBrush::~CD2DBrush](#_dtorcd2dbrush)|Destruktor. Wywoływane, gdy obiekt pędzla D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DBrush::Destroy](#destroy)|Niszczy obiekt CD2DBrush. (Zastępuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBrush::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DBrush::Pobierz](#get)|Zwraca interfejs ID2D1Brush|
|[CD2DBrush::GetOpacity](#getopacity)|Pobiera stopień krycia tego pędzla|
|[CD2DBrush::GetTransform](#gettransform)|Pobiera bieżące przekształcenie obiektu docelowego renderowania|
|[CD2DBrush::IsValid](#isvalid)|Sprawdza ważność zasobu (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DBrush::SetOpacity](#setopacity)|Ustawia stopień krycia tego pędzla|
|[CD2DBrush::SetTransform](#settransform)|Stosuje określone przekształcenie do obiektu docelowego renderowania, zastępując istniejącą transformację. Wszystkie kolejne operacje rysowania występują w przekształconym miejscu|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush*](#operator_id2d1brush_star)|Zwraca interfejs ID2D1Brush|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|Przechowuje wskaźnik do obiektu ID2D1Brush.|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Właściwości pędzla.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush::~CD2DBrush

Destruktor. Wywoływane, gdy obiekt pędzla D2D jest niszczony.

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush::Dołącz

Dołącza istniejący interfejs zasobów do obiektu.

```cpp
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null.

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush::CD2DBrush

Konstruuje obiekt CD2DBrush.

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*pBrushWłaściwki*<br/>
Wskaźnik do krycia i przekształcenia pędzla.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::Destroy

Niszczy obiekt CD2DBrush.

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::Detach

Odłącza interfejs zasobu od obiektu.

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush::Pobierz

Zwraca interfejs ID2D1Brush

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Brush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush::GetOpacity

Pobiera stopień krycia tego pędzla

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość od zera do 1, która wskazuje krycie pędzla. Ta wartość jest stałym mnożnikiem, który liniowo skaluje wartość alfa wszystkich pikseli wypełnionych pędzlem. Wartości krycia są zaciśnięte w zakresie od 0 do 1, zanim zostaną pomnożone razem.

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush::GetTransform

Pobiera bieżące przekształcenie obiektu docelowego renderowania

```cpp
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>Parametry

*Przekształcić*<br/>
Po zwróceniu tego zawiera bieżące przekształcenie obiektu docelowego renderowania. Ten parametr jest przekazywany jako niezainicjowany.

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush::IsValid

Sprawdza ważność zasobu

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush::m_pBrush

Przechowuje wskaźnik do obiektu ID2D1Brush.

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush::m_pBrushProperties

Właściwości pędzla.

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::operator ID2D1Brush*

Zwraca interfejs ID2D1Brush

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Brush lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush::SetOpacity

Ustawia stopień krycia tego pędzla

```cpp
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>Parametry

*Krycie*<br/>
Wartość od zera do 1, która wskazuje krycie pędzla. Ta wartość jest stałym mnożnikiem, który liniowo skaluje wartość alfa wszystkich pikseli wypełnionych pędzlem. Wartości krycia są zaciśnięte w zakresie od 0 do 1, zanim zostaną pomnożone razem.

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::SetTransform

Stosuje określone przekształcenie do obiektu docelowego renderowania, zastępując istniejącą transformację. Wszystkie kolejne operacje rysowania występują w przekształconym miejscu.

```cpp
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>Parametry

*Przekształcić*<br/>
Transformacja stosowana do celu renderowania

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
