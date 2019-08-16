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
ms.openlocfilehash: b6bb626f944ce87748809a5eb03a6f06f92c3de5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507137"
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
|[CCubicTransition::CCubicTransition](#ccubictransition)|Konstruuje obiekt przejścia i inicjuje jego parametry.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCubicTransition:: Create](#create)|Wywołuje bibliotekę przejściową w celu utworzenia hermetyzowanego obiektu COM przejścia. (Przesłania [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|Szybkość zmiennej na końcu przejścia.|
|[CCubicTransition::m_duration](#m_duration)|Czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Podczas przejścia sześciennego wartość zmiennej animacji zmienia się z jej wartości początkowej na określoną wartość końcową w czasie trwania przejścia, kończąc na określonej prędkości. Ponieważ wszystkie przejścia są automatycznie wyczyszczone, zaleca się ich przydzielenie przy użyciu operatora new. Obiekt hermetyzowanych IUIAnimationTransition COM jest tworzony przez CAnimationController:: Animuj, do momentu, aż będzie miał wartość NULL. Zmiana zmiennych Członkowskich po utworzeniu tego obiektu COM nie ma żadnego skutku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller. h

##  <a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Konstruuje obiekt przejścia i inicjuje jego parametry.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*finalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

*finalVelocity*<br/>
Szybkość zmiennej na końcu przejścia.

##  <a name="create"></a>CCubicTransition:: Create

Wywołuje bibliotekę przejściową w celu utworzenia hermetyzowanego obiektu COM przejścia.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejść standardowych.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście zostało utworzone pomyślnie; w przeciwnym razie FALSE.

##  <a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

Szybkość zmiennej na końcu przejścia.

```
DOUBLE m_dblFinalVelocity;
```

##  <a name="m_duration"></a>CCubicTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
