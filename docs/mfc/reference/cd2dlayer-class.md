---
title: Klasa CD2DLayer
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: 30025d6097e439c07202d144a6e549845b78ffa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754760"
---
# <a name="cd2dlayer-class"></a>Klasa CD2DLayer

Otoka dla ID2D1Layer.

## <a name="syntax"></a>Składnia

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Konstruuje obiekt CD2DLayer.|
|[Płyta CD2DLayer::~PŁYTA 2DLayer](#_dtorcd2dlayer)|Destruktor. Wywoływane, gdy obiekt warstwy D2D jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::Dołącz](#attach)|Dołącza istniejący interfejs zasobu do obiektu|
|[CD2DLayer::Utwórz](#create)|Tworzy warstwę CD2D. (Zastępuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Niszczy OBIEKT CD2DLayer. (Zastępuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Odłącza interfejs zasobu od obiektu|
|[CD2DLayer::Pobierz](#get)|Zwraca interfejs ID2D1Layer|
|[CD2DLayer::GetSize](#getsize)|Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia|
|[Cd2DLayer::IsValid](#isvalid)|Sprawdza ważność zasobu (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer*](#operator_id2d1layer_star)|Zwraca interfejs ID2D1Layer|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Przechowuje wskaźnik do obiektu ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DŹródło](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>Płyta CD2DLayer::~PŁYTA 2DLayer

Destruktor. Wywoływane, gdy obiekt warstwy D2D jest niszczony.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer::Dołącz

Dołącza istniejący interfejs zasobu do obiektu

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Istniejący interfejs zasobów. Nie może być null

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer::CD2DLayer

Konstruuje obiekt CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

*bAutoDestroj*<br/>
Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer::Utwórz

Tworzy warstwę CD2D.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do obiektu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::Destroy

Niszczy OBIEKT CD2DLayer.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::Detach

Odłącza interfejs zasobu od obiektu

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs zasobu.

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer::Pobierz

Zwraca interfejs ID2D1Layer

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Layer lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer::GetSize

Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>Cd2DLayer::IsValid

Sprawdza ważność zasobu

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zasób jest prawidłowy; w przeciwnym razie FALSE.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer::m_pLayer

Przechowuje wskaźnik do obiektu ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::operator ID2D1Layer*

Zwraca interfejs ID2D1Layer

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Layer lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
