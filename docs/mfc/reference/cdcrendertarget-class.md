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
ms.openlocfilehash: 8c07962c017d160cb3ce5841a75f1ae8a8761641
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753393"
---
# <a name="cdcrendertarget-class"></a>Klasa CDCRenderTarget

Otoka dla ID2D1DCRenderTarget.

## <a name="syntax"></a>Składnia

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Konstruuje obiekt CDCRenderTarget.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::Dołącz](#attach)|Dołącza istniejący interfejs docelowy renderowania do obiektu|
|[CDCRenderTarget::BindDC](#binddc)|Wiąże obiekt docelowy renderowania z kontekstem urządzenia, do którego wydaje polecenia rysowania|
|[CDCRenderTarget::Utwórz](#create)|Tworzy CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Zwraca interfejs ID2D1DCRenderTarget|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|Zwraca interfejs ID2D1DCRenderTarget|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Wskaźnik do obiektu ID2DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[Cel CDCRender](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Dołącz

Dołącza istniejący interfejs docelowy renderowania do obiektu

```cpp
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Istniejący interfejs docelowy renderowania. Nie może być null

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC

Wiąże obiekt docelowy renderowania z kontekstem urządzenia, do którego wydaje polecenia rysowania

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Kontekst urządzenia, do którego obiekt docelowy renderowania wydaje polecenia rysowania

*Rect*<br/>
Wymiary uchwytu do kontekstu urządzenia (HDC), z którym jest powiązany obiekt docelowy renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget

Konstruuje obiekt CDCRenderTarget.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Utwórz

Tworzy CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parametry

*Rekwizyty*<br/>
Tryb renderowania, format pikseli, opcje komunikacji zdalnej, informacje DPI i minimalna obsługa DirectX wymagana do renderowania sprzętowego.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach

Odłącza interfejs docelowy renderowania z obiektu

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs docelowy renderowania.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget

Zwraca interfejs ID2D1DCRenderTarget

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2DCRenderTarget lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget

Wskaźnik do obiektu ID2DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget*

Zwraca interfejs ID2D1DCRenderTarget

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2DCRenderTarget lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
