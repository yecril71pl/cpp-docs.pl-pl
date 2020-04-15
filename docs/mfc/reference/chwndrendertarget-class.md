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
ms.openlocfilehash: 24cf4127c2f429f66143af3a0f49625f23a4e6ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372465"
---
# <a name="chwndrendertarget-class"></a>Klasa CHwndRenderTarget

Otoka dla ID2D1HwndRenderTarget.

## <a name="syntax"></a>Składnia

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Konstruuje obiekt CHwndRenderTarget z HWND.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::Dołącz](#attach)|Dołącza istniejący interfejs docelowy renderowania do obiektu|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Wskazuje, czy HWND skojarzone z tym obiektem docelowym renderowania jest nieobjęta.|
|[CHwndRenderTarget::Utwórz](#create)|Tworzy obiekt docelowy renderowania skojarzony z oknem|
|[CHwndRenderTarget::Detach](#detach)|Odłącza interfejs docelowy renderowania z obiektu|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Zwraca HWND skojarzone z tym obiektem docelowym renderowania.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Zwraca interfejs ID2D1HwndRenderTarget.|
|[CHwndRenderTarget::Odtwórz](#recreate)|Ponownie tworzy obiekt docelowy renderowania skojarzony z oknem|
|[CHwndRenderTarget::Resize](#resize)|Zmienia rozmiar obiektu docelowego renderowania na określony rozmiar piksela|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|Zwraca interfejs ID2D1HwndRenderTarget.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Wskaźnik do obiektu ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRenderTarget::Dołącz

Dołącza istniejący interfejs docelowy renderowania do obiektu

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Istniejący interfejs docelowy renderowania. Nie może być null

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState

Wskazuje, czy HWND skojarzone z tym obiektem docelowym renderowania jest nieobjęta.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która wskazuje, czy HWND skojarzone z tym obiektem docelowym renderowania jest okludowana.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget

Konstruuje obiekt CHwndRenderTarget z HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND skojarzone z tym celem renderowania

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRenderTarget::Utwórz

Tworzy obiekt docelowy renderowania skojarzony z oknem

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND skojarzone z tym celem renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::Detach

Odłącza interfejs docelowy renderowania z obiektu

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do odłączony interfejs docelowy renderowania.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRenderTarget::GetHwnd

Zwraca HWND skojarzone z tym obiektem docelowym renderowania.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Wartość zwracana

HWND skojarzone z tym obiektem docelowym renderowania.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget

Zwraca interfejs ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1HwndRenderTarget lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

Wskaźnik do obiektu ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget*

Zwraca interfejs ID2D1HwndRenderTarget.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu ID2D1HwndRenderTarget lub NULL, jeśli obiekt nie został jeszcze zainicjowany.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRenderTarget::Odtwórz

Ponownie tworzy obiekt docelowy renderowania skojarzony z oknem

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
HWND skojarzone z tym celem renderowania

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRenderTarget::Resize

Zmienia rozmiar obiektu docelowego renderowania na określony rozmiar piksela

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Nowy rozmiar obiektu docelowego renderowania w pikselach urządzenia

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca wartość TRUE. W przeciwnym razie zwraca wartość FAŁSZ.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
