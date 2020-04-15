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
ms.openlocfilehash: 0ba550b4a0b9443d0681e17195687fb94c207ace
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318205"
---
# <a name="csmoothstoptransition-class"></a>Klasa CSmoothStopTransition

Hermetyzuje przejście z płynnym zatrzymywania.

## <a name="syntax"></a>Składnia

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|Konstruuje przejście smooth-stop i inicjuje jego maksymalny czas trwania i wartość końcową.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|Maksymalny czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Przejście smooth-stop spowalnia, gdy zbliża się do danej wartości końcowej i osiąga ją z prędkością zero. Czas trwania przejścia jest określany przez prędkość początkową, różnicę między wartościami początkowymi i końcowymi oraz określony maksymalny czas trwania. Jeśli nie ma rozwiązania składającego się z pojedynczego łuku parabolicznego, ta metoda tworzy przejście sześcienne. Ponieważ wszystkie przejścia są czyszczone automatycznie, zaleca się przydzielenie ich przy użyciu nowego operatora. Zhermetyzowany obiekt COM IUIAnimationTransition jest tworzony przez CAnimationController::AnimateGroup, do tego czasu jest null. Zmiana zmiennych członkowskich po utworzeniu tego obiektu COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition (Tłumaczenie CSmoothStopTransition)](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="csmoothstoptransitioncreate"></a><a name="create"></a>CSmoothStopTransition::Tworzenie

Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do biblioteki przejścia, który jest odpowiedzialny za tworzenie standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejście zostanie utworzone pomyślnie; w przeciwnym razie FALSE.

## <a name="csmoothstoptransitioncsmoothstoptransition"></a><a name="csmoothstoptransition"></a>CSmoothStopTransition::CSmoothStopTransition

Konstruuje przejście smooth-stop i inicjuje jego maksymalny czas trwania i wartość końcową.

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*maksymalnaduracjonalna*<br/>
Maksymalny czas trwania przejścia.

*dblFinalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

## <a name="csmoothstoptransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CSmoothStopTransition::m_dblFinalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_dblFinalValue;
```

## <a name="csmoothstoptransitionm_maximumduration"></a><a name="m_maximumduration"></a>CSmoothStopTransition::m_maximumDuration

Maksymalny czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
