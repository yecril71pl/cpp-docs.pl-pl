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
ms.openlocfilehash: 76e0d12308ad579e4bdf9866dfcf1cde231a2d0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749153"
---
# <a name="ccustomtransition-class"></a>Klasa CCustomTransition

Implementuje przejście niestandardowe.

## <a name="syntax"></a>Składnia

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Konstruuje niestandardowy obiekt przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::Tworzenie](#create)|Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia. (Zastępuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Ustawia wartość początkową, która zostanie zastosowana do zmiennej animacji skojarzonej z tym przejściem.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Ustawia prędkość początkową, która zostanie zastosowana do zmiennej animacji skojarzonej z tym przejściem.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Określa, czy wartość początkowa została określona za pomocą Wartości SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Określa, czy prędkość początkowa została określona za pomocą SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Przechowuje wartość początkową.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Przechowuje prędkość początkową.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Przechowuje wskaźnik do niestandardowego interpolatora.|

## <a name="remarks"></a>Uwagi

Klasa CCustomTransitions umożliwia deweloperom implementowanie przejść niestandardowych. Jest tworzony i używany jako standardowe przejście, ale jego konstruktor akceptuje jako parametr wskaźnik do niestandardowego interpolatora. Wykonaj następujące kroki, aby użyć przejść niestandardowych: 1. Wywodź klasę z CCustomInterpolator i zaimplementuj co najmniej Metodę InterpolateValue. 2. Upewnij się, że okres istnienia niestandardowego obiektu interpolatora musi być dłuższy niż czas trwania animacji, w którym jest używany. 3. Wystąpienia (przy użyciu operatora nowy) CCustomTransition obiektu i przekazać wskaźnik do niestandardowego interpolatora w konstruktorze. 4. Wywołanie CCustomTransition::SetInitialValue i CCustomTransition::SetInitialVelocity jeśli te parametry są wymagane dla interpolacji niestandardowej. 5. Przekaż wskaźnik do przejścia niestandardowego do AddTransition metody obiektu animacji, którego wartość powinna być animowana za pomocą algorytmu niestandardowego. 6. Kiedy wartość obiektu animacji należy zmienić interfejs API animacji systemu Windows wywoła InterpolateValue (i inne odpowiednie metody) w CCustomInterpolator.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition (Transport baz)](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition

Konstruuje niestandardowy obiekt przejścia.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Wskaźnik do niestandardowego interpolatora.

## <a name="ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Tworzenie

Wywołuje bibliotekę przejściową w celu utworzenia zhermetyzowanego obiektu COM przejścia.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parametry

*pFactory (Fabryka)*<br/>
Wskaźnik do przejścia fabryki, który jest odpowiedzialny za tworzenie przejść niestandardowych.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Ta metoda może również ustawić wartość początkową i prędkość początkową, które mają być stosowane do zmiennej animacji, która jest skojarzona z tym przejściem. W tym celu należy wywołać SetInitialValue i SetInitialVelocity przed ramą tworzy zhermetyzowany obiekt COM przejścia (dzieje się tak po wywołaniu CAnimationController::AnimateGroup).

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified

Określa, czy wartość początkowa została określona za pomocą Wartości SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified

Określa, czy prędkość początkowa została określona za pomocą SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue

Przechowuje wartość początkową.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity

Przechowuje prędkość początkową.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator

Przechowuje wskaźnik do niestandardowego interpolatora.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue

Ustawia wartość początkową, która zostanie zastosowana do zmiennej animacji skojarzonej z tym przejściem.

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parametry

*wartość początkowa*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity

Ustawia prędkość początkową, która zostanie zastosowana do zmiennej animacji skojarzonej z tym przejściem.

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*początkowaVelocity*

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
