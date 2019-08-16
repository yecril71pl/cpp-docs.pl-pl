---
title: Klasa CLinearTransition
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: 1a6348d1afd0117683bd31af61324b14e16f710c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505742"
---
# <a name="clineartransition-class"></a>Klasa CLinearTransition

Hermetyzuje przejście liniowe.

## <a name="syntax"></a>Składnia

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransition::CLinearTransition](#clineartransition)|Konstruuje obiekt przejścia liniowego i inicjuje go z czasem trwania i wartością końcową.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransition:: Create](#create)|Wywołuje bibliotekę przejściową w celu utworzenia hermetyzowanego obiektu COM przejścia. (Przesłania [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|
|[CLinearTransition::m_duration](#m_duration)|Czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Podczas przejścia liniowego wartość zmiennej animacji przechodzi liniowo od wartości początkowej do określonej wartości końcowej. Ponieważ wszystkie przejścia są automatycznie wyczyszczone, zaleca się ich przydzielenie przy użyciu operatora new. Obiekt hermetyzowanych IUIAnimationTransition COM jest tworzony przez CAnimationController:: Animuj, do momentu, aż będzie miał wartość NULL. Zmiana zmiennych Członkowskich po utworzeniu tego obiektu COM nie ma żadnego skutku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller. h

##  <a name="clineartransition"></a>CLinearTransition::CLinearTransition

Konstruuje obiekt przejścia liniowego i inicjuje go z czasem trwania i wartością końcową.

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Czas trwania przejścia.

*dblFinalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

##  <a name="create"></a>CLinearTransition:: Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransition::m_dblFinalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_duration"></a>CLinearTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
