---
title: Klasa CCubicTransition
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369346"
---
# <a name="ccubictransition-class"></a>Klasa CCubicTransition

Hermetyzuje przejście sześcienne.

## <a name="syntax"></a>Składnia

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|Konstruuje obiekt przejściowy i inicjuje jego parametry.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCubicTransition::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|Prędkość zmiennej na końcu przejścia.|
|[CCubicTransition::m_duration](#m_duration)|Czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Podczas przejścia sześciennego wartość zmiennej animacji zmienia się z jego wartości początkowej na określoną wartość końcową w czasie trwania przejścia, kończąc na określonej prędkości. Ponieważ wszystkie przejścia są czyszczone automatycznie, zaleca się przydzielenie ich przy użyciu nowego operatora. Zhermetyzowany obiekt COM IUIAnimationTransition jest tworzony przez CAnimationController::AnimateGroup, do tego czasu jest null. Zmiana zmiennych członkowskich po utworzeniu tego obiektu COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Konstruuje obiekt przejściowy i inicjuje jego parametry.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

*finałVelocity*<br/>
Prędkość zmiennej na końcu przejścia.

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Tworzenie

Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejście zostanie utworzone pomyślnie; w przeciwnym razie FALSE.

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

Prędkość zmiennej na końcu przejścia.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubicTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
