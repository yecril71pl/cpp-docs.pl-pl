---
title: Klasa CSmoothStopTransition
ms.date: 11/04/2016
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
ms.openlocfilehash: 89496c1b867d6fbb498f56271de7b45afef7edc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323885"
---
# <a name="csmoothstoptransition-class"></a>Klasa CSmoothStopTransition

Hermetyzuje gładkie zatrzymanie przejścia.

## <a name="syntax"></a>Składnia

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|Gładkie zatrzymanie przejścia tworzy i inicjuje jego maksymalny czas trwania i końcowa wartość.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji z końcem przejścia.|
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|Maksymalny czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Gładkie zatrzymanie przejścia spowalnia zbliża się do danej wartości końcowej i osiągnie on z prędkości o wartości zero. Czas trwania przejścia zależy od prędkości początkowej różnicę wartości początkowe i końcowe i określony maksymalny czas trwania. Jeśli nie ma żadnego rozwiązania składający się z pojedynczego łuk paraboliczne, ta metoda tworzy sześcienne przejścia. Ponieważ wszystkie przejścia są automatycznie czyszczone, zaleca się ich przydzielone za pomocą nowego operatora. Zhermetyzowanego obiektu IUIAnimationTransition COM przy utworzono CAnimationController::AnimateGroup, aż do, a następnie ma wartość NULL. Zmienianie zmiennych składowych, po tworzenie ten obiekt COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="create"></a>  CSmoothStopTransition::Create

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

##  <a name="csmoothstoptransition"></a>  CSmoothStopTransition::CSmoothStopTransition

Gładkie zatrzymanie przejścia tworzy i inicjuje jego maksymalny czas trwania i końcowa wartość.

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*maximumDuration*<br/>
Maksymalny czas trwania przejścia.

*dblFinalValue*<br/>
Wartość zmiennej animacji z końcem przejścia.

##  <a name="m_dblfinalvalue"></a>  CSmoothStopTransition::m_dblFinalValue

Wartość zmiennej animacji z końcem przejścia.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_maximumduration"></a>  CSmoothStopTransition::m_maximumDuration

Maksymalny czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
