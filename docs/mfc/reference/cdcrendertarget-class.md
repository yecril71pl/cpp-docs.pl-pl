---
title: Klasa CDCRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: e172d175bba5b4c379f7cd29451d7ad4215d9c68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541716"
---
# <a name="cdcrendertarget-class"></a>Klasa CDCRenderTarget

Otoka ID2D1DCRenderTarget.

## <a name="syntax"></a>Składnia

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Tworzy obiekt CDCRenderTarget.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|Dołącza istniejące renderowania interfejsu docelowego do obiektu|
|[CDCRenderTarget::BindDC](#binddc)|Powiązania obiektu docelowego renderowania do kontekstu urządzenia, do którego emituje polecenia rysowania|
|[CDCRenderTarget::Create](#create)|Tworzy CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Zwraca ID2D1DCRenderTarget interfejsu|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Zwraca ID2D1DCRenderTarget interfejsu|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Wskaźnik do obiektu ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

Dołącza istniejące renderowania interfejsu docelowego do obiektu

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Istniejący interfejs docelowego renderowania. Nie może mieć wartości NULL

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

Powiązania obiektu docelowego renderowania do kontekstu urządzenia, do którego emituje polecenia rysowania

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Kontroler domeny*<br/>
Kontekst urządzenia, do którego obiektu docelowego renderowania wydaje polecenia rysowania

*Rect*<br/>
Wymiary dojścia do kontekstu urządzenia (elementu HDC), z którym powiązany jest obiektu docelowego renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

Tworzy obiekt CDCRenderTarget.

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

Tworzy CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parametry

*właściwości*<br/>
Tryb renderowania, format pikseli, opcji komunikacji zdalnej, informacje o rozdzielczości DPI i minimalna obsługa technologii DirectX, wymagane do renderowania sprzętowego.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość PRAWDA. W przeciwnym razie zwraca wartość FALSE.

##  <a name="detach"></a>  CDCRenderTarget::Detach

Odłącza interfejs docelowy renderowania z obiektu

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączonego renderowania interfejs docelowy.

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

Zwraca ID2D1DCRenderTarget interfejsu

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1DCRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

Wskaźnik do obiektu ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget *

Zwraca ID2D1DCRenderTarget interfejsu

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1DCRenderTarget lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
