---
title: CBitmapRenderTarget Class
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8c110ec8f7c232180bf054e8e4ba90a18f1902c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388440"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget Class

Otoka ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Składnia

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Tworzy obiekt CBitmapRenderTarget.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Dołącza istniejące renderowania interfejsu docelowego do obiektu|
|[CBitmapRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Pobiera mapy bitowej dla tego obiektu docelowego renderowania. Zwrócone mapy bitowej może służyć do rysowania operacji.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Zwraca ID2D1BitmapRenderTarget interfejsu|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*](#operator_id2d1bitmaprendertarget_star)|Zwraca ID2D1BitmapRenderTarget interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Wskaźnik do obiektu ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

Dołącza istniejące renderowania interfejsu docelowego do obiektu

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Istniejący interfejs docelowego renderowania. Nie może mieć wartości NULL

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

Tworzy obiekt CBitmapRenderTarget.

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

Odłącza interfejs docelowy renderowania z obiektu

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączonego renderowania interfejs docelowy.

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

Pobiera mapy bitowej dla tego obiektu docelowego renderowania. Zwrócone mapy bitowej może służyć do rysowania operacji.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parametry

*bitmap*<br/>
Po powrocie z tej metody zawiera Nieprawidłowa mapa bitowa dla tego obiektu docelowego renderowania. Ta mapa bitowa może służyć do rysowania operacji.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

Zwraca ID2D1BitmapRenderTarget interfejsu

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

Wskaźnik do obiektu ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *

Zwraca ID2D1BitmapRenderTarget interfejsu

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1BitmapRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
