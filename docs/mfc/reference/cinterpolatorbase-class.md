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
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916191"
---
# <a name="cinterpolatorbase-class"></a>Klasa CInterpolatorBase

Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, gdy musi obliczyć nową wartość zmiennej animacji.

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
|[CInterpolatorBase:: CreateInstance](#createinstance)|Tworzy wystąpienie programu `CInterpolatorBase` i zapisuje wskaźnik do niestandardowego interpolowania, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase:: getzależności](#getdependencies)|Pobiera zależności interpolacji. (Przesłania `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase:: GetDuration](#getduration)|Pobiera czas trwania interpolacji. (Przesłania `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Pobiera końcową wartość, do której prowadzi ten Interpolacja. (Przesłania `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpoluje wartość w danym przesunięciu (przesłonięcia `CUIAnimationInterpolatorBase::InterpolateValue`).|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpoluje szybkość dla danego przesunięcia (przesłonięcia `CUIAnimationInterpolatorBase::InterpolateVelocity`).|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Przechowuje wskaźnik do niestandardowego interpolowania, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase:: SetDuration](#setduration)|Ustawia czas trwania interpolacji (przesłonięcia `CUIAnimationInterpolatorBase::SetDuration`).|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową i prędkość dla interpolacji. (Przesłania `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Uwagi

Ta procedura obsługi jest tworzona i przenoszona `IUIAnimationTransitionFactory::CreateTransition` do `CCustomTransition` momentu utworzenia obiektu w ramach procesu inicjowania animacji (rozpoczętego przez `CAnimationController::AnimateGroup`). Zazwyczaj nie trzeba używać tej klasy bezpośrednio, a `CCustomInterpolator`jedynie routs wszystkie zdarzenia do klasy pochodnej, której wskaźnik jest przekazywać do `CCustomTransition`konstruktora.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller. h

##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Konstruuje obiekt CInterpolatorBase.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>CInterpolatorBase:: CreateInstance

Tworzy wystąpienie elementu CInterpolatorBase i zapisuje wskaźnik do niestandardowego interpolowania, który będzie obsługiwał zdarzenia.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do niestandardowego interpolka.

*ppHandler*<br/>
Rozdzielczości. Zawiera wskaźnik do wystąpienia elementu CInterpolatorBase, gdy funkcja zwraca wartość.

### <a name="return-value"></a>Wartość zwracana

##  <a name="getdependencies"></a>CInterpolatorBase:: getzależności

Pobiera zależności interpolacji.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Rozdzielczości. Aspekty interpolacji, które są zależne od wartości początkowej przesłanej do SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Rozdzielczości. Aspekty interpolacji, które zależą od początkowej prędkości przekazaną do SetInitialValueAndVelocity.

*durationDependencies*<br/>
Rozdzielczości. Aspekty interpolacji, które zależą od czasu trwania przesłanego do SetDuration.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody getzależności.

##  <a name="getduration"></a>CInterpolatorBase:: GetDuration

Pobiera czas trwania interpolacji.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Rozdzielczości. Czas trwania przejścia (w sekundach).

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody GetDuration.

##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Pobiera końcową wartość, do której prowadzi ten Interpolacja.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Rozdzielczości. Końcowa wartość zmiennej na końcu przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody GetFinalValue.

##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpoluje wartość w danym przesunięciu

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większe lub równe zero i mniejsze niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*value*<br/>
Rozdzielczości. Wartość interpolowana.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody InterpolateValue.

##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpoluje szybkość dla danego przesunięcia

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większe lub równe zeru i mniejsze lub równe czasowi trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*szybkość pracy*<br/>
Rozdzielczości. Szybkość zmiennej w przesunięciu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody InterpolateVelocity.

##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Przechowuje wskaźnik do niestandardowego interpolowania, który będzie obsługiwał zdarzenia.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do niestandardowego interpolka.

##  <a name="setduration"></a>CInterpolatorBase:: SetDuration

Ustawia czas trwania interpolacji

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody SetDuration.

##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Ustawia wartość początkową i prędkość dla interpolacji.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialValue*<br/>
Wartość zmiennej na początku przejścia.

*initialVelocity*<br/>
Szybkość zmiennej na początku przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca S_OK. Zwraca wartość E_FAIL, Jeśli CCustomInterpolator nie jest ustawiona, lub implementacja niestandardowa zwraca wartość FALSE z metody SetInitialValueAndVelocity.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
