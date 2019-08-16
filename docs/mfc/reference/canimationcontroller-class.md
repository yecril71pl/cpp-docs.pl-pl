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
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507651"
---
# <a name="canimationcontroller-class"></a>Klasa CAnimationController

Implementuje kontroler animacji, który udostępnia centralny interfejs do tworzenia animacji i zarządzania nimi.

## <a name="syntax"></a>Składnia

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Konstruuje kontroler animacji.|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|Destruktor. Wywoływana, gdy trwa niszczenie obiektu kontrolera animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController:: AddAnimationObject](#addanimationobject)|Dodaje obiekt animacji do grupy należącej do kontrolera animacji.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Dodaje klatkę kluczową do grupy.|
|[CAnimationController:: animować](#animategroup)|Przygotowuje grupę do uruchomienia animacji i opcjonalnie planuje ją.|
|[CAnimationController:: czyszczący](#cleanupgroup)|Przeciążone. Wywoływane przez platformę, aby oczyścić grupę po zaplanowaniu animacji.|
|[CAnimationController:: isklatka kluczowa](#createkeyframe)|Przeciążone. Tworzy klatkę kluczową, która zależy od przejścia i dodaje ją do określonej grupy.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Ustawia lub zwalnia procedurę obsługi do wywoływania, gdy zmienia się stan Menedżera animacji.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Ustawia lub zwalnia procedurę obsługi dla zdarzeń chronometrażu i procedury obsługi dla aktualizacji czasowych.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Ustawia lub zwalnia procedurę obsługi porównania priorytetów do wywołania, aby określić, czy zaplanowana scenorys może zostać anulowana, zawarta, przycięta lub skompresowana.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Ustawia lub zwalnia procedurę obsługi dla zdarzeń dotyczących stanu i aktualizacji scenorysu.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Przeciążone. Znajduje grupę animacji według scenorysu.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Znajduje obiekt animacji zawierający określoną zmienną animacji.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Zwraca klatkę kluczową, która identyfikuje początek scenorysu.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationManager.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTimer.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Wskaźnik do interfejsu IUIAnimationTransitionFactory lub NULL, jeśli Tworzenie biblioteki przejścia nie powiodło się.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTransitionLibrary.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Informuje, czy co najmniej jedna grupa Odtwarza animację.|
|[CAnimationController:: IsValid](#isvalid)|Informuje, czy kontroler animacji jest prawidłowy.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Wywoływane przez platformę, gdy została zmieniona wartość całkowita zmiennej animacji.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Wywoływane przez platformę w odpowiedzi na Zdarzenie StatusChanged z Menedżera animacji.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Wywoływane przez platformę po zakończeniu aktualizacji animacji.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Wywoływane przez platformę przed rozpoczęciem aktualizacji animacji.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Wywoływane przez platformę, gdy współczynnik klatek renderowania dla animacji spadnie poniżej minimalnej pożądanej szybkości klatek.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Wywoływane przez platformę, gdy wartość zmiennej animacji została zmieniona.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Wywoływane przez platformę bezpośrednio przed zaplanowaniem animacji.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Wywoływane przez platformę, aby rozwiązać konflikty planowania.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Wywoływane przez platformę, aby rozwiązać konflikty planowania.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Wywoływane przez platformę, aby rozwiązać konflikty planowania.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Wywoływane przez platformę, aby rozwiązać konflikty planowania.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Wywoływane przez platformę, gdy stan scenorysu został zmieniony.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Wywoływane przez platformę, gdy scenorys został zaktualizowany.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Usuwa wszystkie grupy animacji z kontrolera animacji.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Usuwa grupę animacji z określonym IDENTYFIKATORem z kontrolera animacji.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Usuń obiekt animacji z kontrolera animacji.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Usuwa przejścia z obiektów animacji należących do określonej grupy.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Planuje animację.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Ustanawia relację między kontrolerem animacji a oknem.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Kieruje Menedżera animacji do aktualizowania wartości wszystkich zmiennych animacji.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController:: czyszczący](#cleanupgroup)|Przeciążone. Pomocnik, który czyści grupę.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Wywoływane przez platformę, gdy została właśnie zaplanowana animacja dla określonej grupy.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Klatka kluczowa, która reprezentuje początek scenorysu.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Określa, czy kontroler animacji jest prawidłowy, czy nie. Ten element członkowski ma wartość FAŁSZ, jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Lista grup animacji należących do tego kontrolera animacji.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Przechowuje wskaźnik do obiektu COM Menedżera animacji.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Przechowuje wskaźnik do obiektu COM czasomierza animacji.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Wskaźnik do powiązanego obiektu CWnd, który może być automatycznie ponownie rysowany w przypadku zmiany stanu Menedżera animacji lub wystąpienia zdarzenia aktualizacji. Może mieć wartość NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Zapisuje wskaźnik w celu przejścia do fabryki obiektów COM.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Przechowuje wskaźnik do obiektu COM biblioteki przejścia.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationController jest kluczem klasy, która zarządza animacjami. W aplikacji można utworzyć co najmniej jedno wystąpienie kontrolera animacji, a opcjonalnie połączyć wystąpienie kontrolera animacji z obiektem CWnd za pomocą CAnimationController:: SetRelatedWnd. To połączenie jest wymagane do automatycznego wysyłania komunikatów WM_PAINT do powiązanego okna, gdy stan Menedżera animacji został zmieniony lub został zaktualizowany czasomierz animacji. Jeśli ta relacja nie zostanie włączona, należy ponownie narysować okno, które ręcznie wyświetla animację. W tym celu można utworzyć klasę z CAnimationController i zastąpić OnAnimationManagerStatusChanged i/lub OnAnimationTimerPostUpdate i unieważniać co najmniej jedno z okien, jeśli jest to konieczne.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller. h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

Destruktor. Wywoływana, gdy trwa niszczenie obiektu kontrolera animacji.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>CAnimationController:: AddAnimationObject

Dodaje obiekt animacji do grupy należącej do kontrolera animacji.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Wskaźnik do obiektu animacji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do istniejącej lub nowej grupy animacji, gdzie pObject został dodany, jeśli funkcja się powiedzie; Wartość NULL, jeśli pObject został już dodany do grupy należącej do innego kontrolera animacji.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dodać obiekt animacji do kontrolera animacji. Obiekt zostanie dodany do grupy zgodnie z identyfikatorem GroupID obiektu (zobacz CAnimationBaseObject:: SetID). Kontroler animacji utworzy nową grupę, jeśli jest to pierwszy obiekt dodawany z określonym identyfikatorem grupy. Obiekt animacji można dodać tylko do jednego kontrolera animacji. Jeśli musisz dodać obiekt do innego kontrolera, najpierw Wywołaj RemoveAnimationObject. Jeśli wywołasz SetID z nowym identyfikatorem grupy dla obiektu, który został już dodany do grupy, obiekt zostanie usunięty ze starej grupy i dodany do innej grupy o określonym IDENTYFIKATORze.

##  <a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Dodaje klatkę kluczową do grupy.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*pKeyframe*<br/>
Wskaźnik do klatki kluczowej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli funkcja się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zazwyczaj nie trzeba wywoływać tej metody, zamiast tego należy użyć CAnimationController:: \ klatka kluczowa, która umożliwia automatyczne utworzenie i dodanie utworzonej klatki kluczowej do grupy.

##  <a name="animategroup"></a>CAnimationController:: animować

Przygotowuje grupę do uruchomienia animacji i opcjonalnie planuje ją.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*bScheduleNow*<br/>
Określa, czy od razu uruchamiać animację.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli animacja została pomyślnie zaplanowana i uruchomiona.

### <a name="remarks"></a>Uwagi

Ta metoda wykonuje rzeczywistą prace tworzącą scenorys, dodając zmienne animacji, stosując przejścia i ustawiając klatki kluczowe. Można opóźnić planowanie, jeśli ustawisz bScheduleNow na wartość FALSE. W takim przypadku określona grupa będzie przechowywać scenorys, który został skonfigurowany do animacji. W tym momencie można skonfigurować zdarzenia dla scenorysu i zmiennych animacji. Gdy konieczne jest uruchomienie wywołania animacji CAnimationController:: Schedule.

##  <a name="canimationcontroller"></a>CAnimationController::CAnimationController

Konstruuje kontroler animacji.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>CAnimationController:: czyszczący

Wywoływane przez platformę, aby oczyścić grupę po zaplanowaniu animacji.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*pGroup*<br/>
Wskaźnik do grupy animacji do oczyszczenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie przejścia i ramki kluczowe z określonej grupy, ponieważ nie są one istotne po zaplanowaniu animacji.

##  <a name="createkeyframe"></a>CAnimationController:: isklatka kluczowa

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

*nGroupID*<br/>
Określa identyfikator grupy, dla której jest tworzona klatka kluczowa.

*pTransition*<br/>
Wskaźnik do przejścia. Klatka kluczowa zostanie wstawiona do scenorysu po wykonaniu tego przejścia.

*pKeyframe*<br/>
Wskaźnik do podstawowej klatki kluczowej dla tej klatki kluczowej.

*offset*<br/>
Przesunięcie w sekundach od podstawowej klatki kluczowej określonej przez pKeyframe.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonej klatki kluczowej, jeśli funkcja się powiedzie.

### <a name="remarks"></a>Uwagi

Można przechowywać zwrócony wskaźnik i oprzeć inne ramki kluczowe w nowo utworzonej klatce kluczowej (zobacz drugie Przeciążenie). Można rozpocząć przejścia w klatkach kluczowych — Zobacz CBaseTransition:: setklatka kluczowe. Nie trzeba usuwać klatek kluczowych utworzonych w ten sposób, ponieważ są one usuwane automatycznie przez grupy animacji. Należy zachować ostrożność podczas tworzenia klatek kluczowych w oparciu o inne ramki kluczowe i przejścia oraz uniknąć odwołań cyklicznych.

##  <a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Ustawia lub zwalnia procedurę obsługi do wywoływania, gdy zmienia się stan Menedżera animacji.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy należy ustawić lub zwolnić procedurę obsługi.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydano.

### <a name="remarks"></a>Uwagi

Gdy program obsługi jest ustawiony (włączony) wywołania animacji systemu Windows OnAnimationManagerStatusChanged, gdy zmienia się stan Menedżera animacji.

##  <a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Ustawia lub zwalnia procedurę obsługi dla zdarzeń chronometrażu i procedury obsługi dla aktualizacji czasowych.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Określa, czy mają być ustawiane lub zwalniane programy obsługi.

*idleBehavior*<br/>
Określa zachowanie bezczynne dla programu obsługi aktualizacji czasomierza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli programy obsługi zostały pomyślnie ustawione lub wydane; FAŁSZ, jeśli ta metoda jest wywoływana dla drugiego czasu bez zwalniania programów obsługi, lub jeśli wystąpi jakikolwiek inny błąd.

### <a name="remarks"></a>Uwagi

Po ustawieniu programów obsługi (włączone) interfejs API animacji systemu Windows wywołuje metody OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow. Należy włączyć czasomierze animacji, aby umożliwić aktualizowanie scenorysów przez interfejs API animacji systemu Windows. W przeciwnym razie należy wywołać CAnimationController:: UpdateAnimationManager, aby skierować Menedżera animacji do aktualizowania wartości wszystkich zmiennych animacji.

##  <a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Ustawia lub zwalnia procedurę obsługi porównania priorytetów do wywołania, aby określić, czy zaplanowana scenorys może zostać anulowana, zawarta, przycięta lub skompresowana.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parametry

*dwHandlerType*<br/>
Kombinacja flag UI_ANIMATION_PHT_ (Zobacz uwagi), która określa, jakie procedury obsługi należy ustawić lub zwolnić.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydano.

### <a name="remarks"></a>Uwagi

Po ustawieniu programu obsługi (Enabled) animacja systemu Windows wywołuje następujące metody wirtualne w zależności od dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler może być kombinacją następujących flag: UI_ANIMATION_PHT_NONE — Zwolnij wszystkie programy obsługi UI_ANIMATION_PHT_CANCEL — ustaw pozycję anulowania obsługi porównania UI_ANIMATION_PHT_CONCLUDE-Set Kończenie procedury obsługi porównania Procedura obsługi porównania przycinania UI_ANIMATION_PHT_CANCEL_REMOVE — usuwanie procedury obsługi porównania anulowania UI_ANIMATION_PHT_CONCLUDE_REMOVE — usuwanie końcowego procedury obsługi porównania UI_ANIMATION_PHT_COMPRESS_REMOVE — usuwanie procedury obsługi porównania kompresji UI_ANIMATION_PHT _TRIM_REMOVE — usuwanie procedury obsługi porównania odcinania

##  <a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Ustawia lub zwalnia procedurę obsługi dla zdarzeń dotyczących stanu i aktualizacji scenorysu.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*bEnable*<br/>
Określa, czy należy ustawić lub zwolnić procedurę obsługi.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydano. Wartość FALSE, jeśli określona grupa animacji zostanie znaleziona lub nie zainicjowano animacji dla określonej grupy, a jej wewnętrzna seria ujęć ma wartość NULL.

### <a name="remarks"></a>Uwagi

Po ustawieniu procedury obsługi (Enabled) interfejs API animacji systemu Windows wywołuje metody wirtualne OnStoryboardStatusChanges i OnStoryboardUpdated. Program obsługi musi być ustawiony po wywołaniu CAnimationController:: Animuj dla określonej grupy animacji, ponieważ tworzy on hermetyzowany obiekt IUIAnimationStoryboard.

##  <a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Znajduje grupę animacji według identyfikatora grupy.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*pStoryboard*<br/>
Wskaźnik do scenorysu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do grupy animacji lub wartości NULL, jeśli nie można odnaleźć grupy o określonym IDENTYFIKATORze.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby znaleźć grupę animacji w czasie wykonywania. Grupa jest tworzona i dodawana do wewnętrznej listy grup animacji, gdy pierwszy obiekt animacji z określonym identyfikatorem GroupID jest dodawany do kontrolera animacji.

##  <a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Znajduje obiekt animacji zawierający określoną zmienną animacji.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Wskaźnik do zmiennej animacji.

*ppObject*<br/>
Rozdzielczości. Zawiera wskaźnik do obiektu animacji lub ma wartość NULL.

*ppGroup*<br/>
Rozdzielczości. Zawiera wskaźnik do grupy animacji, która zawiera obiekt animacji, lub wartość NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obiekt został znaleziony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywoływane z obsługi zdarzeń, gdy jest wymagane do znalezienia obiektu animacji ze zmiennej animacji przychodzącej.

##  <a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Klatka kluczowa, która reprezentuje początek scenorysu.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Zwraca klatkę kluczową, która identyfikuje początek scenorysu.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowej klatki kluczowej, który identyfikuje początek scenorysu.

### <a name="remarks"></a>Uwagi

Uzyskaj tę klatkę kluczową, aby oprzeć wszystkie inne ramki kluczowe lub przejścia w momencie rozpoczęcia tworzenia scenorysu.

##  <a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationManager.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationManager lub NULL, jeśli Tworzenie Menedżera animacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL i po tym, że wszystkie kolejne wywołania w CAnimationController:: IsValid zwracają wartość FALSE. Może być konieczne uzyskanie dostępu do IUIAnimationManager w celu wywołania metod interfejsu, które nie są opakowane przez kontroler animacji.

##  <a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTimer.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationTimer lub NULL, jeśli Tworzenie czasomierza animacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL i po tym, że wszystkie kolejne wywołania w CAnimationController:: IsValid zwracają wartość FALSE.

##  <a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Wskaźnik do interfejsu IUIAnimationTransitionFactory lub NULL, jeśli Tworzenie biblioteki przejścia nie powiodło się.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do IUIAnimationTransitionFactory lub NULL, jeśli Tworzenie fabryki przejścia nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL i po tym, że wszystkie kolejne wywołania w CAnimationController:: IsValid zwracają wartość FALSE.

##  <a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Zapewnia dostęp do zhermetyzowanego obiektu IUIAnimationTransitionLibrary.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu IUIAnimationTransitionLibrary lub NULL, jeśli Tworzenie biblioteki przejścia nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows, ta metoda zwraca wartość NULL i po tym, że wszystkie kolejne wywołania w CAnimationController:: IsValid zwracają wartość FALSE.

##  <a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Informuje, czy co najmniej jedna grupa Odtwarza animację.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli istnieje animacja w toku dla tego kontrolera animacji; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Sprawdza stan Menedżera animacji i zwraca wartość TRUE, jeśli stan to UI_ANIMATION_MANAGER_BUSY.

##  <a name="isvalid"></a>CAnimationController:: IsValid

Informuje, czy kontroler animacji jest prawidłowy.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, Jeśli kontroler animacji jest prawidłowy; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość FALSE tylko wtedy, gdy interfejs API animacji systemu Windows nie jest obsługiwany w bieżącym systemie operacyjnym i tworzenie Menedżera animacji nie powiodło się, ponieważ nie jest zarejestrowany. Musisz wywołać GetUIAnimationManager co najmniej raz po inicjalizacji bibliotek COM, aby spowodować ustawienie tej flagi.

##  <a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Określa, czy kontroler animacji jest prawidłowy, czy nie. Ten element członkowski ma wartość FAŁSZ, jeśli bieżący system operacyjny nie obsługuje interfejsu API animacji systemu Windows.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Lista grup animacji należących do tego kontrolera animacji.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Przechowuje wskaźnik do obiektu COM Menedżera animacji.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

Przechowuje wskaźnik do obiektu COM czasomierza animacji.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

Wskaźnik do powiązanego obiektu CWnd, który może być automatycznie ponownie rysowany w przypadku zmiany stanu Menedżera animacji lub wystąpienia zdarzenia aktualizacji. Może mieć wartość NULL.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Zapisuje wskaźnik w celu przejścia do fabryki obiektów COM.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Przechowuje wskaźnik do obiektu COM biblioteki przejścia.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Wywoływane przez platformę, gdy została właśnie zaplanowana animacja dla określonej grupy.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy animacji, która została zaplanowana.

### <a name="remarks"></a>Uwagi

Implementacja domyślna usuwa ramki kluczowe z określonej grupy i przechodzi ze zmiennych animacji należących do określonej grupy. Może zostać zastąpiony w klasie pochodnej, aby wykonać dodatkowe akcje po harmonogramie animacji.

##  <a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Wywoływane przez platformę, gdy została zmieniona wartość całkowita zmiennej animacji.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy animacji, która zawiera obiekt animacji, którego wartość została zmieniona.

*pObject*<br/>
Wskaźnik do obiektu animacji, który zawiera zmienną animacji, której wartość została zmieniona.

*zmiennej*<br/>
Wskaźnik do zmiennej animacji.

*newValue*<br/>
Określa nową wartość.

*prevValue*<br/>
Określa poprzednią wartość.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń zmiennych animacji z EnableIntegerValueChangedEvent wywołana dla określonej zmiennej animacji lub obiektu animacji. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged

Wywoływane przez platformę w odpowiedzi na Zdarzenie StatusChanged z Menedżera animacji.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nowy stan Menedżera animacji.

*previousStatus*<br/>
Poprzedni stan Menedżera animacji.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, jeśli włączysz zdarzenia Menedżera animacji z EnableAnimationManagerEvent. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Domyślna implementacja aktualizuje okno powiązane, jeśli zostało ustawione z SetRelatedWnd.

##  <a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Wywoływane przez platformę po zakończeniu aktualizacji animacji.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate

Wywoływane przez platformę przed rozpoczęciem aktualizacji animacji.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow

Wywoływane przez platformę, gdy współczynnik klatek renderowania dla animacji spadnie poniżej minimalnej pożądanej szybkości klatek.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*składnika*<br/>
Bieżąca szybkość klatek w klatkach na sekundę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Minimalna pożądany współczynnik klatek jest określony przez wywołanie IUIAnimationTimer:: SetFrameRateThreshold.

##  <a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Wywoływane przez platformę, gdy wartość zmiennej animacji została zmieniona.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy animacji, która zawiera obiekt animacji, którego wartość została zmieniona.

*pObject*<br/>
Wskaźnik do obiektu animacji, który zawiera zmienną animacji, której wartość została zmieniona.

*zmiennej*<br/>
Wskaźnik do zmiennej animacji.

*newValue*<br/>
Określa nową wartość.

*prevValue*<br/>
Określa poprzednią wartość.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń zmiennych animacji z EnableValueChangedEvent wywołana dla określonej zmiennej animacji lub obiektu animacji. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Wywoływane przez platformę bezpośrednio przed zaplanowaniem animacji.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy animacji, którego animacja ma zostać rozpoczęta.

### <a name="remarks"></a>Uwagi

To wywołanie jest kierowane do powiązanej CWnd i może zostać zastąpione w klasie pochodnej w celu wykonania dodatkowych akcji przed rozpoczęciem animacji dla określonej grupy.

##  <a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

Wywoływane przez platformę, aby rozwiązać konflikty planowania.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Grupa będąca właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNew*<br/>
Grupa będąca właścicielem nowego scenorysu, który jest w trakcie planowania konfliktu z zaplanowanym scenorysem należącym do pGroupScheduled.

*priorityEffect*<br/>
Potencjalny wpływ na pGroupNew, jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić wartość TRUE, jeśli scenorys, którego właścicielem jest pGroupNew, ma priorytet. Powinien zwrócić wartość FALSE, jeśli scenorys, którego właścicielem jest pGroupScheduled, ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń porównania priorytetów przy użyciu CAnimationController:: EnablePriorityComparisonHandler i określania UI_ANIMATION_PHT_CANCEL. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Wywoływane przez platformę, aby rozwiązać konflikty planowania.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Grupa będąca właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNew*<br/>
Grupa będąca właścicielem nowego scenorysu, który jest w trakcie planowania konfliktu z zaplanowanym scenorysem należącym do pGroupScheduled.

*priorityEffect*<br/>
Potencjalny wpływ na pGroupNew, jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić wartość TRUE, jeśli scenorys, którego właścicielem jest pGroupNew, ma priorytet. Powinien zwrócić wartość FALSE, jeśli scenorys, którego właścicielem jest pGroupScheduled, ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń porównania priorytetów przy użyciu CAnimationController:: EnablePriorityComparisonHandler i określania UI_ANIMATION_PHT_COMPRESS. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude

Wywoływane przez platformę, aby rozwiązać konflikty planowania.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Grupa będąca właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNew*<br/>
Grupa będąca właścicielem nowego scenorysu, który jest w trakcie planowania konfliktu z zaplanowanym scenorysem należącym do pGroupScheduled.

*priorityEffect*<br/>
Potencjalny wpływ na pGroupNew, jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić wartość TRUE, jeśli scenorys, którego właścicielem jest pGroupNew, ma priorytet. Powinien zwrócić wartość FALSE, jeśli scenorys, którego właścicielem jest pGroupScheduled, ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń porównania priorytetów przy użyciu CAnimationController:: EnablePriorityComparisonHandler i określania UI_ANIMATION_PHT_CONCLUDE. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

Wywoływane przez platformę, aby rozwiązać konflikty planowania.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parametry

*pGroupScheduled*<br/>
Grupa będąca właścicielem aktualnie zaplanowanego scenorysu.

*pGroupNew*<br/>
Grupa będąca właścicielem nowego scenorysu, który jest w trakcie planowania konfliktu z zaplanowanym scenorysem należącym do pGroupScheduled.

*priorityEffect*<br/>
Potencjalny wpływ na pGroupNew, jeśli pGroupScheduled ma wyższy priorytet.

### <a name="return-value"></a>Wartość zwracana

Należy zwrócić wartość TRUE, jeśli scenorys, którego właścicielem jest pGroupNew, ma priorytet. Powinien zwrócić wartość FALSE, jeśli scenorys, którego właścicielem jest pGroupScheduled, ma priorytet.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń porównania priorytetów przy użyciu CAnimationController:: EnablePriorityComparisonHandler i określania UI_ANIMATION_PHT_TRIM. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji. Przeczytaj dokumentację interfejsu API animacji systemu Windows, aby uzyskać więcej informacji na temat [zarządzania konfliktami](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged

Wywoływane przez platformę, gdy stan scenorysu został zmieniony.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy animacji, która jest właścicielem scenorysu, którego stan zmienił się.

*newStatus*<br/>
Określa nowy stan.

*previousStatus*<br/>
Określa poprzedni stan.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń scenorysu przy użyciu CAnimationController:: EnableStoryboardEventHandler. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated

Wywoływane przez platformę, gdy scenorys został zaktualizowany.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parametry

*pGroup*<br/>
Wskaźnik do grupy, która jest właścicielem scenorysu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w przypadku włączenia zdarzeń scenorysu przy użyciu CAnimationController:: EnableStoryboardEventHandler. Można go zastąpić w klasie pochodnej, aby wykonać działania specyficzne dla aplikacji.

##  <a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Usuwa wszystkie grupy animacji z kontrolera animacji.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Uwagi

Wszystkie grupy zostaną usunięte, ich wskaźniki, jeśli są przechowywane na poziomie aplikacji, muszą być unieważnione. Jeśli CAnimationGroup:: m_bAutodestroyAnimationObjects dla usuwanej grupy ma wartość TRUE, wszystkie obiekty animacji należące do tej grupy zostaną usunięte; w przeciwnym razie odwołania do nadrzędnego kontrolera animacji zostaną ustawione na wartość NULL i można je dodać do innego kontrolera.

##  <a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Usuwa grupę animacji z określonym IDENTYFIKATORem z kontrolera animacji.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy animacji.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę animacji z wewnętrznej listy grup i usuwa ją, dlatego jeśli do tej grupy animacji jest przechowywany wskaźnik, musi on być unieważniony. Jeśli CAnimationGroup:: m_bAutodestroyAnimationObjects ma wartość TRUE, wszystkie obiekty animacji należące do tej grupy zostaną usunięte. w przeciwnym razie odwołania do nadrzędnego kontrolera animacji zostaną ustawione na wartość NULL i można je dodać do innego kontrolera.

##  <a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Usuń obiekt animacji z kontrolera animacji.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Wskaźnik do obiektu animacji.

*bNoDelete*<br/>
Jeśli ten parametr ma wartość TRUE, obiekt nie zostanie usunięty po usunięciu.

### <a name="remarks"></a>Uwagi

Usuwa obiekt animacji z kontrolera animacji i grupy animacji. Wywołaj tę funkcję, jeśli określony obiekt nie powinien już być animowany lub jeśli musisz przenieść obiekt na inny kontroler animacji. W ostatnim przypadku bNoDelete musi mieć wartość TRUE.

##  <a name="removetransitions"></a>CAnimationController::RemoveTransitions

Usuwa przejścia z obiektów animacji należących do określonej grupy.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

### <a name="remarks"></a>Uwagi

Grupa jest pętlą względem obiektów animacji i wywołuje ClearTransitions (FALSE) dla każdego obiektu animacji. Ta metoda jest wywoływana przez platformę po zaplanowaniu animacji.

##  <a name="schedulegroup"></a>CAnimationController:: Schedule — lista

Planuje animację.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy animacji do zaplanowania.

*czas*<br/>
Określa czas do zaplanowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli animacja została zaplanowana pomyślnie. Wartość FALSE, jeśli scenorys nie został utworzony lub Wystąpił inny błąd.

### <a name="remarks"></a>Uwagi

Musisz wywołać animację z parametrem bScheduleNow ustawionym na wartość FALSE przed poprzednią funkcją Schedule. Można określić żądany czas animacji uzyskany z IUIAnimationTimer:: GetTime. Jeśli parametr czasu to 0,0, animacja jest zaplanowana na bieżącą godzinę.

##  <a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Ustanawia relację między kontrolerem animacji a oknem.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do obiektu okna do ustawienia.

### <a name="remarks"></a>Uwagi

Jeśli pokrewny obiekt CWnd jest ustawiony, kontroler animacji może automatycznie zaktualizować go (wysłać wiadomość WM_PAINT), gdy wystąpił stan Menedżera animacji lub zdarzenie po aktualizacji.

##  <a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Kieruje Menedżera animacji do aktualizowania wartości wszystkich zmiennych animacji.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody powoduje przejście Menedżera animacji do bieżącego czasu, zmianę stanu scenorysów w razie potrzeby i zaktualizowanie wszelkich zmiennych animacji do odpowiednich interpolowanych wartości. Wewnętrznie ta metoda wywołuje IUIAnimationTimer:: GetTime (timeNow) i IUIAnimationManager:: Update (timeNow). Zastąp tę metodę w klasie pochodnej, aby dostosować to zachowanie.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
