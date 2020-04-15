---
title: Klasa CLinearTransitionFromSpeed
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 31c04c303e7e253ec4de41bf076130d19232aac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372265"
---
# <a name="clineartransitionfromspeed-class"></a>Klasa CLinearTransitionFromSpeed

Hermetyzuje przejście liniowej prędkości.

## <a name="syntax"></a>Składnia

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed CLinearTransitionFromSpeed CLinearTransitionFrom](#clineartransitionfromspeed)|Konstruuje obiekt przejścia z prędkością liniową i inicjuje go z szybkością i wartością końcową.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|Wartość bezwzględna prędkości zmiennej.|

## <a name="remarks"></a>Uwagi

Podczas przejścia z prędkością liniową wartość zmiennej animacji zmienia się z określoną szybkością. Czas trwania przejścia jest określany przez różnicę między wartością początkową a określoną wartością końcową. Ponieważ wszystkie przejścia są czyszczone automatycznie, zaleca się przydzielenie ich przy użyciu nowego operatora. Zhermetyzowany obiekt COM IUIAnimationTransition jest tworzony przez CAnimationController::AnimateGroup, do tego czasu jest null. Zmiana zmiennych członkowskich po utworzeniu tego obiektu COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionOdPeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed::CLinearTransitionFromSpeed CLinearTransitionFromSpeed CLinearTransitionFrom

Konstruuje obiekt przejścia z prędkością liniową i inicjuje go z szybkością i wartością końcową.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*dblSpeed (prędkość)*<br/>
Wartość bezwzględna prędkości zmiennej.

*dblFinalValue*<br/>
Wartość zmiennej animacji na końcu przejścia.

## <a name="clineartransitionfromspeedcreate"></a><a name="create"></a>CLinearTransitionFromSpeed::Tworzenie

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

## <a name="clineartransitionfromspeedm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed::m_dblFinalValue

Wartość zmiennej animacji na końcu przejścia.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionfromspeedm_dblspeed"></a><a name="m_dblspeed"></a>CLinearTransitionFromSpeed::m_dblSpeed

Wartość bezwzględna prędkości zmiennej.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
