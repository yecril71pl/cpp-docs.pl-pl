---
title: Klasa CInterpolatorBase
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: efa08aa5dd556d7e136323c31451a9f33bd72ec6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754948"
---
# <a name="cinterpolatorbase-class"></a>Klasa CInterpolatorBase

Implementuje wywołanie zwrotne, który jest wywoływany przez interfejs API animacji, gdy ma obliczyć nową wartość zmiennej animacji.

## <a name="syntax"></a>Składnia

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Konstruuje `CInterpolatorBase` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Tworzy wystąpienie `CInterpolatorBase` i przechowuje wskaźnik do niestandardowego interpolatora, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Pobiera zależności interpolatora. (Przesłania `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase::GetDuration](#getduration)|Pobiera czas trwania interpolatora. (Przesłania `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Pobiera wartość końcową, do której prowadzi interpolator. (Przesłania `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpoluje wartość przy danym przesunięciu (Zastąpienia `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpoluje prędkość przy danym przesunięciu `CUIAnimationInterpolatorBase::InterpolateVelocity`(Zastępowanie .)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Przechowuje wskaźnik do niestandardowego interpolatora, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase::SetDuration](#setduration)|Ustawia czas trwania interpolatora (Overrides `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową i prędkość interpolatora. (Przesłania `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Uwagi

Ten program obsługi jest `IUIAnimationTransitionFactory::CreateTransition` tworzony `CCustomTransition` i przekazywany do momentu utworzenia obiektu `CAnimationController::AnimateGroup`jako części procesu inicjowania animacji (rozpoczętego przez ). Zazwyczaj nie trzeba używać tej klasy bezpośrednio, to po prostu `CCustomInterpolator`routs wszystkie zdarzenia do klasy pochodnej, którego wskaźnik jest przekazywany do konstruktora `CCustomTransition`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Konstruuje CInterpolatorBase obiektu.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>CInterpolatorBase::CreateInstance

Tworzy wystąpienie CInterpolatorBase i przechowuje wskaźnik do niestandardowego interpolatora, który będzie obsługi zdarzeń.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do niestandardowego interpolatora.

*ps.*<br/>
Wyjście. Zawiera wskaźnik do wystąpienia CInterpolatorBase, gdy funkcja zwraca.

### <a name="return-value"></a>Wartość zwracana

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase::GetDependencies

Pobiera zależności interpolatora.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Wyjście. Aspekty interpolatora, które zależą od wartości początkowej przekazane do SetInitialValueAndVelocity.

*initialVelocityZależnienia*<br/>
Wyjście. Aspekty interpolatora, które zależą od prędkości początkowej przekazywane do SetInitialValueAndVelocity.

*czas trwaniaZależności*<br/>
Wyjście. Aspekty interpolatora, które zależą od czasu trwania przekazanych do SetDuration.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiona lub implementacji niestandardowej zwraca FALSE z GetDependencies metody.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>CInterpolatorBase::GetDuration

Pobiera czas trwania interpolatora.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Wyjście. Czas trwania przejścia w sekundach.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacja niestandardowa zwraca FALSE z GetDuration metody.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Pobiera wartość końcową, do której prowadzi interpolator.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wyjście. Ostateczna wartość zmiennej na końcu przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacja niestandardowa zwraca FALSE z GetFinalValue metody.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpoluje wartość przy danym przesunięciu

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większe lub równe zero i mniejsze niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*value*<br/>
Wyjście. Wartość interpolowana.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacja niestandardowa zwraca FALSE z InterpolateValue metody.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpoluje prędkość przy danym odsunięciu

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większe lub równe zero i mniejsze lub równe czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*Prędkość*<br/>
Wyjście. Prędkość zmiennej przy odsunięciu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacja niestandardowa zwraca FALSE z Metody InterpolateVelocity.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Przechowuje wskaźnik do niestandardowego interpolatora, który będzie obsługiwał zdarzenia.

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do niestandardowego interpolatora.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>CInterpolatorBase::SetDuration

Ustawia czas trwania interpolatora

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacji niestandardowej zwraca FALSE z SetDuration metody.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Ustawia wartość początkową i prędkość interpolatora.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*wartość początkowa*<br/>
Wartość zmiennej na początku przejścia.

*początkowaVelocity*<br/>
Prędkość zmiennej na początku przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwraca S_OK. Zwraca E_FAIL, jeśli CCustomInterpolator nie jest ustawiony lub implementacja niestandardowa zwraca FALSE z SetInitialValueAndVelocity metody.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
