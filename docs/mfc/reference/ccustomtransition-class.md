---
title: Klasa CCustomTransition
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: e0e5250b27ce6b902939ebcbfa03bf022a202788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391286"
---
# <a name="ccustomtransition-class"></a>Klasa CCustomTransition

Implementuje niestandardowe przejścia.

## <a name="syntax"></a>Składnia

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Tworzy obiekt niestandardowe przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Ustawia wartość początkową, które mają zostać zastosowane do skojarzonych z tym przejściem zmiennej animacji.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Ustawia prędkości początkowej, które mają zostać zastosowane do skojarzonych z tym przejściem zmiennej animacji.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Określa, czy wartość początkowa została określona za pomocą SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Określa, czy z SetInitialVelocity określono prędkości początkowej.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Przechowuje wartość początkową.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Przechowuje prędkości początkowej.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Przechowuje wskaźnik do interpolatora niestandardowych.|

## <a name="remarks"></a>Uwagi

Klasa CCustomTransitions umożliwia deweloperom implementuje niestandardowe przejścia. Utworzona i używany jako standardowy przejścia, ale jego Konstruktor akceptuje jako parametru wskaźnika do interpolatora niestandardowych. Wykonaj poniższe kroki, aby użyć niestandardowego przejścia: 1. Wyprowadzenia klasy z CCustomInterpolator i wdrożenie co najmniej InterpolateValue metody. 2. Upewnij się, że okres istnienia obiektu niestandardowego interpolatora musi być dłuższy niż czas trwania animacji gdzie jest używany. 3. Utwórz wystąpienie (nowe za pomocą operatora) obiektu CCustomTransition i przekazać wskaźnik do niestandardowych interpolatora w konstruktorze. 4. Jeśli te parametry są wymagane do interpolacji niestandardowe, należy wywołać CCustomTransition::SetInitialValue i CCustomTransition::SetInitialVelocity. 5. Zatrzymaj wskaźnik myszy na niestandardowe przejścia do metody AddTransition obiektu animacji, w których wartość powinna być animowane za pomocą niestandardowego algorytmu. 6. Gdy wartość obiektu animacji, należy zmienić interfejs API animacji Windows będzie wywoływać w CCustomInterpolator InterpolateValue (i inne odpowiednie metody).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

Tworzy obiekt niestandardowe przejścia.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do interpolatora niestandardowych.

##  <a name="create"></a>  CCustomTransition::Create

Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Wskaźnik do przejścia factory, która jest odpowiedzialna za tworzenie niestandardowe przejścia.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Tę metodę można również ustawić wartości początkowej oraz prędkości początkowej ma zostać zastosowany do zmiennej animacji, która jest skojarzona z tego przejścia. W tym celu należy wywołać SetInitialValue SetInitialVelocity przed szablon tworzy przejścia zhermetyzowanego obiektu COM (wykonywane po wywołaniu CAnimationController::AnimateGroup).

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

Określa, czy wartość początkowa została określona za pomocą SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

Określa, czy z SetInitialVelocity określono prędkości początkowej.

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

Przechowuje wartość początkową.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

Przechowuje prędkości początkowej.

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

Przechowuje wskaźnik do interpolatora niestandardowych.

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

Ustawia wartość początkową, które mają zostać zastosowane do skojarzonych z tym przejściem zmiennej animacji.

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parametry

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

Ustawia prędkości początkowej, które mają zostać zastosowane do skojarzonych z tym przejściem zmiennej animacji.

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialVelocity*

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
