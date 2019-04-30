---
title: CInterpolatorBase Class
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
ms.openlocfilehash: 379aa5607e459ad8acfd99c5899315afb84ac4a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392664"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase Class

Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, gdy należy obliczyć nową wartość zmiennej animacji.

## <a name="syntax"></a>Składnia

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Konstruuje `CInterpolatorBase` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Tworzy wystąpienie `CInterpolatorBase` i przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Pobiera interpolatora zależności. (Przesłania `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase::GetDuration](#getduration)|Pobiera czas trwania interpolatora. (Przesłania `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Pobiera wartość końcową, do której prowadzi interpolatora. (Przesłania `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Wartość w danym przesunięciu interpolacji (zastępuje `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Szybkość pracy w danym przesunięciu interpolacji (zastępuje `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.|
|[CInterpolatorBase::SetDuration](#setduration)|Ustawia czas trwania interpolatora (zastępuje `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową interpolatora i szybkość pracy. (Przesłania `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Uwagi

Ten program obsługi jest tworzony i przekazywany do `IUIAnimationTransitionFactory::CreateTransition` podczas `CCustomTransition` obiekt jest tworzony jako część procesu inicjowania animacji (uruchomione przez `CAnimationController::AnimateGroup`). Zazwyczaj nie trzeba korzystać bezpośrednio do tej klasy, po prostu routs wszystkich zdarzeń w celu `CCustomInterpolator`-klasy, w których wskaźnik jest przekazywana do konstruktora `CCustomTransition`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

Tworzy obiekt CInterpolatorBase.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

Tworzy wystąpienie CInterpolatorBase i przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do interpolatora niestandardowych.

*ppHandler*<br/>
Dane wyjściowe. Zawiera wskaźnik do wystąpienia CInterpolatorBase, gdy funkcja zwraca.

### <a name="return-value"></a>Wartość zwracana

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

Pobiera interpolatora zależności.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od początkowa wartość przekazywana do SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od prędkości początkowej przekazany do SetInitialValueAndVelocity.

*durationDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od czasu trwania są przekazywane do SetDuration.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody GetDependencies zwraca E_FAIL.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

Pobiera czas trwania interpolatora.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Dane wyjściowe. Czas trwania przejścia, w ciągu kilku sekund.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody GetDuration zwraca E_FAIL.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Pobiera wartość końcową, do której prowadzi interpolatora.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Dane wyjściowe. Końcowa wartość zmiennej z końcem przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody GetFinalValue zwraca E_FAIL.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

Wartość argumentu wartość danego przesunięcia.

```
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większa lub równa zero i mniejsza niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*value*<br/>
Dane wyjściowe. Wartość interpolowane.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody InterpolateValue zwraca E_FAIL.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

Wartość argumentu prędkość w danego przesunięcia.

```
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Przesunięcie od początku przejścia. Przesunięcie jest zawsze większa lub równa zero i mniejsza niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia wynosi zero.

*velocity*<br/>
Dane wyjściowe. Prędkość zmiennej przy przesunięciu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody InterpolateVelocity zwraca E_FAIL.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

Przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do interpolatora niestandardowych.

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

Ustawia czas trwania interpolatora

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody SetDuration zwraca E_FAIL.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

Ustawia wartość początkową interpolatora i szybkość pracy.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue,
  __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialValue*<br/>
Wartość zmiennej na początku tego przejścia.

*initialVelocity*<br/>
Prędkość zmiennej na początku tego przejścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub implementację niestandardową zwróci wartość FALSE z metody SetInitialValueAndVelocity zwraca E_FAIL.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
