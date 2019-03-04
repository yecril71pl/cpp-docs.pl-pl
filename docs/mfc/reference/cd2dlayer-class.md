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
ms.openlocfilehash: 28ebe19b0f28692116a0b95721ff2e5490ad7e68
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270881"
---
# <a name="cd2dlayer-class"></a>Klasa CD2DLayer

Otoka ID2D1Layer.

## <a name="syntax"></a>Składnia

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Tworzy obiekt CD2DLayer.|
|[CD2DLayer::~CD2DLayer](#_dtorcd2dlayer)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt warstwy D2D.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::attach](#attach)|Dołącza istniejących zasobów interfejsu do obiektu|
|[CD2DLayer::Create](#create)|Tworzy CD2DLayer. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Niszczy obiekt CD2DLayer. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Odłącza interfejsu zasobów z obiektu|
|[CD2DLayer::Get](#get)|Zwraca ID2D1Layer interfejsu|
|[CD2DLayer::GetSize](#getsize)|Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia|
|[CD2DLayer::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|Zwraca ID2D1Layer interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Przechowuje wskaźnik do obiektu ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="_dtorcd2dlayer"></a>  CD2DLayer:: ~ CD2DLayer

Destruktor. Wywołuje się, kiedy niszczony jest obiekt warstwy D2D.

```
virtual ~CD2DLayer();
```

##  <a name="attach"></a>  CD2DLayer::attach

Dołącza istniejących zasobów interfejsu do obiektu

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Istniejący interfejs zasobów. Nie może mieć wartości NULL

##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer

Tworzy obiekt CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

*bAutoDestroy*<br/>
Wskazuje, że obiekt jest niszczony przez właściciela (pParentTarget).

##  <a name="create"></a>  CD2DLayer::Create

Tworzy CD2DLayer.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Wskaźnik do elementu docelowego renderowania.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="destroy"></a>  CD2DLayer::Destroy

Niszczy obiekt CD2DLayer.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLayer::detach

Odłącza interfejsu zasobów z obiektu

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu odłączyć zasobu.

##  <a name="get"></a>  CD2DLayer::Get

Zwraca ID2D1Layer interfejsu

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Layer lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="getsize"></a>  CD2DLayer::GetSize

Zwraca rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący rozmiar obiektu docelowego renderowania w pikselach niezależnych od urządzenia

##  <a name="isvalid"></a>  CD2DLayer::IsValid

Sprawdzanie zasobów ważności

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zasób jest ważny; w przeciwnym razie wartość FALSE.

##  <a name="m_player"></a>  CD2DLayer::m_pLayer

Przechowuje wskaźnik do obiektu ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer *

Zwraca ID2D1Layer interfejsu

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1Layer lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
