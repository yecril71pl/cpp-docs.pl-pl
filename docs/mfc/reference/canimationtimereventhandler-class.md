---
title: Klasa CAnimationTimerEventHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: 72b6e5d8d9d4823795a1fb053c5f2374cb80fba4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320012"
---
# <a name="canimationtimereventhandler-class"></a>Klasa CAnimationTimerEventHandler

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji, gdy wystąpią zdarzenia chronometrażu.

## <a name="syntax"></a>Składnia

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationTimerEventHandler` wywołania zwrotnego.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Obsługuje zdarzenia, które występują po zakończeniu aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPostUpdate`).|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Obsługuje zdarzenia, które występują przed rozpoczęciem aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPreUpdate`).|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Obsługuje zdarzenia występujące, gdy liczba klatek na sekundę renderowania animacji spadnie poniżej minimalnej pożądanej liczby klatek na sekundę. (Przesłania `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`).|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.|

## <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń jest tworzony i przekazywany do IUIAnimationTimer::SetTimerEventHandler podczas wywoływania CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance

Tworzy wystąpienie wywołania zwrotnego CAnimationTimerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

*ppTimerEventHandler*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate

Obsługuje zdarzenia, które występują po zakończeniu aktualizacji animacji.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate

Obsługuje zdarzenia, które występują przed rozpoczęciem aktualizacji animacji.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>CAnimationTimerEventHandler::OnRenderingTooSlow

Obsługuje zdarzenia występujące, gdy liczba klatek na sekundę renderowania animacji spadnie poniżej minimalnej pożądanej liczby klatek na sekundę.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*Fps*

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
