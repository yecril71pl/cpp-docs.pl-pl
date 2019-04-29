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
ms.openlocfilehash: d12f38491cf3aafca41756ce97e1cad44deb67d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338262"
---
# <a name="canimationstoryboardeventhandler-class"></a>Klasa CAnimationStoryboardEventHandler

Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, gdy zmieniono stan scenorysu lub zaktualizowano scenorys.

## <a name="syntax"></a>Składnia

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Konstruuje `CAnimationStoryboardEventHandler` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationStoryboardEventHandler` wywołania zwrotnego.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Obsługuje `OnStoryboardStatusChanged` zdarzenia, które występują, gdy zmieni się stan scenorysu (zastępuje `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.)|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Obsługuje `OnStoryboardUpdated` zdarzenia, które występują, gdy zaktualizowano scenorys (zastępuje `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.|

## <a name="remarks"></a>Uwagi

Ta procedura obsługi zdarzeń jest tworzony i przekazywany do `IUIAnimationStoryboard::SetStoryboardEventHandler` po wywołaniu metody `CAnimationController::EnableStoryboardEventHandler`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="canimationstoryboardeventhandler"></a>  CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Tworzy obiekt CAnimationStoryboardEventHandler.

```
CAnimationStoryboardEventHandler();
```

##  <a name="createinstance"></a>  CAnimationStoryboardEventHandler::CreateInstance

Tworzy wystąpienie CAnimationStoryboardEventHandler wywołania zwrotnego.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.

*ppHandler*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

##  <a name="onstoryboardstatuschanged"></a>  CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

Obsługuje OnStoryboardStatusChanged zdarzenia, które występują, gdy zmieni się stan scenorysu

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*scenorysu*<br/>
Wskaźnik do scenorysu, którego stan został zmieniony.

*newStatus*<br/>
Określa nowy stan scenorysu.

*previousStatus*<br/>
Określa poprzedni stan scenorysu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL.

##  <a name="onstoryboardupdated"></a>  CAnimationStoryboardEventHandler::OnStoryboardUpdated

Obsługuje OnStoryboardUpdated zdarzenia, które występują, gdy zaktualizowano scenorys

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Parametry

*scenorysu*<br/>
Wskaźnik do scenorysu, który został zaktualizowany.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationStoryboardEventHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji kierowanie zdarzeń.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Wskaźnik do Kontroler animacji, które zostaną odebrane zdarzenia.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
