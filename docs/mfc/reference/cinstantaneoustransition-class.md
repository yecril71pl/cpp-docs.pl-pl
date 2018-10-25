---
title: Klasa CInstantaneousTransition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
dev_langs:
- C++
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46fe01c3382f5f3667cbe909a5fb796bbb8ccc6f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062460"
---
# <a name="cinstantaneoustransition-class"></a>Klasa CInstantaneousTransition

Hermetyzuje natychmiastowe przejście.

## <a name="syntax"></a>Składnia

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Tworzy obiekt przejścia i inicjuje jego wartość końcową.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInstantaneousTransition::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji z końcem przejścia.|

## <a name="remarks"></a>Uwagi

Podczas natychmiastowe przejście wartość zmiennej animacji zmienia się natychmiast z jego bieżąca wartość określonej wartości końcowej. Czas trwania tego przejścia zawsze wynosi zero. Ponieważ wszystkie przejścia są automatycznie czyszczone, zaleca się ich przydzielone za pomocą nowego operatora. Zhermetyzowanego obiektu IUIAnimationTransition COM przy utworzono CAnimationController::AnimateGroup, aż do, a następnie ma wartość NULL. Zmienianie zmiennych składowych, po tworzenie ten obiekt COM nie ma wpływu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="cinstantaneoustransition"></a>  CInstantaneousTransition::CInstantaneousTransition

Tworzy obiekt przejścia i inicjuje jego wartość końcową.

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parametry

*dblFinalValue*<br/>
Wartość zmiennej animacji z końcem przejścia.

##  <a name="create"></a>  CInstantaneousTransition::Create

Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejścia standardowe.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="m_dblfinalvalue"></a>  CInstantaneousTransition::m_dblFinalValue

Wartość zmiennej animacji z końcem przejścia.

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
