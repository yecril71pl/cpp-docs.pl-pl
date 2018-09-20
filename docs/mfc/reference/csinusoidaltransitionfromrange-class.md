---
title: Klasa CSinusoidalTransitionFromRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe31f54a15f897cd14c16ee3061e1f1a7d45584c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422392"
---
# <a name="csinusoidaltransitionfromrange-class"></a>Klasa CSinusoidalTransitionFromRange

Hermetyzuje przejście zakresu sinusoidalnego, które dany zakres oscylacji.

## <a name="syntax"></a>Składnia

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|Tworzy obiekt przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|Wartość zmiennej animacji w piku sinusoidalnego wave.|
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|Wartość zmiennej animacji przy rynience sinusoidalnego wave.|
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|Czas trwania przejścia.|
|[CSinusoidalTransitionFromRange::m_period](#m_period)|Okres oscylacji sinusoidalnego wave w ciągu kilku sekund.|
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|Krzywa na początku tego przejścia.|

## <a name="remarks"></a>Uwagi

Wartość zmiennej animacji zmienia się od określonej wartości minimalnej i maksymalnej przez cały czas trwania przejście zakresu sinusoidalnego. Parametr nachylenie jest używany do rozróżniania między dwa możliwe poprzedzającym sinus określonego przez inne parametry. Ponieważ wszystkie przejścia są automatycznie czyszczone, zaleca się ich przydzielone za pomocą nowego operatora. Zhermetyzowanego obiektu IUIAnimationTransition COM przy utworzono CAnimationController::AnimateGroup, aż do, a następnie ma wartość NULL. Zmienianie zmiennych składowych, po tworzenie ten obiekt COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="create"></a>  CSinusoidalTransitionFromRange::Create

Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do przejścia biblioteki, która jest odpowiedzialna za tworzenie standardowego przejścia.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="csinusoidaltransitionfromrange"></a>  CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange

Tworzy obiekt przejścia.

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*dblMinimumValue*<br/>
Wartość zmiennej animacji przy rynience sinusoidalnego wave.

*dblMaximumValue*<br/>
Wartość zmiennej animacji w piku sinusoidalnego wave.

*Okres*<br/>
Okres oscylacji sinusoidalnego wave w ciągu kilku sekund.

*Krzywa*<br/>
Krzywa na początku tego przejścia.

##  <a name="m_dblmaximumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMaximumValue

Wartość zmiennej animacji w piku sinusoidalnego wave.

```
DOUBLE m_dblMaximumValue;
```

##  <a name="m_dblminimumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMinimumValue

Wartość zmiennej animacji przy rynience sinusoidalnego wave.

```
DOUBLE m_dblMinimumValue;
```

##  <a name="m_duration"></a>  CSinusoidalTransitionFromRange::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_period"></a>  CSinusoidalTransitionFromRange::m_period

Okres oscylacji sinusoidalnego wave w ciągu kilku sekund.

```
UI_ANIMATION_SECONDS m_period;
```

##  <a name="m_slope"></a>  CSinusoidalTransitionFromRange::m_slope

Krzywa na początku tego przejścia.

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
