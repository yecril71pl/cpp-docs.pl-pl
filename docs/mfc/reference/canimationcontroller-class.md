---
title: Klasa CAnimationController | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ec93c2d39206bbc0c3076835f55e624d3eef715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356927"
---
# <a name="canimationcontroller-class"></a>Klasa CAnimationController
Implementuje kontrolera animacji, który udostępnia interfejs centralnej do tworzenia i zarządzania animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationController : public CObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationController::CAnimationController](#canimationcontroller)|Tworzy kontroler animacji.|  
|[CAnimationController:: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu kontrolera animacji.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](#addanimationobject)|Dodaje obiekt animacji do grupy, który należy do kontrolera animacji.|  
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Dodaje kluczową do grupy.|  
|[CAnimationController::AnimateGroup](#animategroup)|Przygotowuje grupy do uruchomienia animacji i opcjonalnie umożliwia zaplanowanie.|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Przeciążone. Wywoływane przez platformę, aby wyczyścić grupy, gdy zaplanowano animacji.|  
|[CAnimationController::CreateKeyframe](#createkeyframe)|Przeciążone. Tworzy klatki kluczowej, która jest zależna od przejścia i dodaje go do określonej grupy.|  
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Ustawia lub zwalnia obsługi do wywołania po zmianie stanu Menedżera animacji.|  
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Ustawia lub zwalnia obsługi dla zdarzenia czasowe i obsługę chronometrażu aktualizacji.|  
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Ustawia lub zwalnia obsługi porównania priorytet wywołanie w celu sprawdzenia, czy zaplanowane scenorysu można być anulowana, zawartych, przycięty skompresowane.|  
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Ustawia lub zwalnia program obsługi zdarzeń stanu i aktualizowania scenorysu.|  
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Przeciążone. Znajduje grupy animacji przy jego scenorysu.|  
|[CAnimationController::FindAnimationObject](#findanimationobject)|Umożliwia znalezienie zawierającego zmienną animacji określonego obiektu animacji.|  
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Zwraca kluczową określający początek scenorysu.|  
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Zapewnia dostęp do obiektu IUIAnimationManager hermetyzowany.|  
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Zapewnia dostęp do obiektu IUIAnimationTimer hermetyzowany.|  
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Wskaźnik do interfejsu IUIAnimationTransitionFactory lub wartość NULL, jeśli nie można utworzyć biblioteki przejścia.|  
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Zapewnia dostęp do obiektu IUIAnimationTransitionLibrary hermetyzowany.|  
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Informuje, czy co najmniej jedną grupę odtwarzania animacji.|  
|[CAnimationController::IsValid](#isvalid)|Informuje, czy animacja kontrolera jest nieprawidłowy.|  
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Wywoływane przez platformę, gdy zmieniono wartość całkowitą typu zmienną animacji.|  
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Wywoływane przez platformę w odpowiedzi na zdarzenie StatusChanged z Menedżera animacji.|  
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Wywoływane przez platformę po zakończeniu aktualizacji animacji.|  
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Wywoływane przez platformę przed rozpoczęciem aktualizacji animacji.|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Wywoływane przez platformę, gdy szybkość renderowania animacji spadnie poniżej minimalnej pożądane szybkości.|  
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Wywoływane przez platformę, gdy zmieniono wartość zmiennej animacji.|  
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Wywoływane przez platformę, prawy przed zaplanowaniem animacji.|  
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Wywoływane przez platformę, by rozwiązać konflikty planowania.|  
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Wywoływane przez platformę, by rozwiązać konflikty planowania.|  
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Wywoływane przez platformę, by rozwiązać konflikty planowania.|  
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Wywoływane przez platformę, by rozwiązać konflikty planowania.|  
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Wywoływane przez platformę, gdy zostanie zmieniony stan scenorysu.|  
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Wywoływane przez platformę, gdy scenorysu został zaktualizowany.|  
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Usuwa wszystkie grupy animacji z kontrolera animacji.|  
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Usuwa grupę animacji, o określonym identyfikatorze z kontrolera animacji.|  
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Usuń obiekt animacji z kontrolera animacji.|  
|[CAnimationController::RemoveTransitions](#removetransitions)|Usuwa przejścia z obiektów animacji, które należą do określonej grupy.|  
|[CAnimationController::ScheduleGroup](#schedulegroup)|Planuje animacji.|  
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Ustanawia relację między kontrolerem animacji i okna.|  
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Określa, że Menedżer animacji, aby zaktualizować wartości zmiennych animacji.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Przeciążone. Obiekt pomocnika czyści grupy.|  
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Wywoływane przez platformę, gdy właśnie zostało zaplanowane animacji dla określonej grupy.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Kluczową reprezentujący początek scenorysu.|  
|[CAnimationController::m_bIsValid](#m_bisvalid)|Określa, czy kontroler animacji jest prawidłowa. Ten element członkowski ma ustawioną wartość FALSE, jeśli bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji.|  
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Lista grup animacji, które należą do tego kontrolera animacji.|  
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Przechowuje wskaźnik do obiektu COM Menedżera animacji.|  
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Przechowuje wskaźnik do obiektu COM czasomierza animacji.|  
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Wskaźnik do obiektu pokrewnego CWnd, które można automatycznie odświeżać, gdy zmienił się stan Menedżera animacji lub po aktualizacji zdarzenia. Może mieć wartości NULL.|  
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Przechowuje wskaźnik do obiektu COM fabryki przejścia.|  
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Przechowuje wskaźnik do obiektu COM biblioteki przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationController jest klucza klasy, która zarządza animacji. Może utworzyć co najmniej jedno wystąpienie kontrolera animacji w aplikacji i, opcjonalnie, Połącz wystąpienie kontrolera animacji z obiektem CWnd, przy użyciu CAnimationController::SetRelatedWnd. To połączenie jest wymagana do WM_PAINT automatyczne wysyłanie wiadomości do okna pokrewne animacji Menedżera stan został zmieniony lub czasomierza animacja została zaktualizowana. Jeśli ta relacja nie zostanie włączone, należy odświeżyć okno wyświetla animacji ręcznie. W tym celu można wyprowadzenia klasy z CAnimationController i zastąpić OnAnimationManagerStatusChanged i/lub OnAnimationTimerPostUpdate i unieważnić co najmniej jeden windows, gdy jest to konieczne.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationController`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationcontroller"></a>  CAnimationController:: ~ CAnimationController  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu kontrolera animacji.  
  
```  
virtual ~CAnimationController(void);
```   
  
##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject  
 Dodaje obiekt animacji do grupy, który należy do kontrolera animacji.  
  
```  
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Wskaźnik do obiektu animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do istniejącej lub nowej grupy animacji, w którym został dodany pObject Jeśli funkcja zakończy się pomyślnie; Wartość NULL, jeśli pObject został już dodany do grupy, który należy do innego kontrolera animacji.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby dodać obiekt animacji na kontrolerze animacji. Obiekt zostanie dodany do grupy, zgodnie z identyfikatorem obiektu grupy (zobacz CAnimationBaseObject::SetID). Kontroler animacji spowoduje utworzenie nowej grupy, jeśli pierwszy obiekt dodawany z określonym identyfikatorem grupy. Obiekt animacji można dodać do tylko jednej animacji kontrolera. Jeśli potrzebujesz dodać obiektu do innego kontrolera, należy najpierw wywołać RemoveAnimationObject. Identyfikator zestawu z GroupID nowych połączeń dla obiekt, który został już dodany do grupy, obiekt zostaną usunięte z grupy stary i dodać do innej grupy o określonym identyfikatorze.  
  
##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup  
 Dodaje kluczową do grupy.  
  
```  
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `pKeyframe`  
 Wskaźnik do kluczową.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle nie trzeba wywołać tę metodę, użyj CAnimationController::CreateKeyframe, która tworzy i dodaje kluczową utworzony automatycznie do grupy.  
  
##  <a name="animategroup"></a>  CAnimationController::AnimateGroup  
 Przygotowuje grupy do uruchomienia animacji i opcjonalnie umożliwia zaplanowanie.  
  
```  
BOOL AnimateGroup(
    UINT32 nGroupID,  
    BOOL bScheduleNow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `bScheduleNow`  
 Określa, czy mają być uruchamiane natychmiast animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli animacja została pomyślnie zaplanowane i uruchomić.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wykonuje faktyczną pracę tworzenia scenorysu, Dodawanie animacji zmiennych, stosowania przejścia i ustawiania klatek. Istnieje możliwość opóźnienia, planowania, jeśli bScheduleNow jest ustawiona na FALSE. W takim przypadku określonej grupy będą przechowywane scenorysu, który nie został skonfigurowany dla animacji. W takiej sytuacji należy skonfigurować zdarzenia zmiennych scenorysu i animacji. Gdy faktycznie należy uruchomić CAnimationController::ScheduleGroup wywołanie animacji.  
  
##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController  
 Tworzy kontroler animacji.  
  
```  
CAnimationController(void);
```   
  
##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup  
 Wywoływane przez platformę, aby wyczyścić grupy, gdy zaplanowano animacji.  
  
```  
void CleanUpGroup(UINT32 nGroupID);  
void CleanUpGroup(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `pGroup`  
 Wskaźnik do grupy animacji, aby wyczyścić.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa wszystkie przejścia i kluczowych z określonej grupy, ponieważ nie mają odpowiednich po zaplanowano animacji.  
  
##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe  
 Tworzy klatki kluczowej, która jest zależna od przejścia i dodaje go do określonej grupy.  
  
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
 `nGroupID`  
 Określa identyfikator grupy, dla której utworzona jest klatki kluczowej.  
  
 `pTransition`  
 Wskaźnik do przejścia. Klatki kluczowej zostanie wstawiony do scenorysu po ten proces przejścia.  
  
 `pKeyframe`  
 Wskaźnik do podstawowego klatki kluczowej dla tego klatki kluczowej.  
  
 `offset`  
 Przesunięcie w sekundach od podstawowej klatki kluczowej, określony przez pKeyframe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonej klatki kluczowej, jeśli funkcja zakończy się powodzeniem.  
  
### <a name="remarks"></a>Uwagi  
 Można przechowywać zwrócony wskaźnik i podstawą innych klatki kluczowej nowo utworzony (Zobacz drugi przeciążenia). Istnieje możliwość rozpoczęcia przejścia na kluczowych — Zobacz CBaseTransition::SetKeyframes. Nie trzeba usunąć kluczowych utworzone w ten sposób, ponieważ są usuwane automatycznie przez grupy animacji. Należy zachować ostrożność podczas tworzenia klatek na podstawie innych klatek kluczowych i przejścia i uniknąć odwołań cyklicznych.  
  
##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent  
 Ustawia lub zwalnia obsługi do wywołania po zmianie stanu Menedżera animacji.  
  
```  
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Określa, czy ustawienie lub wyłączenie obsługi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydane.  
  
### <a name="remarks"></a>Uwagi  
 Gdy program obsługi ma wartość (włączone) animacji Windows wywołuje OnAnimationManagerStatusChanged po zmianie stanu Menedżera animacji.  
  
##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler  
 Ustawia lub zwalnia obsługi dla zdarzenia czasowe i obsługę chronometrażu aktualizacji.  
  
```  
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,  
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Określa, czy ustawienie lub wyłączenie obsługi.  
  
 `idleBehavior`  
 Określa zachowanie bezczynności czasomierza programu obsługi aktualizacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli programy obsługi pomyślnie zostały ustawione lub wydane; Wartość FALSE, jeśli ta metoda jest wywoływana raz drugi bez najpierw zwalniania obsługi lub jeśli inne wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Podczas obsługi są ustawiane (włączone) wywołań interfejsu API systemu Windows animacji OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow metody. Musisz włączyć czasomierze animacji umożliwia scenorys aktualizacji interfejsu API systemu Windows animacji. W przeciwnym razie należy wywołać CAnimationController::UpdateAnimationManager aby skierować animacji manager, aby zaktualizować wartości zmiennych animacji.  
  
##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler  
 Ustawia lub zwalnia obsługi porównania priorytet wywołanie w celu sprawdzenia, czy zaplanowane scenorysu można być anulowana, zawartych, przycięty skompresowane.  
  
```  
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```  
  
### <a name="parameters"></a>Parametry  
 `dwHandlerType`  
 Kombinacja UI_ANIMATION_PHT_ flagi (zobacz Uwagi), która określa, jakie programy obsługi się ustawienie lub wyłączenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydane.  
  
### <a name="remarks"></a>Uwagi  
 Gdy program obsługi ma wartość (włączone) animacji systemu Windows wymaga następujących metod wirtualnych, w zależności od dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler może być kombinacją następujące flagi: UI_ANIMATION_PHT_NONE - wersji wszystkich programów obsługi UI_ANIMATION_PHT_CANCEL — Ustawianie Anuluj porównanie obsługi UI_ANIMATION_PHT_CONCLUDE - ustawić programu obsługi porównanie Conclude UI_ANIMATION_PHT_COMPRESS — Ustawianie Kompresuj porównanie obsługi UI_ANIMATION_PHT_TRIM - ustawić programu obsługi przycinania porównanie UI_ANIMATION_PHT_CANCEL_REMOVE - Usuń Anuluj porównanie obsługi UI_ANIMATION_PHT_CONCLUDE_REMOVE - Usuń Conclude porównanie obsługi UI_ANIMATION_PHT_COMPRESS_ Usuń - Usuwa Kompresuj porównanie obsługi UI_ANIMATION_PHT_TRIM_REMOVE - Usuń przycinania porównanie obsługi  
  
##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler  
 Ustawia lub zwalnia program obsługi zdarzeń stanu i aktualizowania scenorysu.  
  
```  
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `bEnable`  
 Określa, czy ustawienie lub wyłączenie obsługi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli program obsługi został pomyślnie ustawiony lub wydane; Wartość FALSE, jeśli teraz znaleźć grupy animacji określony lub nie została zainicjowana animacji dla określonej grupy i jego wewnętrznego scenorysu ma wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Gdy program obsługi ma wartość interfejsu API animacji (włączone) systemu Windows wywołuje OnStoryboardStatusChanges i OnStoryboardUpdated metodach wirtualnych. Program obsługi musi mieć wartość po wywołaniu CAnimationController::Animate grupy określonej animacji, ponieważ tworzy hermetyzowany IUIAnimationStoryboard obiektu.  
  
##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup  
 Odnajduje grupę animacji przez jego identyfikator grupy.  
  
```  
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);  
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik grupą animacji lub wartość NULL, jeśli nie znaleziono grupy o określonym identyfikatorze.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody można znaleźć grupy animacji w czasie wykonywania. Grupy jest tworzony i dodawany do wewnętrznej listy grup animacji, gdy pierwszy obiekt animacji z określonym identyfikatorem grupy jest dodawany do kontrolera animacji.  
  
##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject  
 Umożliwia znalezienie zawierającego zmienną animacji określonego obiektu animacji.  
  
```  
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,  
    CAnimationBaseObject** ppObject,  
    CAnimationGroup** ppGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Wskaźnik do zmiennej animacji.  
  
 `ppObject`  
 Dane wyjściowe. Zawiera wskaźnik do obiektu animacji lub wartość NULL.  
  
 `ppGroup`  
 Dane wyjściowe. Zawiera wskaźnik do grupy animacji, która zawiera obiekt animacji lub wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli obiekt został odnaleziony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływane z obsługi zdarzeń, gdy są wymagane, aby znaleźć obiektu animacji na podstawie przychodzącego zmiennej animacji.  
  
##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart  
 Kluczową reprezentujący początek scenorysu.  
  
```  
static CBaseKeyFrame gkeyframeStoryboardStart;  
```  
  
##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart  
 Zwraca kluczową określający początek scenorysu.  
  
```  
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do podstawowego klatki kluczowej, która identyfikuje początku scenorysu.  
  
### <a name="remarks"></a>Uwagi  
 Uzyskaj to klatki kluczowej do podstawowej innych kluczowych lub przejścia w chwili rozpoczęcia scenorysu.  
  
##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager  
 Zapewnia dostęp do obiektu IUIAnimationManager hermetyzowany.  
  
```  
IUIAnimationManager* GetUIAnimationManager();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IUIAnimationManager lub wartość NULL, jeśli nie można utworzyć Menedżera animacji.  
  
### <a name="remarks"></a>Uwagi  
 Bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji, ta metoda zwraca wartość NULL, a następnie zwraca wartość FALSE, wszystkie kolejne wywołania na CAnimationController::IsValid. Konieczne może być dostęp IUIAnimationManager aby wywoływać metod interfejsu, które nie zostały opakowane przez kontrolera animacji.  
  
##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer  
 Zapewnia dostęp do obiektu IUIAnimationTimer hermetyzowany.  
  
```  
IUIAnimationTimer* GetUIAnimationTimer();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IUIAnimationTimer lub wartość NULL, jeśli nie można utworzyć czasomierza animacji.  
  
### <a name="remarks"></a>Uwagi  
 Bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji, ta metoda zwraca wartość NULL, a następnie zwraca wartość FALSE, wszystkie kolejne wywołania na CAnimationController::IsValid.  
  
##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory  
 Wskaźnik do interfejsu IUIAnimationTransitionFactory lub wartość NULL, jeśli nie można utworzyć biblioteki przejścia.  
  
```  
IUIAnimationTransitionFactory* GetUITransitionFactory();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do IUIAnimationTransitionFactory lub wartość NULL, jeśli nie można utworzyć fabryki przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji, ta metoda zwraca wartość NULL, a następnie zwraca wartość FALSE, wszystkie kolejne wywołania na CAnimationController::IsValid.  
  
##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary  
 Zapewnia dostęp do obiektu IUIAnimationTransitionLibrary hermetyzowany.  
  
```  
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu IUIAnimationTransitionLibrary lub wartość NULL, jeśli nie można utworzyć biblioteki przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji, ta metoda zwraca wartość NULL, a następnie zwraca wartość FALSE, wszystkie kolejne wywołania na CAnimationController::IsValid.  
  
##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress  
 Informuje, czy co najmniej jedną grupę odtwarzania animacji.  
  
```  
virtual BOOL IsAnimationInProgress();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli istnieje animacji w toku dla tego kontrolera animacji; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia sprawdzenie stanu Menedżera animacji i zwraca wartość TRUE, jeśli stan jest UI_ANIMATION_MANAGER_BUSY.  
  
##  <a name="isvalid"></a>  CAnimationController::IsValid  
 Informuje, czy animacja kontrolera jest nieprawidłowy.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli kontroler animacji jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ten — metoda zwraca wartość FALSE tylko wtedy, gdy interfejs API systemu Windows animacji nie jest obsługiwana w bieżącego systemu operacyjnego i tworzenie Menedżera animacji nie powiodło się, ponieważ nie jest zarejestrowany. Należy wywołać GetUIAnimationManager co najmniej raz po zainicjowaniu bibliotek COM powoduje ustawienie tej flagi.  
  
##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid  
 Określa, czy kontroler animacji jest prawidłowa. Ten element członkowski ma ustawioną wartość FALSE, jeśli bieżący system operacyjny nie obsługuje interfejsu API systemu Windows animacji.  
  
```  
BOOL m_bIsValid;  
```  
  
##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups  
 Lista grup animacji, które należą do tego kontrolera animacji.  
  
```  
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;  
```  
  
##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager  
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
 Wskaźnik do obiektu pokrewnego CWnd, które można automatycznie odświeżać, gdy zmienił się stan Menedżera animacji lub po aktualizacji zdarzenia. Może mieć wartości NULL.  
  
```  
CWnd* m_pRelatedWnd;  
```  
  
##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory  
 Przechowuje wskaźnik do obiektu COM fabryki przejścia.  
  
```  
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;  
```  
  
##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary  
 Przechowuje wskaźnik do obiektu COM biblioteki przejścia.  
  
```  
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;  
```  
  
##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule  
 Wywoływane przez platformę, gdy właśnie zostało zaplanowane animacji dla określonej grupy.  
  
```  
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy animacji, które zostało zaplanowane.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja usuwa z określonej grupy klatek kluczowych i przejścia z zmienne animacji, które należą do określonej grupy. Może zostać przesłonięta w klasie pochodnej, aby podejmować dodatkowe akcje w na harmonogram animacji.  
  
##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged  
 Wywoływane przez platformę, gdy zmieniono wartość całkowitą typu zmienną animacji.  
  
```  
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    INT32 newValue,  
    INT32 prevValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy animacji przechowujący obiektu animacji, którego wartość została zmieniona.  
  
 `pObject`  
 Wskaźnik do obiektu animacji, który zawiera zmienną animacji, którego wartość została zmieniona.  
  
 `variable`  
 Wskaźnik do zmiennej animacji.  
  
 `newValue`  
 Określa nową wartość.  
  
 `prevValue`  
 Określa poprzedniej wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu animacji zmiennej zdarzenia z EnableIntegerValueChangedEvent wywołana dla określonych animacji zmiennej lub obiektu animacji. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged  
 Wywoływane przez platformę w odpowiedzi na zdarzenie StatusChanged z Menedżera animacji.  
  
```  
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,  
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `newStatus`  
 Nowy stan Menedżera animacji.  
  
 `previousStatus`  
 Poprzedni stan Menedżera animacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu zdarzeń z Menedżera animacji z EnableAnimationManagerEvent. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Domyślna implementacja aktualizuje powiązane okna, jeśli została ustawiona z SetRelatedWnd.  
  
##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate  
 Wywoływane przez platformę po zakończeniu aktualizacji animacji.  
  
```  
virtual void OnAnimationTimerPostUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate  
 Wywoływane przez platformę przed rozpoczęciem aktualizacji animacji.  
  
```  
virtual void OnAnimationTimerPreUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow  
 Wywoływane przez platformę, gdy szybkość renderowania animacji spadnie poniżej minimalnej pożądane szybkości.  
  
```  
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```  
  
### <a name="parameters"></a>Parametry  
 `fps`  
 Bieżąca szybkość klatek w klatkach na sekundę.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu obsługi zdarzeń czasomierza przy użyciu EnableAnimationTimerEventHandler. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Minimalna szybkość pożądane jest określona przez wywołanie metody IUIAnimationTimer::SetFrameRateThreshold.  
  
##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged  
 Wywoływane przez platformę, gdy zmieniono wartość zmiennej animacji.  
  
```  
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    DOUBLE newValue,  
    DOUBLE prevValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy animacji przechowujący obiektu animacji, którego wartość została zmieniona.  
  
 `pObject`  
 Wskaźnik do obiektu animacji, który zawiera zmienną animacji, którego wartość została zmieniona.  
  
 `variable`  
 Wskaźnik do zmiennej animacji.  
  
 `newValue`  
 Określa nową wartość.  
  
 `prevValue`  
 Określa poprzedniej wartości.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu animacji zmiennej zdarzenia z EnableValueChangedEvent wywołana dla określonych animacji zmiennej lub obiektu animacji. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart  
 Wywoływane przez platformę, prawy przed zaplanowaniem animacji.  
  
```  
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy animacji, którego animacja się uruchomić.  
  
### <a name="remarks"></a>Uwagi  
 To wywołanie jest kierowany do CWnd pokrewne i może zostać przesłonięta w klasie pochodnej, aby wykonywać żadnych dodatkowych akcji przed uruchomieniem animacji dla określonej grupy.  
  
##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel  
 Wywoływane przez platformę, by rozwiązać konflikty planowania.  
  
```  
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Grupę, do której należy obecnie zaplanowane scenorysu.  
  
 `pGroupNew`  
 Grupę, do której należy nowego scenorysu, który jest w planowaniu konflikt z zaplanowanym scenorysu własnością pGroupScheduled.  
  
 `priorityEffect`  
 Potencjalny wpływ na pGroupNew Jeśli pGroupScheduled ma wyższy priorytet.  
  
### <a name="return-value"></a>Wartość zwracana  
 Należy zwraca wartość TRUE, jeśli scenorysu własnością pGroupNew ma priorytet. Powinna zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu priorytet porównania zdarzenia przy użyciu CAnimationController::EnablePriorityComparisonHandler i określ UI_ANIMATION_PHT_CANCEL. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Dokumentacji interfejsu API animacji Windows odczytu więcej informacji na temat zarządzania (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress  
 Wywoływane przez platformę, by rozwiązać konflikty planowania.  
  
```  
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Grupę, do której należy obecnie zaplanowane scenorysu.  
  
 `pGroupNew`  
 Grupę, do której należy nowego scenorysu, który jest w planowaniu konflikt z zaplanowanym scenorysu własnością pGroupScheduled.  
  
 `priorityEffect`  
 Potencjalny wpływ na pGroupNew Jeśli pGroupScheduled ma wyższy priorytet.  
  
### <a name="return-value"></a>Wartość zwracana  
 Należy zwraca wartość TRUE, jeśli scenorysu własnością pGroupNew ma priorytet. Powinna zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu priorytet porównania zdarzenia przy użyciu CAnimationController::EnablePriorityComparisonHandler i określ UI_ANIMATION_PHT_COMPRESS. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Dokumentacji interfejsu API animacji Windows odczytu więcej informacji na temat zarządzania (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude  
 Wywoływane przez platformę, by rozwiązać konflikty planowania.  
  
```  
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Grupę, do której należy obecnie zaplanowane scenorysu.  
  
 `pGroupNew`  
 Grupę, do której należy nowego scenorysu, który jest w planowaniu konflikt z zaplanowanym scenorysu własnością pGroupScheduled.  
  
 `priorityEffect`  
 Potencjalny wpływ na pGroupNew Jeśli pGroupScheduled ma wyższy priorytet.  
  
### <a name="return-value"></a>Wartość zwracana  
 Należy zwraca wartość TRUE, jeśli scenorysu własnością pGroupNew ma priorytet. Powinna zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu priorytet porównania zdarzenia przy użyciu CAnimationController::EnablePriorityComparisonHandler i określ UI_ANIMATION_PHT_CONCLUDE. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Dokumentacji interfejsu API animacji Windows odczytu więcej informacji na temat zarządzania (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim  
 Wywoływane przez platformę, by rozwiązać konflikty planowania.  
  
```  
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroupScheduled`  
 Grupę, do której należy obecnie zaplanowane scenorysu.  
  
 `pGroupNew`  
 Grupę, do której należy nowego scenorysu, który jest w planowaniu konflikt z zaplanowanym scenorysu własnością pGroupScheduled.  
  
 `priorityEffect`  
 Potencjalny wpływ na pGroupNew Jeśli pGroupScheduled ma wyższy priorytet.  
  
### <a name="return-value"></a>Wartość zwracana  
 Należy zwraca wartość TRUE, jeśli scenorysu własnością pGroupNew ma priorytet. Powinna zwrócić FALSE, jeśli scenorysu własnością pGroupScheduled ma priorytet.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu priorytet porównania zdarzenia przy użyciu CAnimationController::EnablePriorityComparisonHandler i określ UI_ANIMATION_PHT_TRIM. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji. Dokumentacji interfejsu API animacji Windows odczytu więcej informacji na temat zarządzania (http://msdn.microsoft.com/library/dd371759(VS.85).aspx).  
  
##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged  
 Wywoływane przez platformę, gdy zostanie zmieniony stan scenorysu.  
  
```  
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,  
    UI_ANIMATION_STORYBOARD_STATUS newStatus,  
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy animacji, który jest właścicielem scenorysu, których stan zmienił się.  
  
 `newStatus`  
 Określa nowy stan.  
  
 `previousStatus`  
 Określa poprzedniego stanu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu scenorysu zdarzenia przy użyciu CAnimationController::EnableStoryboardEventHandler. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated  
 Wywoływane przez platformę, gdy scenorysu został zaktualizowany.  
  
```  
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `pGroup`  
 Wskaźnik do grupy, który jest właścicielem scenorysu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana po włączeniu scenorysu zdarzenia przy użyciu CAnimationController::EnableStoryboardEventHandler. Może zostać przesłonięta w klasie pochodnej w celu podjęcia działań specyficzne dla aplikacji.  
  
##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups  
 Usuwa wszystkie grupy animacji z kontrolera animacji.  
  
```  
void RemoveAllAnimationGroups();
```  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie grupy będą usunięte, wskaźnika, jeśli przechowywane na poziomie aplikacji musi unieważnione. Gdy CAnimationGroup::m_bAutodestroyAnimationObjects dla grupy, usuwany jest wartość PRAWDA, zostaną usunięte wszystkie obiekty animacji, które należą do tej grupy; w przeciwnym razie ich odwołania do kontrolera elementu nadrzędnego animacji zostanie ustawiona na wartość NULL i będzie możliwe ich dodanie do innego kontrolera.  
  
##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup  
 Usuwa grupę animacji, o określonym identyfikatorze z kontrolera animacji.  
  
```  
void RemoveAnimationGroup(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy animacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa grupę animacji z wewnętrznej listy grup i usuwa je, dlatego jeśli przechowywany wskaźnik do tej grupy animacji, jego musi unieważnione. Jeśli CAnimationGroup::m_bAutodestroyAnimationObjects ma wartość PRAWDA, zostaną usunięte wszystkie obiekty animacji, które należą do tej grupy; w przeciwnym razie ich odwołania do kontrolera elementu nadrzędnego animacji zostanie ustawiona na wartość NULL i będzie możliwe ich dodanie do innego kontrolera.  
  
##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject  
 Usuń obiekt animacji z kontrolera animacji.  
  
```  
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,  
    BOOL bNoDelete = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Wskaźnik do obiektu animacji.  
  
 `bNoDelete`  
 Jeśli ten parametr ma wartość TRUE nie można usunąć obiektu na usuwanie.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa obiekt animacji z kontrolera animacji i grupy animacji. Wywołanie tej funkcji, jeśli określony obiekt nie można animować już lub musisz przenieść obiekt na inny kontroler animacji. W ciągu ostatnich case bNoDelete musi mieć wartość TRUE.  
  
##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions  
 Usuwa przejścia z obiektów animacji, które należą do określonej grupy.  
  
```  
void RemoveTransitions(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
### <a name="remarks"></a>Uwagi  
 Grupa pętli jej obiektów animacji i wywołuje ClearTransitions(FALSE) dla każdego obiektu animacji. Ta metoda jest wywoływana przez platformę po zaplanowano animacji.  
  
##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup  
 Planuje animacji.  
  
```  
BOOL ScheduleGroup(
    UINT32 nGroupID,  
    UI_ANIMATION_SECONDS time = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy można zaplanować animacji.  
  
 `time`  
 Określa czas, aby zaplanować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli animacja została zaplanowana pomyślnie. Wartość FALSE, jeśli nie utworzono scenorysu lub inny błąd występuje.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać AnimateGroup z parametru bScheduleNow ustawiona na wartość FALSE przed schedulegroup —. Można określić czas żądaną animacji uzyskane z IUIAnimationTimer::GetTime. Jeśli parametr time 0.0, animacji jest zaplanowane dla bieżącego czasu.  
  
##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd  
 Ustanawia relację między kontrolerem animacji i okna.  
  
```  
void SetRelatedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do obiektu okna, aby ustawić.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli powiązany obiekt CWnd jest ustawiona, kontrolera animacji mogą być automatycznie aktualizowane (Wyślij komunikat WM_PAINT) gdy zmienił stan Menedżera animacji lub czasomierza post aktualizacji zdarzenia.  
  
##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager  
 Określa, że Menedżer animacji, aby zaktualizować wartości zmiennych animacji.  
  
```  
virtual void UpdateAnimationManager();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie, którego ta metoda przesuwa Menedżera animacji na bieżący czas, zmiana stany scenorys odpowiednio do potrzeb i aktualizowania zmiennych animacji do odpowiedniej interpolowane wartości. Wewnętrznie ta metoda wywołuje IUIAnimationTimer::GetTime(timeNow) i IUIAnimationManager::Update(timeNow). Zastępuje tę metodę w klasie pochodnej, aby dostosować ten problem.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
