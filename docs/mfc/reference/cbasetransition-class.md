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
ms.openlocfilehash: 37bf536403d0edfc16b098929a4758a6c6958cf1
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565912"
---
# <a name="cbasetransition-class"></a>Klasa CBaseTransition

Przedstawia przejście podstawowe.

## <a name="syntax"></a>Składnia

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-enumerations"></a>Wyliczenia publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wyliczenie CBaseTransition::TRANSITION_TYPE](#transition_type_enumeration)|Definiuje typy przejścia są obecnie obsługiwane przez interfejs API animacji Windows implementacji MFC.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Tworzy obiekt podstawowy przejścia.|
|[CBaseTransition:: ~ CBaseTransition](#_dtorcbasetransition)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt przejścia.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Dodaje przejścia do scenorysu.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Dodaje przejścia do scenorysu.|
|[CBaseTransition::Clear](#clear)|Wersje hermetyzowany obiektu IUIAnimationTransition COM.|
|[CBaseTransition::Create](#create)|Tworzy przejście COM.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Zwraca start klatki kluczowej.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Zwraca wskaźnik do zmiennej powiązanej.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Zwraca start klatki kluczowej.|
|[CBaseTransition::GetTransition](#gettransition)|Przeciążone. Zwraca wskaźnik do podstawowego obiektu przejścia COM.|
|[CBaseTransition::GetType](#gettype)|Zwraca wartość typu przejścia.|
|[CBaseTransition::IsAdded](#isadded)|Informuje, czy przejście zostały dodane do scenorysu.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Ustawia klatki kluczowe przejścia.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Ustanawia relację między zmiennej animacji i przejść.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Określa, czy przejście zostały dodane do scenorysu.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Przechowuje wskaźnik do ramki kluczowej, który określa koniec przejścia.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Wskaźnik do zmiennej animacji, która jest animowany z przejściem przechowywane w m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Przechowuje wskaźnik do ramki kluczowej, która określa początek przejścia.|
|[CBaseTransition::m_transition](#m_transition)|Przechowuje wskaźnik do IUIAnimationTransition. Wartość NULL, jeśli nie został utworzony obiekt COM przejścia.|
|[CBaseTransition::m_type](#m_type)|Przechowuje typ przejścia.|

## <a name="remarks"></a>Uwagi

Ta klasa hermetyzuje interfejs IUIAnimationTransition i służy jako klasa bazowa dla wszystkich przejść.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="_dtorcbasetransition"></a>  CBaseTransition:: ~ CBaseTransition

Destruktor. Wywołuje się, kiedy niszczony jest obiekt przejścia.

```
virtual ~CBaseTransition();
```

##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard

Dodaje przejścia do scenorysu.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu, który będzie animować powiązane zmiennej.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście zostało pomyślnie dodane do scenorysu.

### <a name="remarks"></a>Uwagi

Ma zastosowanie przejścia do zmiennych powiązanych z scenorysu. Jeśli jest to pierwsze przejście zastosowany do zmiennej w tym scenorysem, przejście rozpoczyna się na początku tego scenorysu. W przeciwnym razie przejścia jest dołączany do którego nastąpi przejście, ostatnio dodana do zmiennej.

##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes

Dodaje przejścia do scenorysu.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu, który będzie animować powiązane zmiennej.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście zostało pomyślnie dodane do scenorysu.

### <a name="remarks"></a>Uwagi

Ma zastosowanie przejścia do zmiennych powiązanych z scenorysu. Jeśli określono klatki kluczowej rozpoczęcia przejścia rozpoczyna się od tej ramki kluczowej. Jeśli określono klatki kluczowej zakończenia, przejście rozpoczyna się od ramki kluczowej start i zatrzymuje się na ramki kluczowej zakończenia. Jeśli przejście został utworzony za pomocą parametru czasu trwania określony, ten czas jest zastępowany czas pomiędzy klatkami kluczowymi rozpoczęcia i zakończenia. Jeśli nie określono żadnych klatki kluczowej, przejście jest dołączany do przejścia ostatnio dodana do zmiennej.

##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition

Tworzy obiekt podstawowy przejścia.

```
CBaseTransition();
```

##  <a name="clear"></a>  CBaseTransition::Clear

Wersje hermetyzowany obiektu IUIAnimationTransition COM.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Ta metoda powinna być wywoływana z metody tworzenia klasy pochodnej, aby uniknąć przecieku interfejsu IUITransition.

##  <a name="create"></a>  CBaseTransition::Create

Tworzy przejście COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do przejścia biblioteki, która tworzy przejścia standardowe. Może być NULL dla niestandardowych przejść.

*pFactory*<br/>
Wskaźnik do przejścia factory, która tworzy niestandardowe przejścia. Może być NULL dla przejścia standardowe.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejście obiektu COM został pomyślnie utworzony; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

To jest czysta funkcja wirtualna, która musi zostać zastąpiona w klasie pochodnej. Jest ona wywoływana przez platformę, by wystąpienia podstawowego obiektu modelu COM w przejścia.

##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe

Zwraca start klatki kluczowej.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do ramki kluczowej lub wartość NULL, jeśli nie można wstawić przejścia pomiędzy klatkami kluczowymi.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do dostępu do obiektu klatki kluczowej, która wcześniej została ustawiona przez SetKeyframes. Jest on wywoływany przez kod najwyższego poziomu, podczas przejścia są dodawane do scenorysu.

##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable

Zwraca wskaźnik do zmiennej powiązanej.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do zmiennej animacji lub wartość NULL, jeśli nie ustawiono zmienną animacji przez SetRelatedVariable.

### <a name="remarks"></a>Uwagi

Jest to metoda dostępu do zmiennej animacji powiązane.

##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe

Zwraca start klatki kluczowej.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do ramki kluczowej lub wartość NULL, jeśli przejście nie powinna być uruchamiana po klatki kluczowej.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do dostępu do obiektu klatki kluczowej, która wcześniej została ustawiona przez SetKeyframes. Jest on wywoływany przez kod najwyższego poziomu, podczas przejścia są dodawane do scenorysu.

##  <a name="gettransition"></a>  CBaseTransition::GetTransition

Zwraca wskaźnik do podstawowego obiektu przejścia COM.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do przejścia biblioteki, która tworzy przejścia standardowe. Może być NULL dla niestandardowych przejść.

*pFactory*<br/>
Wskaźnik do przejścia factory, która tworzy niestandardowe przejścia. Może być NULL dla przejścia standardowe.

### <a name="return-value"></a>Wartość zwracana

Nie można utworzyć prawidłowego wskaźnika do IUIAnimationTransition lub wartość NULL, jeśli podstawowy przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wskaźnik do podstawowego obiektu przejścia COM i utworzy go, jeśli to konieczne.

##  <a name="gettype"></a>  CBaseTransition::GetType

Zwraca wartość typu przejścia.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedną z TRANSITION_TYPE wyliczonych wartości.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do identyfikowania obiektów przejście od jego typu. Typ jest ustawiany w konstruktorze klasy pochodnej.

##  <a name="isadded"></a>  CBaseTransition::IsAdded

Informuje, czy przejście zostały dodane do scenorysu.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli dodano przejścia do scenorysu, w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta flaga jest ustawiona wewnętrznie, gdy najwyższego poziomu kodu dodaje przejścia do scenorysu.

##  <a name="m_badded"></a>  CBaseTransition::m_bAdded

Określa, czy przejście zostały dodane do scenorysu.

```
BOOL m_bAdded;
```

##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe

Przechowuje wskaźnik do ramki kluczowej, który określa koniec przejścia.

```
CBaseKeyFrame* m_pEndKeyframe;
```

##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable

Wskaźnik do zmiennej animacji, która jest animowany z przejściem przechowywane w m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe

Przechowuje wskaźnik do ramki kluczowej, która określa początek przejścia.

```
CBaseKeyFrame* m_pStartKeyframe;
```

##  <a name="m_transition"></a>  CBaseTransition::m_transition

Przechowuje wskaźnik do IUIAnimationTransition. Wartość NULL, jeśli nie został utworzony obiekt COM przejścia.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

##  <a name="m_type"></a>  CBaseTransition::m_type

Przechowuje typ przejścia.

```
TRANSITION_TYPE m_type;
```

##  <a name="setkeyframes"></a>  CBaseTransition::SetKeyframes

Ustawia klatki kluczowe przejścia.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parametry

*pStart*<br/>
Klatki kluczowej, która określa początek przejścia.

*pEnd*<br/>
Kluczową Określa koniec przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda informuje o przejście do uruchamia się po określonym ramki kluczowej i, opcjonalnie, jeśli oczekują nie ma wartość NULL, zakończyć przed określonym klatki kluczowej. Jeśli przejście został utworzony za pomocą parametru czasu trwania określony, ten czas jest zastępowany czas pomiędzy klatkami kluczowymi rozpoczęcia i zakończenia.

##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable

Ustanawia relację między zmiennej animacji i przejść.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Wskaźnik do zmiennej animacji powiązane.

### <a name="remarks"></a>Uwagi

Ustanawia relację między zmiennej animacji i przejść. Przejścia może być stosowane tylko do jednej zmiennej.

##  <a name="transition_type_enumeration"></a>  Wyliczenie CBaseTransition::TRANSITION_TYPE

Definiuje typy przejścia są obecnie obsługiwane przez interfejs API animacji Windows implementacji MFC.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Uwagi

Typ przejścia znajduje się w Konstruktorze określonego przejścia. Na przykład CSinusoidalTransitionFromRange ustawia SINUSOIDAL_FROM_RANGE jego typu.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
