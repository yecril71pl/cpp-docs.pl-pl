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
ms.openlocfilehash: 28d305e2107f7b9a8fd2164eb0ec9678d62ef8fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369743"
---
# <a name="canimationgroup-class"></a>Klasa CAnimationGroup

Implementuje grupę animacji, która łączy scenorys animacji, obiekty animacji i przejścia w celu zdefiniowania animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationGroup;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Konstruuje grupę animacji.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|Destruktor. Wywoływana, gdy grupa animacji jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Animuje grupę.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Stosuje przejścia do obiektów animacji.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Znajduje obiekt animacji zawierający określoną zmienną animacji.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Zwraca groupid.|
|[CAnimationGroup::RemoveKeyframes CAnimationGroup::RemoveKeyframes CAnimationGroup::RemoveKeyframes CAni](#removekeyframes)|Usuwa i opcjonalnie niszczy wszystkie klatki kluczowe, które należą do grupy animacji.|
|[CAnimationGroup::Usuńtransitions](#removetransitions)|Usuwa przejścia z obiektów animacji należących do grupy animacji.|
|[CAnimationGroup::Harmonogram](#schedule)|Planuje animację o określonej godzinie.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Kieruje wszystkie obiekty animacji należące do grupy automatycznie niszczą przejścia.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocnik, który dodaje klatki kluczowe do scenorysu.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocnik, który dodaje przejścia do scenorysu.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocnik, który tworzy obiekty przejścia COM.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Określa sposób usuwania przejść z obiektów animacji należących do grupy. Jeśli ten element członkowski ma wartość PRAWDA, przejścia są usuwane automatycznie po zaplanowaniu animacji. W przeciwnym razie należy ręcznie usunąć przejścia.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Określa sposób niszczenia obiektów animacji. Jeśli ten parametr ma wartość PRAWDA, obiekty animacji zostaną automatycznie zniszczone po zniszczeniu grupy. W przeciwnym razie obiekty animacji muszą zostać zniszczone ręcznie. Wartością domyślną jest FAŁSZ. Ustaw tę wartość na WARTOŚĆ PRAWDA tylko wtedy, gdy wszystkie obiekty animacji należące do grupy są przydzielane dynamicznie z operatorem nowym.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Określa sposób niszczenia klatek kluczowych. Jeśli ta wartość jest PRAWDA, wszystkie klatki kluczowe są usuwane i niszczone; w przeciwnym razie są one usuwane tylko z listy. Wartością domyślną jest PRAWDA.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Zawiera listę obiektów animacji.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Zawiera listę klatek kluczowych.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Wskazuje scenorys animacji. Ten wskaźnik jest prawidłowy tylko po wywołaniu programu Animate.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Unikatowy identyfikator grupy animacji.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Wskaźnik do kontrolera animacji, do którego należy ta grupa.|

## <a name="remarks"></a>Uwagi

Grupy animacji są tworzone automatycznie przez kontroler animacji (CAnimationController) podczas dodawania obiektów animacji za pomocą CAnimationController::AddAnimationObject. Grupa animacji jest identyfikowana przez GroupID, który jest zwykle traktowany jako parametr do manipulowania grupami animacji. Identyfikator grupy jest pobierany z pierwszego obiektu animacji dodawany do nowej grupy animacji. Scenorysu animacji zhermetyzowanej jest tworzony po wywołaniu CAnimationController::AnimateGroup i można uzyskać dostęp za pośrednictwem publicznego m_pStoryboard członkowskiego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAnimationGroup`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>CAnimationGroup::~CAnimationGroup

Destruktor. Wywoływana, gdy grupa animacji jest niszczony.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>CAnimationGroup::AddKeyframes

Pomocnik, który dodaje klatki kluczowe do scenorysu.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do obiektu COM ujęć.

*bDdDeep*<br/>
Określa, czy ta metoda powinna być dodana do scenorysu klatek kluczowych, które zależą od innych klatek kluczowych.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>CAnimationGroup::AddTransitions

Pomocnik, który dodaje przejścia do scenorysu.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do obiektu COM ujęć.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a>CAnimationGroup::Animate

Animuje grupę.

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

PRAWDA, jeśli metoda powiedzie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wewnętrzny scenorys, tworzy i stosuje przejścia i planuje animację, jeśli bScheduleNow ma wartość TRUE. Jeśli bScheduleNow jest FALSE, należy wywołać Harmonogram, aby rozpocząć animację w określonym czasie.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>CAnimationGroup::ApplyTransitions

Stosuje przejścia do obiektów animacji.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Uwagi

Ta metoda potwierdza w trybie debugowania, jeśli scenorys nie został utworzony. Najpierw tworzy wszystkie przejścia, a następnie dodaje "statyczne" klatki kluczowe (klatki kluczowe zależne od przesunięć), dodaje przejścia, które nie zależą od klatek kluczowych, dodaje klatki kluczowe w zależności od przejść i innych klatek kluczowych, a na koniec dodaje przejścia zależne od klatek kluczowych.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup

Konstruuje grupę animacji.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*pKontrolerparentuser*<br/>
Wskaźnik do kontrolera animacji, który tworzy grupę.

*nGrupaID*<br/>
Określa groupid.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>CAnimationGroup::CreateTransitions

Pomocnik, który tworzy obiekty przejścia COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA jest metoda powiedzie się, w przeciwnym razie FALSE.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject

Znajduje obiekt animacji zawierający określoną zmienną animacji.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pWarienne*<br/>
Wskaźnik do zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu animacji lub NULL, jeśli obiekt animacji nie zostanie znaleziony.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>CAnimationGroup::GetGroupID

Zwraca groupid.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator grupy.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions

Określa sposób usuwania przejść z obiektów animacji należących do grupy. Jeśli ten element członkowski ma wartość PRAWDA, przejścia są usuwane automatycznie po zaplanowaniu animacji. W przeciwnym razie należy ręcznie usunąć przejścia.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects

Określa sposób niszczenia obiektów animacji. Jeśli ten parametr ma wartość PRAWDA, obiekty animacji zostaną automatycznie zniszczone po zniszczeniu grupy. W przeciwnym razie obiekty animacji muszą zostać zniszczone ręcznie. Wartością domyślną jest FAŁSZ. Ustaw tę wartość na WARTOŚĆ PRAWDA tylko wtedy, gdy wszystkie obiekty animacji należące do grupy są przydzielane dynamicznie z operatorem nowym.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes

Określa sposób niszczenia klatek kluczowych. Jeśli ta wartość jest PRAWDA, wszystkie klatki kluczowe są usuwane i niszczone; w przeciwnym razie są one usuwane tylko z listy. Wartością domyślną jest PRAWDA.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects

Zawiera listę obiektów animacji.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames

Zawiera listę klatek kluczowych.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID

Unikatowy identyfikator grupy animacji.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController

Wskaźnik do kontrolera animacji, do którego należy ta grupa.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard

Wskazuje scenorys animacji. Ten wskaźnik jest prawidłowy tylko po wywołaniu programu Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes CAnimationGroup::RemoveKeyframes CAnimationGroup::RemoveKeyframes CAni

Usuwa i opcjonalnie niszczy wszystkie klatki kluczowe, które należą do grupy animacji.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Uwagi

Jeśli m_bAutodestroyKeyframes element członkowski ma wartość PRAWDA, klatki kluczowe są usuwane i niszczone, w przeciwnym razie klatki kluczowe są po prostu usuwane z wewnętrznej listy klatek kluczowych.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>CAnimationGroup::Usuńtransitions

Usuwa przejścia z obiektów animacji należących do grupy animacji.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Uwagi

Jeśli flaga m_bAutoclearTransitions jest ustawiona na WARTOŚĆ TRUE, ta metoda zapętla wszystkie obiekty animacji, które należą do grupy i wywołuje CAnimationObject::ClearTransitions(FALSE).

## <a name="canimationgroupschedule"></a><a name="schedule"></a>CAnimationGroup::Harmonogram

Planuje animację o określonej godzinie.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parametry

*pTimer*<br/>
Wskaźnik do czasomierza animacji.

*Czas*<br/>
Określa czas planowania animacji.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda powiedzie się; FAŁSZ, jeśli metoda nie powiedzie się lub jeśli program Animate nie został wywołany z bScheduleNow ustawiona na FAŁSZ.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zaplanować animację w określonym czasie. Należy wywołać program Animate z bScheduleNow najpierw ustawiona na FAŁSZ.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions

Kieruje wszystkie obiekty animacji należące do grupy automatycznie niszczą przejścia.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroj*<br/>
Określa sposób niszczenia przejść.

### <a name="remarks"></a>Uwagi

Ustaw tę wartość na FALSE tylko wtedy, gdy przydzielić przejścia na stosie. Wartością domyślną jest TRUE, dlatego zdecydowanie zaleca się przydzielanie obiektów przejścia przy użyciu nowego operatora.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
