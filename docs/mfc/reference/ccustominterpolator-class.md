---
title: Klasa CCustomInterpolator
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749163"
---
# <a name="ccustominterpolator-class"></a>Klasa CCustomInterpolator

Implementuje podstawowy interpolator.

## <a name="syntax"></a>Składnia

```
class CCustomInterpolator;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Przeciążone. Konstruuje niestandardowy obiekt interpolatora i inicjuje czas trwania i prędkość do określonych wartości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|Pobiera zależności interpolatora.|
|[CCustomInterpolator::GetDuration](#getduration)|Pobiera czas trwania interpolatora.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Pobiera wartość końcową, do której prowadzi interpolator.|
|[CCustomInterpolator::Init](#init)|Inicjuje czas trwania i wartość końcową.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpoluje wartość przy danym przesunięciu.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpoluje prędkość przy danym odsunięciu|
|[CCustomInterpolator::SetDuration](#setduration)|Ustawia czas trwania interpolatora.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową i prędkość interpolatora.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Wartość interpolowana.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Prędkość interpolowana.|
|[CCustomInterpolator::m_duration](#m_duration)|Czas trwania przejścia.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Ostateczna wartość zmiennej na końcu przejścia.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Wartość zmiennej na początku przejścia.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Prędkość zmiennej na początku przejścia.|

## <a name="remarks"></a>Uwagi

Wywodź klasę z CCustomInterpolator i zastąpić wszystkie niezbędne metody w celu zaimplementowania algorytmu interpolacji niestandardowej. Wskaźnik do tej klasy powinny być przekazywane jako parametr do CCustomTransition.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CCustomInterpolator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator

Konstruuje niestandardowy obiekt interpolatora i ustawia wszystkie wartości na domyślne 0.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

*finalValue*

### <a name="remarks"></a>Uwagi

Użyj CCustomInterpolator::Init zainicjować czas trwania i wartość końcową w dalszej części kodu.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::GetDependencies

Pobiera zależności interpolatora.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Wyjście. Aspekty interpolatora, które zależą od wartości początkowej przekazane do SetInitialValueAndVelocity.

*initialVelocityZależnienia*<br/>
Wyjście. Aspekty interpolatora, które zależą od prędkości początkowej przekazywane do SetInitialValueAndVelocity.

*czas trwaniaZależności*<br/>
Wyjście. Aspekty interpolatora, które zależą od czasu trwania przekazanych do SetDuration.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration

Pobiera czas trwania interpolatora.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Wyjście. Czas trwania przejścia w sekundach.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue

Pobiera wartość końcową, do której prowadzi interpolator.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wyjście. Ostateczna wartość zmiennej na końcu przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init

Inicjuje czas trwania i wartość końcową.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Ostateczna wartość zmiennej na końcu przejścia.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue

Interpoluje wartość przy danym przesunięciu.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Wyjście. Wartość interpolowana.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity

Interpoluje prędkość przy danym odsunięciu

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Prędkość*<br/>
Wyjście. Prędkość zmiennej przy odsunięciu.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue

Wartość interpolowana.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity

Prędkość interpolowana.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue

Ostateczna wartość zmiennej na końcu przejścia.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue

Wartość zmiennej na początku przejścia.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity

Prędkość zmiennej na początku przejścia.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration

Ustawia czas trwania interpolatora.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity

Ustawia wartość początkową i prędkość interpolatora.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*wartość początkowa*<br/>
Wartość zmiennej na początku przejścia.

*początkowaVelocity*<br/>
Prędkość zmiennej na początku przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawowa implementacja zawsze zwraca wartość TRUE. Zwraca FAŁSZ z implementacji zastąpione, jeśli chcesz zakończyć się niepowodzeniem zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
