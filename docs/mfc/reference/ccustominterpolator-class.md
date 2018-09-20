---
title: Klasa CCustomInterpolator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 175af6d9fdd02e24aaa9caae663db51c7dd4167a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432831"
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
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Przeciążone. Tworzy obiekt interpolatora niestandardowych i inicjuje czas trwania i szybkość pracy do określonej wartości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|Pobiera interpolatora zależności.|
|[CCustomInterpolator::GetDuration](#getduration)|Pobiera czas trwania interpolatora.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Pobiera wartość końcową, do której prowadzi interpolatora.|
|[CCustomInterpolator::Init](#init)|Inicjuje czas trwania i końcowa wartość.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Wartość argumentu wartości w danym przesunięciu.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Wartość argumentu prędkość w danego przesunięcia.|
|[CCustomInterpolator::SetDuration](#setduration)|Ustawia czas trwania interpolatora.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową interpolatora i szybkość pracy.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Wartość interpolowane.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Prędkość interpolowane.|
|[CCustomInterpolator::m_duration](#m_duration)|Czas trwania przejścia.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Końcowa wartość zmiennej z końcem przejścia.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Wartość zmiennej na początku tego przejścia.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Prędkość zmiennej na początku tego przejścia.|

## <a name="remarks"></a>Uwagi

Wyprowadzenia klasy z CCustomInterpolator i zastępują wszystkie metody niezbędne w celu wdrożenia algorytm interpolacji niestandardowych. Wskaźnik do klasy powinien zostać przekazany jako parametr, do CCustomTransition.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CCustomInterpolator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator

Tworzy obiekt interpolatora niestandardowych i ustawia wszystkie wartości domyślne 0.

```
CCustomInterpolator();


CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*finalValue*

### <a name="remarks"></a>Uwagi

Aby zainicjować czas trwania i końcowa wartość w dalszej części kodu, należy użyć CCustomInterpolator::Init.

##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies

Pobiera interpolatora zależności.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od początkowa wartość przekazywana do SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od prędkości początkowej przekazany do SetInitialValueAndVelocity.

*durationDependencies*<br/>
Dane wyjściowe. Aspekty interpolatora, które są zależne od czasu trwania są przekazywane do SetDuration.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="getduration"></a>  CCustomInterpolator::GetDuration

Pobiera czas trwania interpolatora.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Dane wyjściowe. Czas trwania przejścia, w ciągu kilku sekund.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue

Pobiera wartość końcową, do której prowadzi interpolatora.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Dane wyjściowe. Końcowa wartość zmiennej z końcem przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="init"></a>  CCustomInterpolator::Init

Inicjuje czas trwania i końcowa wartość.

```
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Końcowa wartość zmiennej z końcem przejścia.

##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue

Wartość argumentu wartości w danym przesunięciu.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Dane wyjściowe. Wartość interpolowane.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity

Wartość argumentu prędkość w danego przesunięcia.

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Szybkość pracy*<br/>
Dane wyjściowe. Prędkość zmiennej przy przesunięciu.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue

Wartość interpolowane.

```
DOUBLE m_currentValue;
```

##  <a name="m_currentvelocity"></a>  CCustomInterpolator::m_currentVelocity

Prędkość interpolowane.

```
DOUBLE m_currentVelocity;
```

##  <a name="m_duration"></a>  CCustomInterpolator::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CCustomInterpolator::m_finalValue

Końcowa wartość zmiennej z końcem przejścia.

```
DOUBLE m_finalValue;
```

##  <a name="m_initialvalue"></a>  CCustomInterpolator::m_initialValue

Wartość zmiennej na początku tego przejścia.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity

Prędkość zmiennej na początku tego przejścia.

```
DOUBLE m_initialVelocity;
```

##  <a name="setduration"></a>  CCustomInterpolator::SetDuration

Ustawia czas trwania interpolatora.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity

Ustawia wartość początkową interpolatora i szybkość pracy.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*Wartość początkowa*<br/>
Wartość zmiennej na początku tego przejścia.

*initialVelocity*<br/>
Prędkość zmiennej na początku tego przejścia.

### <a name="return-value"></a>Wartość zwracana

Podstawową implementację zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE od implementacji zgodnym z przesłoniętą jeśli chce się nie powieść zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
