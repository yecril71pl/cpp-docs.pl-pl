---
title: Klasa CAnimationGroup
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 32b2adfee2a36139a11caa12fa98bd240b0732dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152080"
---
# <a name="canimationgroup-class"></a>Klasa CAnimationGroup

Implementuje grupę animacji, która łączy scenorysu animacji, obiektów w animacji i przejść do definiowania animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationGroup;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Tworzy grupę animacji.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|Destruktor. Wywołuje się, kiedy niszczony jest grupą animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Animuje grupy.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Ma zastosowanie przejścia do obiektów w animacji.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Znajduje obiekt animacji, który zawiera zmienną animacji określony.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Zwraca identyfikator grupy.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Usuwa i opcjonalnie niszczy wszystkich ramkami kluczowymi, które należą do grupy animacji.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Usuwa przejścia z obiektów w animacji, które należą do grupy animacji.|
|[CAnimationGroup::Schedule](#schedule)|Planuje animacji o określonej godzinie.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Określa, że wszystkich obiektów w animacji, które należą do grupy automatycznie zniszczyć przejścia.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocniczy, który dodaje klatki kluczowe do scenorysu.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocniczy, który dodaje przejścia do scenorysu.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocniczy, który tworzy obiekty przejścia COM.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Określa, jak wyczyścić przejścia z obiektów w animacji, które należą do grupy. Jeśli ten element członkowski ma wartość TRUE, przejścia są usuwane automatycznie, gdy zaplanowano animacji. W przeciwnym razie należy ręcznie usunąć przejścia.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Określa, jak można zniszczyć obiektów w animacji. Jeśli ten parametr ma wartość TRUE, obiektów w animacji zostanie automatycznie niszczony, kiedy niszczony jest grupy. W przeciwnym razie obiektów w animacji musi zostać zniszczona, ręcznie. Wartość domyślna to FALSE. Wartość tę należy ustawić na wartość TRUE tylko wtedy, gdy wszystkich obiektów w animacji, które należą do grupy są dynamicznie przydzielane za pomocą nowego operatora.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Określa, jak można zniszczyć ramek kluczowych. Jeśli ta wartość wynosi TRUE, wszystkie klatki kluczowe są usuwane i zniszczone; w przeciwnym razie są usuwane z listy tylko. Wartość domyślna to TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Zawiera listę obiektów w animacji.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Zawiera listę ramek kluczowych.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Wskazuje scenorysu animacji. This, wskaźnik jest prawidłowy tylko po wywołanie Animate.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Unikatowy identyfikator grupy animacji.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Wskaźnik do Kontroler animacji, do której należy ta grupa.|

## <a name="remarks"></a>Uwagi

Animacja grupy są tworzone automatycznie przez kontroler animacji (CAnimationController) podczas dodawania obiektów w animacji przy użyciu CAnimationController::AddAnimationObject. Grupa animacji jest identyfikowana przez identyfikator grupy, w której są zwykle pobierane jako parametr do manipulowania grupami animacji. Identyfikator grupy jest pobierana z pierwszego obiektu animacji, dodawane do nowej grupy animacji. Scenorysu zhermetyzowany animacji jest tworzony po wywołać CAnimationController::AnimateGroup i możliwy za pośrednictwem m_pStoryboard publicznego elementu członkowskiego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAnimationGroup`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup:: ~ CAnimationGroup

Destruktor. Wywołuje się, kiedy niszczony jest grupą animacji.

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

Pomocniczy, który dodaje klatki kluczowe do scenorysu.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do obiektu COM scenorysu.

*bAddDeep*<br/>
Określa, czy tej metody należy dodać do scenorysu ramkami kluczowymi, które są zależne od innych klatek kluczowych.

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

Pomocniczy, który dodaje przejścia do scenorysu.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do obiektu COM scenorysu.

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

Animuje grupy.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy scenorys wewnętrznego, tworzy i ma zastosowanie przejścia i planuje animacji, gdy bScheduleNow jest wartość PRAWDA. Jeśli bScheduleNow ma wartość FALSE, należy wywołać harmonogram Rozpocznij animację o określonej godzinie.

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

Ma zastosowanie przejścia do obiektów w animacji.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Uwagi

Ta metoda potwierdza w trybie debugowania, jeśli nie utworzono scenorysu. Go najpierw tworzy wszystkie przejścia, a następnie dodaje "statyczne" klatek kluczowych (ramek kluczowych, które są zależne od przesunięcia), dodaje przejścia, które nie są zależne od ramkami kluczowymi, dodaje ramkami kluczowymi, w zależności od przejścia i innych klatek kluczowych i ostatnio dodaje przejść, które są zależne od klatek kluczowych .

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

Tworzy grupę animacji.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*pParentController*<br/>
Wskaźnik na kontroler animacji, który tworzy grupę.

*nGroupID*<br/>
Określa identyfikator grupy.

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

Pomocniczy, który tworzy obiekty przejścia COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE jest metoda się powiedzie, w przeciwnym razie wartość FALSE.

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

Znajduje obiekt animacji, który zawiera zmienną animacji określony.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Wskaźnik do zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu animacji, lub wartość NULL, jeśli nie można odnaleźć obiektu animacji.

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

Zwraca identyfikator grupy.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator grupy.

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

Określa, jak wyczyścić przejścia z obiektów w animacji, które należą do grupy. Jeśli ten element członkowski ma wartość TRUE, przejścia są usuwane automatycznie, gdy zaplanowano animacji. W przeciwnym razie należy ręcznie usunąć przejścia.

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

Określa, jak można zniszczyć obiektów w animacji. Jeśli ten parametr ma wartość TRUE, obiektów w animacji zostanie automatycznie niszczony, kiedy niszczony jest grupy. W przeciwnym razie obiektów w animacji musi zostać zniszczona, ręcznie. Wartość domyślna to FALSE. Wartość tę należy ustawić na wartość TRUE tylko wtedy, gdy wszystkich obiektów w animacji, które należą do grupy są dynamicznie przydzielane za pomocą nowego operatora.

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

Określa, jak można zniszczyć ramek kluczowych. Jeśli ta wartość wynosi TRUE, wszystkie klatki kluczowe są usuwane i zniszczone; w przeciwnym razie są usuwane z listy tylko. Wartość domyślna to TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

Zawiera listę obiektów w animacji.

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

Zawiera listę ramek kluczowych.

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

Unikatowy identyfikator grupy animacji.

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

Wskaźnik do Kontroler animacji, do której należy ta grupa.

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

Wskazuje scenorysu animacji. This, wskaźnik jest prawidłowy tylko po wywołanie Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

Usuwa i opcjonalnie niszczy wszystkich ramkami kluczowymi, które należą do grupy animacji.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Uwagi

Jeśli element członkowski m_bAutodestroyKeyframes ma wartość TRUE, a ramki kluczowe są usuwane zniszczone, w przeciwnym razie klatki kluczowe po prostu są usuwane z wewnętrzną listę ramek kluczowych.

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

Usuwa przejścia z obiektów w animacji, które należą do grupy animacji.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Uwagi

Jeśli m_bAutoclearTransitions flaga jest ustawiona na wartość TRUE, ta metoda pętli wszystkich obiektów w animacji, które należą do grupy i wywołuje CAnimationObject::ClearTransitions(FALSE).

##  <a name="schedule"></a>  CAnimationGroup::Schedule

Planuje animacji o określonej godzinie.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parametry

*pTimer*<br/>
Wskaźnik do animacji czasomierza.

*czas*<br/>
Określa czas, aby zaplanować animacji.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; FALSE Jeśli metoda nie powiedzie się lub animacja nie została wywołana z bScheduleNow ustawiony na wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zaplanować animacji o określonej godzinie. Animuj musi wywołać za pomocą bScheduleNow wartość FALSE.

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

Określa, że wszystkich obiektów w animacji, które należą do grupy automatycznie zniszczyć przejścia.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
Określa, jak można zniszczyć przejścia.

### <a name="remarks"></a>Uwagi

Tę wartość można ustawić na wartość FALSE, tylko wtedy, gdy przydzielić przejścia na stosie. Wartość domyślna to TRUE, w związku z tym zdecydowanie zaleca się alokowania obiektów przejścia za pomocą nowego operatora.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
