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
ms.openlocfilehash: c94cb3849d4101365d137733c08135b86db23801
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518667"
---
# <a name="canimationtimereventhandler-class"></a>Klasa CAnimationTimerEventHandler

Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, po wystąpieniu zdarzenia czasowego.

## <a name="syntax"></a>Składnia

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationTimerEventHandler` wywołania zwrotnego.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Obsługuje zdarzenia, które wystąpiły po zakończeniu aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPostUpdate`).|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Obsługuje zdarzenia występujące przed rozpoczęciem aktualizacji animacji. (Przesłania `CUIAnimationTimerEventHandlerBase::OnPreUpdate`).|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Obsługuje zdarzenia, które występują, gdy szybkość renderowania animacji spadnie poniżej minimalna szybkość pożądane. (Przesłania `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`).|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.|

## <a name="remarks"></a>Uwagi

Ta procedura obsługi zdarzeń jest tworzony i przekazywany do IUIAnimationTimer::SetTimerEventHandler, gdy wywołujesz CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance

Tworzy wystąpienie CAnimationTimerEventHandler wywołania zwrotnego.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.

*ppTimerEventHandler*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

Obsługuje zdarzenia, które wystąpiły po zakończeniu aktualizacji animacji.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL.

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

Obsługuje zdarzenia występujące przed rozpoczęciem aktualizacji animacji.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL.

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

Obsługuje zdarzenia, które występują, gdy szybkość renderowania animacji spadnie poniżej minimalna szybkość pożądane.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*kl. / s*

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
