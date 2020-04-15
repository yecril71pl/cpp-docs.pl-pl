---
title: Klasa CAnimationStoryboardEventHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365003"
---
# <a name="canimationstoryboardeventhandler-class"></a>Klasa CAnimationStoryboardEventHandler

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji, gdy stan scenorysu zostanie zmieniony lub scenorysu jest aktualizowana.

## <a name="syntax"></a>Składnia

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Konstruuje `CAnimationStoryboardEventHandler` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationStoryboardEventHandler` wywołania zwrotnego.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatzostałezmieniem](#onstoryboardstatuschanged)|Obsługuje `OnStoryboardStatusChanged` zdarzenia, które występują, gdy zmienia się stan `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`scenorysu (Overrides .)|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated CAnimationStoryboardEventHandler::OnStoryboardUpdated CAnimationStoryboardEventHandler::OnStoryboardUpdated CAni](#onstoryboardupdated)|Obsługuje `OnStoryboardUpdated` zdarzenia, które występują, gdy scenorys `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`jest aktualizowany (Overrides .)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.|

## <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń `IUIAnimationStoryboard::SetStoryboardEventHandler` jest tworzony i `CAnimationController::EnableStoryboardEventHandler`przekazywany do metody, po wywołaniu .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Konstruuje CAnimationStoryboardEventHandler obiektu.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance

Tworzy wystąpienie wywołania zwrotnego CAnimationStoryboardEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

*ps.*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatzostałezmieniem

Obsługuje onstoryboardStatusZmienie zdarzenia, które występują, gdy zmienia się stan scenorysu

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*Serii ujęć*<br/>
Wskaźnik do scenorysu, którego stan uległ zmianie.

*nowyStatus*<br/>
Określa nowy stan scenorysu.

*poprzednistatus*<br/>
Określa poprzedni stan scenorysu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated CAnimationStoryboardEventHandler::OnStoryboardUpdated CAnimationStoryboardEventHandler::OnStoryboardUpdated CAni

Obsługuje onstoryboardUpdated zdarzenia, które występują, gdy scenorys jest aktualizowany

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Parametry

*Serii ujęć*<br/>
Wskaźnik do ujęć, który został zaktualizowany.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
