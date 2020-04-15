---
title: Klasa CAnimationVariableIntegerChangeHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: 261f8eb17953c047fcc8ec05ae48dc369de4614c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377042"
---
# <a name="canimationvariableintegerchangehandler-class"></a>Klasa CAnimationVariableIntegerChangeHandler

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji, gdy zmienia się wartość zmiennej animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Konstruuje `CAnimationVariableIntegerChangeHandler` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance CAnimationVariableIntegerChangeHandler::CreateInstance CAnimationVariableIntegerChangeHandler::CreateInstance CAni](#createinstance)|Tworzy wystąpienie `CAnimationVariableIntegerChangeHandler` wywołania zwrotnego.|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueZmienił](#onintegervaluechanged)|Wywoływana po zmianie wartości zmiennej animacji. (Przesłania `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`).|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.|

## <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń jest tworzony i przekazywany do metody IUIAnimationVariable::SetVariableIntegerChangeHandler, po wywołaniu CAnimationVariable::EnableIntegerValueChangedEvent lub CAnimationBaseObject::EnableIntegerValueChangedEvent (która włącza to zdarzenie dla wszystkich zmiennych animacji zamkniętych w obiekcie animacji).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Klasy MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Konstruuje CAnimationVariableIntegerChangeHandler obiektu.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance CAnimationVariableIntegerChangeHandler::CreateInstance CAnimationVariableIntegerChangeHandler::CreateInstance CAni

Tworzy wystąpienie CAnimationVariableIntegerChangeHandler wywołania zwrotnego.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

*ps.*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueZmienił

Wywoływana po zmianie wartości zmiennej animacji.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Parametry

*Serii ujęć*<br/>
Scenorysu, który jest animowanie zmiennej.

*Zmiennej*<br/>
Zmienna animacji, która została zaktualizowana.

*Newvalue*<br/>
Nowa zaokrąglona wartość.

*poprzedniWartość*<br/>
Poprzednia zaokrąglona wartość.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
