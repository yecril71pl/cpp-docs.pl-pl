---
title: Klasa CAnimationController
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 34a02567bfeb76666cc38ccf05dcc285a1f658f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369752"
---
# <a name="canimationcontroller-class"></a>Klasa CAnimationController

Implementuje kontroler animacji, który zapewnia centralny interfejs do tworzenia animacji i zarządzania nimi.

## <a name="syntax"></a>Składnia

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController::CKontroleranimationcontroller](#canimationcontroller)|Konstruuje kontroler animacji.|
|[CKontroleranimation::~CKontroleranimacji](#_dtorcanimationcontroller)|Destruktor. Wywoływany, gdy obiekt kontrolera animacji jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Canimationcontroller::addanimationobject](#addanimationobject)|Dodaje obiekt animacji do grupy należącej do kontrolera animacji.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Dodaje klatkę kluczową do grupy.|
|[CAnimationController::AnimateGroup](#animategroup)|Przygotowuje grupę do uruchamiania animacji i opcjonalnie planuje ją.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Przeciążone. Wywoływane przez strukturę, aby oczyścić grupę, gdy animacja została zaplanowana.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Przeciążone. Tworzy klatkę kluczową, która zależy od przejścia i dodaje ją do określonej grupy.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Ustawia lub zwalnia program obsługi do wywołania, gdy zmienia się stan menedżera animacji.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Ustawia lub zwalnia program obsługi zdarzeń chronometrażu i obsługi dla aktualizacji chronometrażu.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Ustawia lub zwalnia program obsługi porównania priorytetów do wywołania, aby ustalić, czy zaplanowane scenorysu można anulować, zakończone, przycięte lub skompresowane.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Ustawia lub zwalnia program obsługi dla stanu scenorysu i zaktualizować zdarzenia.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Przeciążone. Znajduje grupę animacji według jej scenorysu.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Znajduje obiekt animacji zawierający określoną zmienną animacji.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Zwraca klatkę kluczową identyfikującą początek scenorysu.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationManager.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTimer.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Wskaźnik do interfejsu IUIAnimationTransitionFactory lub NULL, jeśli utworzenie biblioteki przejścia nie powiodło się.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTransitionLibrary.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Określa, czy co najmniej jedna grupa odtwarza animację.|
|[CAnimationController::IsValid](#isvalid)|Określa, czy kontroler animacji jest prawidłowy.|
|[CAnimationController::OnAnimationIntegerValueZmienił](#onanimationintegervaluechanged)|Wywoływana przez platformę, gdy całkowita wartość zmiennej animacji uległa zmianie.|
|[CAnimationController::OnAnimationManagerStatusZmienił](#onanimationmanagerstatuschanged)|Wywoływane przez strukturę w odpowiedzi na StatusChanged zdarzenia z menedżera animacji.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Wywoływane przez strukturę po zakończeniu aktualizacji animacji.|
|[CAnimationController::OnAnimationTimerPreUpdate CAnimationController::OnAnimationTimerPreUpdate CAnimationController::OnAnimationTimerPreUpdate CAni](#onanimationtimerpreupdate)|Wywoływane przez strukturę przed rozpoczęciem aktualizacji animacji.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Wywoływana przez strukturę, gdy liczba klatek renderowania animacji spada poniżej minimalnej pożądanej liczby klatek na sekundę.|
|[CAnimationController::OnAnimationValueZmienił](#onanimationvaluechanged)|Wywoływana przez strukturę, gdy wartość zmiennej animacji uległa zmianie.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Wywoływana przez strukturę tuż przed zaplanowaniem animacji.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Wywoływane przez strukturę do rozwiązywania konfliktów planowania.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Wywoływane przez strukturę do rozwiązywania konfliktów planowania.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Wywoływane przez strukturę do rozwiązywania konfliktów planowania.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Wywoływane przez strukturę do rozwiązywania konfliktów planowania.|
|[CAnimationController::OnStoryboardStatusZmienia](#onstoryboardstatuschanged)|Wywoływana przez strukturę, gdy stan scenorysu uległ zmianie.|
|[CAnimationController::OnStoryboardUpdated CAnimationController::OnStoryboardUpdated CAnimationController::OnStoryboardUpdated CAni](#onstoryboardupdated)|Wywoływana przez strukturę, gdy scenorys został zaktualizowany.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Usuwa wszystkie grupy animacji z kontrolera animacji.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Usuwa grupę animacji o określonym identyfikatorze z kontrolera animacji.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Usuwanie obiektu animacji z kontrolera animacji.|
|[CAnimationController::Usuńtransitions](#removetransitions)|Usuwa przejścia z obiektów animacji należących do określonej grupy.|
|[CAnimationController::Grupa harmonogramu](#schedulegroup)|Planuje animację.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Ustanawia relację między kontrolerem animacji a oknem.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Kieruje menedżera animacji do aktualizacji wartości wszystkich zmiennych animacji.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Przeciążone. Pomocnik, który czyści grupę.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Wywoływana przez strukturę, gdy animacja dla określonej grupy została właśnie zaplanowana.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart CAnimationController::gkeyframeStoryboardStart CAnimationController::gkeyframeStoryboardStart CAni](#g_keyframestoryboardstart)|Klatka kluczowa reprezentująca początek scenorysu.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Określa, czy kontroler animacji jest prawidłowy, czy nie. Ten element członkowski jest ustawiony na FALSE, jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Lista grup animacji należących do tego kontrolera animacji.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Przechowuje wskaźnik do obiektu COM Menedżera animacji.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Przechowuje wskaźnik do obiektu COM czasomierza animacji.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Wskaźnik do powiązanego obiektu CWnd, który może być automatycznie przerysowany po zmianie stanu menedżera animacji lub zdarzenia po aktualizacji. Może mieć wartość NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Przechowuje wskaźnik do obiektu COM fabryki przejścia.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Przechowuje wskaźnik do obiektu COM biblioteki przejścia.|

## <a name="remarks"></a>Uwagi

CAnimationController Klasa jest klasą klucza, który zarządza animacje. Można utworzyć jedno lub więcej wystąpień kontrolera animacji w aplikacji i, opcjonalnie, połączyć wystąpienie kontrolera animacji do obiektu CWnd przy użyciu CAnimationController::SetRelatedWnd. To połączenie jest wymagane do automatycznego wysyłania wiadomości WM_PAINT do powiązanego okna po zmianie stanu menedżera animacji lub zaktualizowaniu czasomierza animacji. Jeśli ta relacja nie zostanie włączona, należy ponownie wylosować okno, w które wyświetla animację ręcznie. W tym celu można wyprowadzić klasę z CAnimationController i zastąpić OnAnimationManagerStatusChanged i/lub OnAnimationTimerPostUpdate i unieważnić jeden lub więcej okien, gdy jest to konieczne.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CKontroleranimation::~CKontroleranimacji

Destruktor. Wywoływany, gdy obiekt kontrolera animacji jest niszczony.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>Canimationcontroller::addanimationobject

Dodaje obiekt animacji do grupy należącej do kontrolera animacji.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parametry

*Pobject*<br/>
Wskaźnik do obiektu animacji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do istniejącej lub nowej grupy animacji, gdzie pObject został dodany, jeśli funkcja powiedzie się; NULL, jeśli pObject został już dodany do grupy, która należy do innego kontrolera animacji.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby dodać obiekt animacji do kontrolera animacji. Obiekt zostanie dodany do grupy zgodnie z identyfikatorem grupy obiektu (zobacz CAnimationBaseObject::SetID). Kontroler animacji utworzy nową grupę, jeśli jest to pierwszy obiekt dodawany z określonym identyfikatorem grupy. Obiekt animacji można dodać tylko do jednego kontrolera animacji. Jeśli chcesz dodać obiekt do innego kontrolera, najpierw zadzwoń RemoveAnimationObject. Jeśli wywołasz SetID z nowym identyfikatorem grupy dla obiektu, który został już dodany do grupy, obiekt zostanie usunięty ze starej grupy i dodany do innej grupy o określonym identyfikatorze.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Dodaje klatkę kluczową do grupy.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy.

*pKeyframe (klatka klucza)*<br/>
Wskaźnik do klatki kluczowej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja powiedzie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba wywołać tę metodę, należy użyć CAnimationController::CreateKeyframe zamiast tego, który tworzy i dodaje utworzonej klatki kluczowej do grupy automatycznie.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimateGroup

Przygotowuje grupę do uruchamiania animacji i opcjonalnie planuje ją.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa groupid.

*bScheduleNow*<br/>
Określa, czy animacja ma być uruchamiana od razu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli animacja została pomyślnie zaplanowana i uruchomiona.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje rzeczywistą pracę tworzenia scenorysu, dodawanie zmiennych animacji, stosowanie przejść i ustawianie klatek kluczowych. Jest możliwe opóźnienie planowania, jeśli ustawisz bScheduleNow na FALSE. W takim przypadku określona grupa będzie przechowywać scenorys, który został skonfigurowany do animacji. W tym momencie można skonfigurować zdarzenia dla zmiennych scenorysu i animacji. Kiedy rzeczywiście trzeba uruchomić wywołanie animacji CAnimationController::ScheduleGroup.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CKontroleranimationcontroller

Konstruuje kontroler animacji.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CAnimationController::CleanUpGroup

Wywoływane przez strukturę, aby oczyścić grupę, gdy animacja została zaplanowana.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa groupid.

*pGrupa*<br/>
Wskaźnik do grupy animacji do czyszczenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie przejścia i klatki kluczowe z określonej grupy, ponieważ nie są one istotne po zaplanowaniu animacji.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe

Tworzy klatkę kluczową, która zależy od przejścia i dodaje ją do określonej grupy.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy, dla którego tworzona jest klatka kluczowa.

*pTransition (tłumaczenie na pTransition)*<br/>
Wskaźnik do przejścia. Klatka kluczowa zostanie wstawiona do scenorysu po tym przejściu.

*pKeyframe (klatka klucza)*<br/>
Wskaźnik do podstawowej klatki kluczowej dla tej klatki kluczowej.

*Przesunięcie*<br/>
Odsunięcie w sekundach od podstawowej klatki kluczowej określonej przez pKeyframe.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej klatki kluczowej, jeśli funkcja powiedzie się.

### <a name="remarks"></a>Uwagi

Zwrócony wskaźnik i bazowanie innych klatek kluczowych można zapisać na nowo utworzonej klatce kluczowej (zobacz drugie przeciążenie). Jest możliwe, aby rozpocząć przejścia w klatkach kluczowych - zobacz CBaseTransition::SetKeyframes. Nie trzeba usuwać utworzonych w ten sposób klatek kluczowych, ponieważ są one automatycznie usuwane przez grupy animacji. Należy zachować ostrożność podczas tworzenia klatek kluczowych na podstawie innych klatek kluczowych i przejść oraz unikać odwołań cyklicznych.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Ustawia lub zwalnia program obsługi do wywołania, gdy zmienia się stan menedżera animacji.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy ustawić lub zwolnić program obsługi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli program obsługi został pomyślnie ustawiony lub zwolniony.

### <a name="remarks"></a>Uwagi

Gdy program obsługi jest ustawiony (włączony) Animacja systemu Windows wywołuje OnAnimationManagerStatusZmienia się, gdy zmienia się stan menedżera animacji.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Ustawia lub zwalnia program obsługi zdarzeń chronometrażu i obsługi dla aktualizacji chronometrażu.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Określa, czy programy obsługi mają być ustawione, czy zwolnić.

*bezczynneZachody*<br/>
Określa zachowanie bezczynne dla obsługi aktualizacji czasomierza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli programy obsługi zostały pomyślnie ustawione lub zwolnione; FALSE, jeśli ta metoda jest wywoływana po raz drugi bez zwalniania obsługi po raz pierwszy lub jeśli wystąpi jakikolwiek inny błąd.

### <a name="remarks"></a>Uwagi

Gdy programy obsługi są ustawione (włączone) Interfejs API animacji systemu Windows wywołuje onanimationtimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow metody. Należy włączyć czasomierze animacji, aby zezwolić na ujęć scenomierzy interfejsu API animacji systemu Windows. W przeciwnym razie musisz wywołać CAnimationController::UpdateAnimationManager w celu kierowania menedżera animacji, aby zaktualizować wartości wszystkich zmiennych animacji.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Ustawia lub zwalnia program obsługi porównania priorytetów do wywołania, aby ustalić, czy zaplanowane scenorysu można anulować, zakończone, przycięte lub skompresowane.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parametry

*typ dwHandler*<br/>
Kombinacja UI_ANIMATION_PHT_ flag (patrz uwagi), która określa, jakie programy obsługi, aby ustawić lub zwolnić.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli program obsługi został pomyślnie ustawiony lub zwolniony.

### <a name="remarks"></a>Uwagi

Gdy program obsługi jest ustawiony (włączony) Animacja systemu Windows wywołuje następujące metody wirtualne w zależności od dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler może być kombinacją następujących flag: UI_ANIMATION_PHT_NONE - zwolnij wszystkie programy obsługi UI_ANIMATION_PHT_CANCEL - set Anuluj UI_ANIMATION_PHT_CONCLUDE obsługi porównania - set Zawarcie obsługi porównania UI_ANIMATION_PHT_COMPRESS - zestaw Compress comparison handler UI_ANIMATION_PHT_TRIM - set Trim comparison handler UI_ANIMATION_PHT_CANCEL_REMOVE - remove Cancel comparison handler UI_ANIMATION_PHT_CONCLUDE_REMOVE - remove Conclude comparison handler UI_ANIMATION_PHT_COMPRESS_REMOVE - remove Compress comparison handler UI_ANIMATION_PHT_TRIM_REMOVE - usuń program obsługi porównania przycinania

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Ustawia lub zwalnia program obsługi dla stanu scenorysu i zaktualizować zdarzenia.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy.

*bWłaszą*<br/>
Określa, czy ustawić lub zwolnić program obsługi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli program obsługi został pomyślnie ustawiony lub zwolniony; FAŁSZ, jeśli określona grupa animacji została znaleziona lub animacja dla określonej grupy nie została zainicjowana, a jej wewnętrzny scenorys ma wartość NULL.

### <a name="remarks"></a>Uwagi

Gdy program obsługi jest ustawiony (włączony) Interfejs API animacji systemu Windows wywołuje onstoryboardstatzami i metody wirtualne OnStoryboardUpdated. Program obsługi musi być ustawiony po CAnimationController::Animate został wywołany dla określonej grupy animacji, ponieważ tworzy hermetyzowany obiekt IUIAnimationStoryboard.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Znajduje grupę animacji według jej identyfikatora grupy.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa groupID.

*pStoryboard*<br/>
Wskaźnik do scenorysu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do grupy animacji lub NULL, jeśli nie można odnaleźć grupy o określonym identyfikatorze.

### <a name="remarks"></a>Uwagi

Ta metoda służy do znajdowania grupy animacji w czasie wykonywania. Grupa jest tworzona i dodawana do wewnętrznej listy grup animacji, gdy pierwszy obiekt animacji z określonym identyfikatorem grupy jest dodawany do kontrolera animacji.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Znajduje obiekt animacji zawierający określoną zmienną animacji.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parametry

*pWarienne*<br/>
Wskaźnik do zmiennej animacji.

*ppObiekt*<br/>
Wyjście. Zawiera wskaźnik do obiektu animacji lub null.

*grupa ppGroup*<br/>
Wyjście. Zawiera wskaźnik do grupy animacji, która zawiera obiekt animacji lub NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obiekt został znaleziony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywoływane z programów obsługi zdarzeń, gdy jest to wymagane do znalezienia obiektu animacji z przychodzącej zmiennej animacji.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart CAnimationController::gkeyframeStoryboardStart CAnimationController::gkeyframeStoryboardStart CAni

Klatka kluczowa reprezentująca początek scenorysu.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Zwraca klatkę kluczową identyfikującą początek scenorysu.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowej klatki kluczowej, który identyfikuje początek scenorysu.

### <a name="remarks"></a>Uwagi

Uzyskaj tę klatkę kluczową, aby oprzeć inne klatki kluczowe lub przejścia na momencie rozpoczęcia scenorysu.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationManager.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationManager lub NULL, jeśli utworzenie menedżera animacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL, a następnie wszystkie kolejne wywołania CAnimationController::IsValid zwraca WARTOŚĆ FAŁSZ. Może być konieczne uzyskianie dostępu IUIAnimationManager w celu wywołania jego metody interfejsu, które nie są zawijane przez kontroler animacji.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTimer.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationTimer lub NULL, jeśli utworzenie czasomierza animacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL, a następnie wszystkie kolejne wywołania CAnimationController::IsValid zwraca WARTOŚĆ FAŁSZ.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Wskaźnik do interfejsu IUIAnimationTransitionFactory lub NULL, jeśli utworzenie biblioteki przejścia nie powiodło się.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do IUIAnimationTransitionFactory lub NULL, jeśli utworzenie fabryki przejścia nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL, a następnie wszystkie kolejne wywołania CAnimationController::IsValid zwraca WARTOŚĆ FAŁSZ.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTransitionLibrary.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationTransitionLibrary lub NULL, jeśli utworzenie biblioteki przejścia nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL, a następnie wszystkie kolejne wywołania CAnimationController::IsValid zwraca WARTOŚĆ FAŁSZ.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Określa, czy co najmniej jedna grupa odtwarza animację.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli dla tego kontrolera animacji trwa animacja; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Sprawdza stan menedżera animacji i zwraca wartość TRUE, jeśli stan jest UI_ANIMATION_MANAGER_BUSY.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid

Określa, czy kontroler animacji jest prawidłowy.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli kontroler animacji jest prawidłowy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość FALSE tylko wtedy, gdy interfejs API animacji systemu Windows nie jest obsługiwany w bieżącym systemie operacyjnym, a tworzenie menedżera animacji nie powiodło się, ponieważ nie jest zarejestrowany. Musisz wywołać GetUIAnimationManager co najmniej raz po inicjacji bibliotek COM, aby spowodować ustawienie tej flagi.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Określa, czy kontroler animacji jest prawidłowy, czy nie. Ten element członkowski jest ustawiony na FALSE, jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Lista grup animacji należących do tego kontrolera animacji.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Przechowuje wskaźnik do obiektu COM Menedżera animacji.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Przechowuje wskaźnik do obiektu COM czasomierza animacji.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Wskaźnik do powiązanego obiektu CWnd, który może być automatycznie przerysowany po zmianie stanu menedżera animacji lub zdarzenia po aktualizacji. Może mieć wartość NULL.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Przechowuje wskaźnik do obiektu COM fabryki przejścia.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Przechowuje wskaźnik do obiektu COM biblioteki przejścia.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Wywoływana przez strukturę, gdy animacja dla określonej grupy została właśnie zaplanowana.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy animacji, która została zaplanowana.

### <a name="remarks"></a>Uwagi

Domyślna implementacja usuwa klatki kluczowe z określonej grupy i przejścia ze zmiennych animacji należących do określonej grupy. Można zastąpić w klasie pochodnej do podjęcia dodatkowych działań zgodnie z harmonogramem animacji.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueZmienił

Wywoływana przez platformę, gdy całkowita wartość zmiennej animacji uległa zmianie.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy animacji, która zawiera obiekt animacji, którego wartość została zmieniona.

*Pobject*<br/>
Wskaźnik do obiektu animacji, który zawiera zmienną animacji, której wartość została zmieniona.

*Zmiennej*<br/>
Wskaźnik do zmiennej animacji.

*Newvalue*<br/>
Określa nową wartość.

*wartość przedwvalue*<br/>
Określa poprzednią wartość.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia zmiennej animacji z EnableIntegerValueChangedEvent wywoływane dla określonej zmiennej animacji lub obiektu animacji. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusZmienił

Wywoływane przez strukturę w odpowiedzi na StatusChanged zdarzenia z menedżera animacji.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*nowyStatus*<br/>
Nowy stan menedżera animacji.

*poprzednistatus*<br/>
Poprzedni stan menedżera animacji.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia menedżera animacji za pomocą EnableAnimationManagerEvent. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Domyślna implementacja aktualizuje powiązane okno, jeśli zostało ustawione za pomocą SetRelatedWnd.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Wywoływane przez strukturę po zakończeniu aktualizacji animacji.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz programy obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate CAnimationController::OnAnimationTimerPreUpdate CAnimationController::OnAnimationTimerPreUpdate CAni

Wywoływane przez strukturę przed rozpoczęciem aktualizacji animacji.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz programy obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow

Wywoływana przez strukturę, gdy liczba klatek renderowania animacji spada poniżej minimalnej pożądanej liczby klatek na sekundę.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*Fps*<br/>
Bieżąca liczba klatek na sekundę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz programy obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Minimalna pożądana liczba klatek na sekundę jest określona przez wywołanie IUIAnimationTimer::SetFrameRateThreshold.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueZmienił

Wywoływana przez strukturę, gdy wartość zmiennej animacji uległa zmianie.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy animacji, która zawiera obiekt animacji, którego wartość została zmieniona.

*Pobject*<br/>
Wskaźnik do obiektu animacji, który zawiera zmienną animacji, której wartość została zmieniona.

*Zmiennej*<br/>
Wskaźnik do zmiennej animacji.

*Newvalue*<br/>
Określa nową wartość.

*wartość przedwvalue*<br/>
Określa poprzednią wartość.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia zmiennej animacji z EnableValueChangedEvent wywoływane dla określonej zmiennej animacji lub obiektu animacji. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Wywoływana przez strukturę tuż przed zaplanowaniem animacji.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy animacji, której animacja ma się rozpocząć.

### <a name="remarks"></a>Uwagi

To wywołanie jest kierowane do powiązanych CWnd i może być zastąpione w klasie pochodnej do wykonywania dodatkowych akcji przed rozpoczęciem animacji dla określonej grupy.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

Wywoływane przez strukturę do rozwiązywania konfliktów planowania.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled (GrupaCheduled)*<br/>
Grupa, która jest właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNowy*<br/>
Grupa, która jest właścicielem nowego scenorysu, który jest w harmonogramie konfliktu z zaplanowanego scenorysu własnością pGroupScheduled.

*priorityEfect (efekt priorytetu)*<br/>
Potencjalny wpływ na pGroupNew jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić true, jeśli scenorysu własnością pGroupNew ma priorytet. Należy zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia porównania priorytetów przy użyciu CAnimationController::EnablePriorityComparisonHandler i określisz UI_ANIMATION_PHT_CANCEL. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Wywoływane przez strukturę do rozwiązywania konfliktów planowania.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled (GrupaCheduled)*<br/>
Grupa, która jest właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNowy*<br/>
Grupa, która jest właścicielem nowego scenorysu, który jest w harmonogramie konfliktu z zaplanowanego scenorysu własnością pGroupScheduled.

*priorityEfect (efekt priorytetu)*<br/>
Potencjalny wpływ na pGroupNew jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić true, jeśli scenorysu własnością pGroupNew ma priorytet. Należy zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia porównania priorytetów przy użyciu CAnimationController::EnablePriorityComparisonHandler i określisz UI_ANIMATION_PHT_COMPRESS. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude

Wywoływane przez strukturę do rozwiązywania konfliktów planowania.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled (GrupaCheduled)*<br/>
Grupa, która jest właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNowy*<br/>
Grupa, która jest właścicielem nowego scenorysu, który jest w harmonogramie konfliktu z zaplanowanego scenorysu własnością pGroupScheduled.

*priorityEfect (efekt priorytetu)*<br/>
Potencjalny wpływ na pGroupNew jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić true, jeśli scenorysu własnością pGroupNew ma priorytet. Należy zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia porównania priorytetów przy użyciu CAnimationController::EnablePriorityComparisonHandler i określisz UI_ANIMATION_PHT_CONCLUDE. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

Wywoływane przez strukturę do rozwiązywania konfliktów planowania.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled (GrupaCheduled)*<br/>
Grupa, która jest właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNowy*<br/>
Grupa, która jest właścicielem nowego scenorysu, który jest w harmonogramie konfliktu z zaplanowanego scenorysu własnością pGroupScheduled.

*priorityEfect (efekt priorytetu)*<br/>
Potencjalny wpływ na pGroupNew jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić true, jeśli scenorysu własnością pGroupNew ma priorytet. Należy zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia porównania priorytetów przy użyciu CAnimationController::EnablePriorityComparisonHandler i określisz UI_ANIMATION_PHT_TRIM. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusZmienia

Wywoływana przez strukturę, gdy stan scenorysu uległ zmianie.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy animacji, która jest właścicielem scenorysu, którego stan uległ zmianie.

*nowyStatus*<br/>
Określa nowy stan.

*poprzednistatus*<br/>
Określa poprzedni stan.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia scenorysu przy użyciu CAnimationController::EnableStoryboardEventHandler. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated CAnimationController::OnStoryboardUpdated CAnimationController::OnStoryboardUpdated CAni

Wywoływana przez strukturę, gdy scenorys został zaktualizowany.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGrupa*<br/>
Wskaźnik do grupy, która jest właścicielem scenorysu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia scenorysu przy użyciu CAnimationController::EnableStoryboardEventHandler. Można go zastąpić w klasie pochodnej do podjęcia akcji specyficznych dla aplikacji.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Usuwa wszystkie grupy animacji z kontrolera animacji.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Uwagi

Wszystkie grupy zostaną usunięte, ich wskaźnik, jeśli są przechowywane na poziomie aplikacji, musi zostać unieważniony. Jeśli CAnimationGroup::m_bAutodestroyAnimationObjects dla usuniętej grupy jest PRAWDA, wszystkie obiekty animacji należące do tej grupy zostaną usunięte; w przeciwnym razie ich odwołania do nadrzędnego kontrolera animacji zostaną ustawione na NULL i mogą zostać dodane do innego kontrolera.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Usuwa grupę animacji o określonym identyfikatorze z kontrolera animacji.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy animacji.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę animacji z wewnętrznej listy grup i usuwa ją, dlatego jeśli wskaźnik do tej grupy animacji został zapisany, musi zostać unieważniony. Jeśli CAnimationGroup::m_bAutodestroyAnimationObjects jest TRUE, wszystkie obiekty animacji, które należą do tej grupy zostaną usunięte; w przeciwnym razie ich odwołania do nadrzędnego kontrolera animacji zostaną ustawione na NULL i mogą zostać dodane do innego kontrolera.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Usuwanie obiektu animacji z kontrolera animacji.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parametry

*Pobject*<br/>
Wskaźnik do obiektu animacji.

*bNoDelete*<br/>
Jeśli ten parametr ma wartość PRAWDA, obiekt nie zostanie usunięty po usunięciu.

### <a name="remarks"></a>Uwagi

Usuwa obiekt animacji z kontrolera animacji i grupy animacji. Wywołanie tej funkcji, jeśli określony obiekt nie powinien być już animowany lub jeśli trzeba przenieść obiekt do innego kontrolera animacji. W ostatnim przypadku bNoDelete musi być true.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::Usuńtransitions

Usuwa przejścia z obiektów animacji należących do określonej grupy.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy.

### <a name="remarks"></a>Uwagi

Grupa pętli nad jego obiektów animacji i wywołuje ClearTransitions(FALSE) dla każdego obiektu animacji. Ta metoda jest wywoływana przez platformę po zaplanowaniu animacji.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::Grupa harmonogramu

Planuje animację.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy animacji do zaplanowania.

*Czas*<br/>
Określa czas planowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli animacja została zaplanowana pomyślnie. FAŁSZ, jeśli scenorys nie został utworzony lub wystąpi inny błąd.

### <a name="remarks"></a>Uwagi

Należy wywołać Program AnimateGroup z parametrem bScheduleNow ustawiono wartość FAŁSZ przed grupą harmonogramu. Można określić żądany czas animacji uzyskany z IUIAnimationTimer::GetTime. Jeśli parametr czasu wynosi 0,0, animacja jest zaplanowana dla bieżącego czasu.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Ustanawia relację między kontrolerem animacji a oknem.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do obiektu okna do ustawionego.

### <a name="remarks"></a>Uwagi

Jeśli powiązany obiekt CWnd jest ustawiony, kontroler animacji może go automatycznie zaktualizować (wysłać WM_PAINT komunikat) po zmianie stanu menedżera animacji lub zdarzenia aktualizacji porazy.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Kieruje menedżera animacji do aktualizacji wartości wszystkich zmiennych animacji.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody powoduje przejście menedżera animacji do bieżącego czasu, zmieniając stan scenokrągłów w razie potrzeby i aktualizując wszystkie zmienne animacji do odpowiednich interpolowanych wartości. Wewnętrznie ta metoda wywołuje IUIAnimationTimer::GetTime(timeNow) i IUIAnimationManager::Update(timeNow). Zastąpi tę metodę w klasie pochodnej, aby dostosować to zachowanie.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
