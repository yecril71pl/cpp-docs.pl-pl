---
title: Klasa CBaseTransition
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 8339785fd10fa3dcef1c0fb573310762dc2d2405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352832"
---
# <a name="cbasetransition-class"></a>Klasa CBaseTransition

Reprezentuje przejście podstawowe.

## <a name="syntax"></a>Składnia

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-enumerations"></a>Wyliczenia publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE Wyliczenie](#transition_type_enumeration)|Definiuje typy przejścia obecnie obsługiwane przez implementację MFC interfejsu API animacji systemu Windows.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Konstruuje podstawowy obiekt przejścia.|
|[CBaseTransition::~CBaseTransition](#_dtorcbasetransition)|Destruktor. Wywoływane, gdy obiekt przejścia jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::Płyta AddToStory](#addtostoryboard)|Dodaje przejście do scenorysu.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Dodaje przejście do scenorysu.|
|[CBaseTransition::Wyczyść](#clear)|Zwalnia zhermetyzowany obiekt COM IUIAnimationTransition.|
|[CBaseTransition::Utwórz](#create)|Tworzy przejście COM.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Zwraca początkową klatkę kluczową.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Zwraca wskaźnik do zmiennej pokrewne.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Zwraca początkową klatkę kluczową.|
|[CBaseTransition::GetTransition](#gettransition)|Przeciążone. Zwraca wskaźnik do leżącego u podstaw obiektu przejścia COM.|
|[CBaseTransition::GetType](#gettype)|Zwraca typ przejścia.|
|[CBaseTransition::Isadded](#isadded)|Określa, czy przejście zostało dodane do scenorysu.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Ustawia klatki kluczowe dla przejścia.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Ustanawia relację między zmienną animacji a przejściem.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Określa, czy przejście zostało dodane do scenorysu.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Przechowuje wskaźnik do klatki kluczowej, który określa koniec przejścia.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Wskaźnik do zmiennej animacji, która jest animowana z przejściem przechowywanym w m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Przechowuje wskaźnik do klatki kluczowej, który określa początek przejścia.|
|[CBaseTransition::m_transition](#m_transition)|Przechowuje wskaźnik do IUIAnimationTransition. NULL, jeśli obiekt przejścia COM nie został utworzony.|
|[CBaseTransition::m_type](#m_type)|Przechowuje typ przejścia.|

## <a name="remarks"></a>Uwagi

Ta klasa hermetyzuje interfejs IUIAnimationTransition i służy jako klasa podstawowa dla wszystkich przejść.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition::~CBaseTransition

Destruktor. Wywoływane, gdy obiekt przejścia jest niszczony.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::Płyta AddToStory

Dodaje przejście do scenorysu.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do serii ujęć, który będzie animować powiązaną zmienną.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejście zostało pomyślnie dodane do scenorysu.

### <a name="remarks"></a>Uwagi

Stosuje przejście do zmiennej pokrewne w scenorysu. Jeśli jest to pierwsze przejście zastosowane do tej zmiennej w tym scenorysie, przejście rozpoczyna się na początku scenorysu. W przeciwnym razie przejście jest dołączane do przejścia dodanego ostatnio do zmiennej.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes

Dodaje przejście do scenorysu.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do serii ujęć, który będzie animować powiązaną zmienną.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejście zostało pomyślnie dodane do scenorysu.

### <a name="remarks"></a>Uwagi

Stosuje przejście do zmiennej pokrewne w scenorysu. Jeśli określono początkową klatkę kluczową, przejście rozpoczyna się od tej klatki kluczowej. Jeśli określono końcową klatkę kluczową, przejście rozpoczyna się od początkowej klatki kluczowej i zatrzymuje się na końcowej klatce kluczowej. Jeśli przejście zostało utworzone z określonym parametrem duration, ten czas trwania jest zastępowany wraz z czasem między klatkami kluczowymi początkowymi i końcowymi. Jeśli nie określono klatki kluczowej, przejście jest dołączane do przejścia dodanego ostatnio do zmiennej.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition

Konstruuje podstawowy obiekt przejścia.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Wyczyść

Zwalnia zhermetyzowany obiekt COM IUIAnimationTransition.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana z klasy pochodnej Create metody w celu zapobieżenia wycieku interfejsu IUITransition.

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Utwórz

Tworzy przejście COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do biblioteki przejścia, który tworzy przejścia standardowe. Może to być null dla przejść niestandardowych.

*pFactory (Fabryka)*<br/>
Wskaźnik do przejścia fabryki, który tworzy przejścia niestandardowe. Może to być null dla standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obiekt COM przejścia został utworzony pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jest to czysta funkcja wirtualna, która musi zostać zastąpiona w klasie pochodnej. Jest wywoływana przez platformę do tworzenia wystąpienia podstawowego obiektu przejścia COM.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe

Zwraca początkową klatkę kluczową.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do klatki kluczowej lub NULL, jeśli przejście nie powinno być wstawiane między klatkami kluczowymi.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do uzyskania dostępu do obiektu klatki kluczowej, który został wcześniej ustawiony przez SetKeyframes. Jest wywoływana przez kod najwyższego poziomu, gdy przejścia są dodawane do scenorysu.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable

Zwraca wskaźnik do zmiennej pokrewne.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do zmiennej animacji lub NULL, jeśli zmienna animacji nie została ustawiona przez SetRelatedVariable.

### <a name="remarks"></a>Uwagi

Jest to akcesor do powiązanej zmiennej animacji.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe

Zwraca początkową klatkę kluczową.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do klatki kluczowej lub NULL, jeśli przejście nie powinno się rozpocząć po klatce kluczowej.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do uzyskania dostępu do obiektu klatki kluczowej, który został wcześniej ustawiony przez SetKeyframes. Jest wywoływana przez kod najwyższego poziomu, gdy przejścia są dodawane do scenorysu.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition

Zwraca wskaźnik do leżącego u podstaw obiektu przejścia COM.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do biblioteki przejścia, który tworzy przejścia standardowe. Może to być null dla przejść niestandardowych.

*pFactory (Fabryka)*<br/>
Wskaźnik do przejścia fabryki, który tworzy przejścia niestandardowe. Może to być null dla standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do IUIAnimationTransition lub NULL, jeśli nie można utworzyć przejścia źródłowego.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wskaźnik do leżącego u podstaw obiektu przejścia COM i tworzy go w razie potrzeby.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType

Zwraca typ przejścia.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedną z TRANSITION_TYPE wyliczonych wartości.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do identyfikowania obiektu przejścia według jego typu. Typ jest ustawiany w konstruktorze w klasie pochodnej.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::Isadded

Określa, czy przejście zostało dodane do scenorysu.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli przejście zostało dodane do scenorysu, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta flaga jest ustawiana wewnętrznie, gdy kod najwyższego poziomu dodaje przejścia do scenorysu.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded

Określa, czy przejście zostało dodane do scenorysu.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe

Przechowuje wskaźnik do klatki kluczowej, który określa koniec przejścia.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable

Wskaźnik do zmiennej animacji, która jest animowana z przejściem przechowywanym w m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe

Przechowuje wskaźnik do klatki kluczowej, który określa początek przejścia.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBaseTransition::m_transition

Przechowuje wskaźnik do IUIAnimationTransition. NULL, jeśli obiekt przejścia COM nie został utworzony.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBaseTransition::m_type

Przechowuje typ przejścia.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes

Ustawia klatki kluczowe dla przejścia.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parametry

*pStart*<br/>
Klatka kluczowa określająca początek przejścia.

*Pend*<br/>
Klatka kluczowa określająca koniec przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda informuje przejście, aby rozpocząć po określonej klatce kluczowej i, opcjonalnie, jeśli pEnd nie jest null, zakończyć przed określoną klatkę kluczową. Jeśli przejście zostało utworzone z określonym parametrem duration, ten czas trwania jest zastępowany wraz z czasem między klatkami kluczowymi początkowymi i końcowymi.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable

Ustanawia relację między zmienną animacji a przejściem.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pWarienne*<br/>
Wskaźnik do powiązanej zmiennej animacji.

### <a name="remarks"></a>Uwagi

Ustanawia relację między zmienną animacji a przejściem. Przejście można zastosować tylko do jednej zmiennej.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE Wyliczenie

Definiuje typy przejścia obecnie obsługiwane przez implementację MFC interfejsu API animacji systemu Windows.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Uwagi

Typ przejścia jest ustawiany w konstruktorze określonego przejścia. Na przykład CSinusoidalTransitionFromRange ustawia swój typ na SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
