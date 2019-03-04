---
title: Klasa CHwndRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: bf446cdf1ea064943ff92d66ac89b0e4177e6910
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270335"
---
# <a name="chwndrendertarget-class"></a>Klasa CHwndRenderTarget

Otoka ID2D1HwndRenderTarget.

## <a name="syntax"></a>Składnia

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Tworzy obiekt CHwndRenderTarget z HWND.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Dołącza istniejące renderowania interfejsu docelowego do obiektu|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Wskazuje, czy HWND skojarzone z tego obiektu docelowego renderowania jest zamknięte.|
|[CHwndRenderTarget::Create](#create)|Tworzy element docelowy renderowania skojarzony z oknem|
|[CHwndRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Zwraca HWND skojarzony z tym obiekt docelowy renderowania.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Zwraca interfejs ID2D1HwndRenderTarget.|
|[CHwndRenderTarget::ReCreate](#recreate)|Ponownie tworzy obiektu docelowego renderowania skojarzony z oknem|
|[CHwndRenderTarget::Resize](#resize)|Zmienia rozmiar obiektu docelowego renderowania do rozmiaru określonego pikseli|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Zwraca interfejs ID2D1HwndRenderTarget.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Wskaźnik do obiektu ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

Dołącza istniejące renderowania interfejsu docelowego do obiektu

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Istniejący interfejs docelowego renderowania. Nie może mieć wartości NULL

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

Wskazuje, czy HWND skojarzone z tego obiektu docelowego renderowania jest zamknięte.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która wskazuje, czy element docelowy renderowania HWND skojarzony z tym jest zamknięte.

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

Tworzy obiekt CHwndRenderTarget z HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parametry

*hwnd*<br/>
HWND skojarzony z tym obiekt docelowy renderowania

##  <a name="create"></a>  CHwndRenderTarget::Create

Tworzy element docelowy renderowania skojarzony z oknem

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
HWND skojarzony z tym obiekt docelowy renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

Odłącza interfejs docelowy renderowania z obiektu

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączonego renderowania interfejs docelowy.

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

Zwraca HWND skojarzony z tym obiekt docelowy renderowania.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Wartość zwracana

HWND skojarzony z tym obiekt docelowy renderowania.

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

Zwraca interfejs ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1HwndRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

Wskaźnik do obiektu ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget *

Zwraca interfejs ID2D1HwndRenderTarget.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1HwndRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

Ponownie tworzy obiektu docelowego renderowania skojarzony z oknem

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
HWND skojarzony z tym obiekt docelowy renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="resize"></a>  CHwndRenderTarget::Resize

Zmienia rozmiar obiektu docelowego renderowania do rozmiaru określonego pikseli

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Nowy rozmiar obiektu docelowego renderowania w pikselach urządzenia

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
