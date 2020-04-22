---
title: Klasa CAnimationManagerEventHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: 58bb37e9de40f4bc711b417eab107aa55b8ff0e8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750120"
---
# <a name="canimationmanagereventhandler-class"></a>Klasa CAnimationManagerEventHandler

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji po zmianie stanu menedżera animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Konstruuje `CAnimationManagerEventHandler` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Tworzy wystąpienie `CAnimationManagerEventHandler` obiektu.|
|[CAnimationManagerEventHandler::OnManagerStatusZmienia](#onmanagerstatuschanged)|Wywoływana po zmianie stanu menedżera animacji. (Przesłania `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`).|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.|

## <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń jest tworzony i przekazywany do metody IUIAnimationManager::SetManagerEventHandler, po wywołaniu CAnimationController::EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Konstruuje CAnimationManagerEventHandler obiektu.

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationManagerEventHandler::CreateInstance

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Tworzy wystąpienie CAnimationManagerEventHandler obiektu.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

*ppManagerEventHandler*<br/>
Wyjście. Jeśli metoda powiedzie się zawiera wskaźnik do obiektu COM, który będzie obsługiwać aktualizacje stanu do menedżera animacji.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusZmienia

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Wywoływana po zmianie stanu menedżera animacji.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*nowyStatus*<br/>
Nowy stan.

*poprzednistatus*<br/>
Poprzedni stan.

### <a name="return-value"></a>Wartość zwracana

Bieżąca implementacja zawsze zwraca S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Wymagany jest dodatek SP1 dla programu Visual Studio 2010.

Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
