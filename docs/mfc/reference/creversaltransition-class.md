---
title: Klasa CReversalTransition
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368316"
---
# <a name="creversaltransition-class"></a>Klasa CReversalTransition

Hermetyzuje przejście odwrócenia.

## <a name="syntax"></a>Składnia

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Konstruuje obiekt przejścia odwrócenia i inicjuje jego czas trwania.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CReversalTransition::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|Czas trwania przejścia.|

## <a name="remarks"></a>Uwagi

Przejście odwrócenia płynnie zmienia kierunek w danym czasie trwania. Wartość końcowa będzie taka sama jak wartość początkowa, a prędkość końcowa będzie ujemna od prędkości początkowej. Ponieważ wszystkie przejścia są czyszczone automatycznie, zaleca się przydzielenie ich przy użyciu nowego operatora. Zhermetyzowany obiekt COM IUIAnimationTransition jest tworzony przez CAnimationController::AnimateGroup, do tego czasu jest null. Zmiana zmiennych członkowskich po utworzeniu tego obiektu COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition (Polski)](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>CReversalTransition::Tworzenie

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

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>CReversalTransition::CReversalTransition

Konstruuje obiekt przejścia odwrócenia i inicjuje jego czas trwania.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Długość*<br/>
Czas trwania przejścia.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>CReversalTransition::m_duration

Czas trwania przejścia.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
