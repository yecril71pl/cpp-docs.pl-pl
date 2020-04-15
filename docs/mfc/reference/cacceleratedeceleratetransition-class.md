---
title: Klasa CAccelerateDecelerateTransition
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371146"
---
# <a name="cacceleratedeceleratetransition-class"></a>Klasa CAccelerateDecelerateTransition

Implementuje przyspieszenie-spowolnienie przejścia.

## <a name="syntax"></a>Składnia

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Konstruuje obiekt przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Stosunek czasu spędzonego na przyspieszaniu do czasu trwania.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Stosunek czasu spędzonego na zwalnianiu do czasu trwania.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Czas trwania przejścia.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Wartość zmiennej animacji na końcu przejścia.|

## <a name="remarks"></a>Uwagi

Podczas przejścia przyspieszania i zwalniania zmienna animacji przyspiesza, a następnie spowalnia w czasie trwania przejścia, kończąc na określonej wartości. Można kontrolować, jak szybko zmienna przyspiesza i spowalnia niezależnie, określając różne współczynniki przyspieszenia i spowolnienia. Gdy prędkość początkowa wynosi zero, współczynnik przyspieszenia jest ułamkiem czasu trwania, który zmienna spędzi na przyspieszaniu; podobnie ze wskaźnikiem spowolnienia. Jeśli prędkość początkowa jest niezerowa, jest to ułamek czasu między prędkością osiągającą zero a końcem przejścia. Współczynnik przyspieszenia i współczynnik spowolnienia powinny wynosić maksymalnie 1,0. Ponieważ wszystkie przejścia są czyszczone automatycznie, zaleca się przydzielenie ich przy użyciu nowego operatora. Zhermetyzowany obiekt COM IUIAnimationTransition jest tworzony przez CAnimationController::AnimateGroup, do tego czasu jest null. Zmiana zmiennych członkowskich po utworzeniu tego obiektu COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Konstruuje obiekt przejścia.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

*przyspieszenieRatio*<br/>
Stosunek czasu spędzonego na przyspieszaniu do czasu trwania.

*zwalnianieRatio*<br/>
Stosunek czasu spędzonego na zwalnianiu do czasu trwania.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Tworzenie

Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejście zostanie utworzone pomyślnie; w przeciwnym razie FALSE.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio

Stosunek czasu spędzonego na przyspieszaniu do czasu trwania.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

Stosunek czasu spędzonego na zwalnianiu do czasu trwania.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
