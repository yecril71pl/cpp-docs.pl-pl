---
title: Klasa CAccelerateDecelerateTransition
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: dbebe794ba76ae4abd3d1e3ea6bc8ee31bc3007f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278863"
---
# <a name="cacceleratedeceleratetransition-class"></a>Klasa CAccelerateDecelerateTransition

Implementuje przyspieszenia-spowalniania przejścia.

## <a name="syntax"></a>Składnia

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Tworzy obiekt przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Stosunek czasu spędzanego w skróceniu czasu trwania.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Stosunek czasu spowolnienie do czasu trwania.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Czas trwania przejścia.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Wartość zmiennej animacji z końcem przejścia.|

## <a name="remarks"></a>Uwagi

Podczas przyspieszenia-spowalniania przejścia, zmienną animacji przyspiesza i spowalnia w czasie trwania przejścia, kończąc na określoną wartość. Można kontrolować, jak szybko zmienną przyspiesza i zwalnia niezależnie, określając różne przyspieszenie transmisji i współczynniki opóźnienia. Gdy prędkości początkowej wynosi zero, stosunek przyspieszenia jest część okresu, przez który spędzają zmiennej, przyspieszając; Podobnie za pomocą stosunek opóźnienia. Jeśli prędkości początkowej jest różna od zera, jest ułamku czasu między prędkości docieranie do zera i na końcu przejścia. Współczynnik przyspieszenie i współczynnik prędkości powinien Suma, umożliwiającej maksymalnie 1.0. Ponieważ wszystkie przejścia są automatycznie czyszczone, zaleca się ich przydzielone za pomocą nowego operatora. Zhermetyzowanego obiektu IUIAnimationTransition COM przy utworzono CAnimationController::AnimateGroup, aż do, a następnie ma wartość NULL. Zmienianie zmiennych składowych, po tworzenie ten obiekt COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Tworzy obiekt przejścia.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Wartość zmiennej animacji z końcem przejścia.

*accelerationRatio*<br/>
Stosunek czasu spędzanego w skróceniu czasu trwania.

*decelerationRatio*<br/>
Stosunek czasu spowolnienie do czasu trwania.

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejścia standardowe.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

Stosunek czasu spędzanego w skróceniu czasu trwania.

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

Stosunek czasu spowolnienie do czasu trwania.

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

Wartość zmiennej animacji z końcem przejścia.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
