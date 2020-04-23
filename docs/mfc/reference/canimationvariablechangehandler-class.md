---
title: Klasa CAnimationVariableChangeHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 2dc8f2c03f9df34012fb9db1ed5e5b0bb448b17f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755040"
---
# <a name="canimationvariablechangehandler-class"></a>Klasa CAnimationVariableChangeHandler

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji, gdy zmienia się wartość zmiennej animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Konstruuje `CAnimationVariableChangeHandler` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|Tworzy wystąpienie `CAnimationVariableChangeHandler` obiektu.|
|[CAnimationVariableChangeHandler::OnValueZmienił](#onvaluechanged)|Wywoływana po zmianie wartości zmiennej animacji. (Przesłania `CUIAnimationVariableChangeHandlerBase::OnValueChanged`).|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.|

## <a name="remarks"></a>Uwagi

Ten program obsługi zdarzeń `IUIAnimationVariable::SetVariableChangeHandler` jest tworzony i `CAnimationVariable::EnableValueChangedEvent` `CAnimationBaseObject::EnableValueChangedEvent` przekazywany do metody, podczas wywoływania lub (który włącza to zdarzenie dla wszystkich zmiennych animacji zhermetyzowanych w obiekcie animacji).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueZmienił

Wywoływana po zmianie wartości zmiennej animacji.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Parametry

*Serii ujęć*<br/>
Scenorysu, który jest animowanie zmiennej.

*Zmiennej*<br/>
Zmienna animacji, która została zaktualizowana.

*Newvalue*<br/>
Nowa wartość.

*poprzedniWartość*<br/>
Poprzednia wartość.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. W przeciwnym razie zwraca kod błędu HRESULT.

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController

Przechowuje wskaźnik do kontrolera animacji do kierowania zdarzeń.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pKontroleranimacji*<br/>
Wskaźnik do kontrolera animacji, który będzie odbierał zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
