---
title: Klasa CAnimationGroup | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d047940ac1ef3103168aa40b53c726ce0767b52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationgroup-class"></a>Klasa CAnimationGroup
Implementuje grupy animacji, które łączy scenorysu animacji, obiekty animacji i przejść do definiowania animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationGroup;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Tworzy grupę animacji.|  
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|Destruktor. Wywoływane, gdy trwa niszczenie grupy animacji.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationGroup::Animate](#animate)|Animuje grupy.|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Dotyczy przejścia obiektów animacji.|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Znajduje obiekt animacji, który zawiera zmienną określonego animacji.|  
|[CAnimationGroup::GetGroupID](#getgroupid)|Zwraca identyfikator grupy.|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Usuwa i opcjonalnie niszczy wszystkich kluczowych, które należą do grupy animacji.|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Usuwa przejścia z obiektów animacji, które należą do grupy animacji.|  
|[CAnimationGroup::Schedule](#schedule)|Planuje animacji w określonym czasie.|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Poleca się, że wszystkie obiekty animacji, które należą do grupy automatycznie zniszczyć przejścia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocnik, który dodaje klatek kluczowych do scenorysu.|  
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocnik, który dodaje przejścia do scenorysu.|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocnik, która tworzy obiekty COM przejścia.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Określa, jak wyczyścić przejścia z obiektów animacji, które należą do grupy. Jeśli ten element członkowski ma wartość PRAWDA, przejścia są usuwane automatycznie, gdy zaplanowano animacji. W przeciwnym razie należy ręcznie usunąć przejścia.|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Określa, jak można zniszczyć obiekty animacji. Jeśli ten parametr ma wartość TRUE, obiekty animacji zostanie automatycznie zniszczona, gdy grupa zostanie zniszczony. W przeciwnym razie animacji obiekty muszą zostać zniszczone ręcznie. Wartość domyślna to FALSE. Ta wartość TRUE tylko wtedy, gdy wszystkie obiekty animacji, które należą do grupy są dynamicznie przydzielane z nowy operator.|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Określa, jak można zniszczyć klatek. Jeśli ta wartość wynosi TRUE, wszystkich kluczowych są usuwane i zniszczone; w przeciwnym razie usuwane są tylko na liście. Wartość domyślna to TRUE.|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Zawiera listę obiektów animacji.|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Zawiera listę klatek.|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Wskazuje scenorysu animacji. Ten wskaźnik jest prawidłowy tylko po wywołaniu na Animuj.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Unikatowy identyfikator grupy animacji.|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Wskaźnik do kontrolera animacji, do której należy ta grupa.|  
  
## <a name="remarks"></a>Uwagi  
 Animacja grupy są tworzone automatycznie przez kontroler animacji (CAnimationController) po dodaniu obiektów animacji przy użyciu CAnimationController::AddAnimationObject. Grupy animacji jest identyfikowany przez identyfikator GroupID, który zazwyczaj jest traktowana jako parametr do manipulowania grupami animacji. Identyfikator grupy jest pobierana z pierwszego obiektu animacji dodawana do nowej grupy animacji. Scenorysu hermetyzowany animacji jest tworzony po wywołać CAnimationController::AnimateGroup i jest dostępny za pośrednictwem m_pStoryboard publicznego elementu członkowskiego.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CAnimationGroup`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>CAnimationGroup:: ~ CAnimationGroup  
 Destruktor. Wywoływane, gdy trwa niszczenie grupy animacji.  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>CAnimationGroup::AddKeyframes  
 Pomocnik, który dodaje klatek kluczowych do scenorysu.  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do obiektu storyboard COM.  
  
 `bAddDeep`  
 Określa, czy ta metoda należy dodać do kluczowych scenorysu, które są zależne od innych klatek.  
  
##  <a name="addtransitions"></a>CAnimationGroup::AddTransitions  
 Pomocnik, który dodaje przejścia do scenorysu.  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do obiektu storyboard COM.  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>CAnimationGroup::Animate  
 Animuje grupy.  
  
```  
BOOL Animate(
    IUIAnimationManager* pManager,  
    IUIAnimationTimer* pTimer,  
    BOOL bScheduleNow);
```  
  
### <a name="parameters"></a>Parametry  
 `pManager`  
 `pTimer`  
 `bScheduleNow`  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda utworzy wewnętrzny scenorysu i stosuje przejścia i harmonogramy animacji, jeśli bScheduleNow ma wartość TRUE. Jeśli bScheduleNow ma wartość FALSE, należy wywołać harmonogram, aby uruchomić animacji w określonym czasie.  
  
##  <a name="applytransitions"></a>CAnimationGroup::ApplyTransitions  
 Dotyczy przejścia obiektów animacji.  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda potwierdza w trybie debugowania, jeśli nie utworzono scenorysu. Go najpierw tworzy wszystkie przejścia, a następnie dodaje kluczowych "statyczny" (kluczowych, które są zależne od przesunięcia), dodaje przejścia, które nie są zależne od kluczowych dodaje klatek kluczowych w zależności od przejścia i innych kluczowych i ostatnio dodaje przejścia, które są zależne od kluczowych .  
  
##  <a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup  
 Tworzy grupę animacji.  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentController`  
 Wskaźnik do kontrolera animacji, który tworzy grupę.  
  
 `nGroupID`  
 Określa identyfikator grupy.  
  
##  <a name="createtransitions"></a>CAnimationGroup::CreateTransitions  
 Pomocnik, która tworzy obiekty COM przejścia.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE jest metoda zakończy się powodzeniem, w przeciwnym razie wartość FALSE.  
  
##  <a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject  
 Znajduje obiekt animacji, który zawiera zmienną określonego animacji.  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Wskaźnik do zmiennej animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu animacji lub wartość NULL, jeśli nie znaleziono obiektu animacji.  
  
##  <a name="getgroupid"></a>CAnimationGroup::GetGroupID  
 Zwraca identyfikator grupy.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator grupy.  
  
##  <a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions  
 Określa, jak wyczyścić przejścia z obiektów animacji, które należą do grupy. Jeśli ten element członkowski ma wartość PRAWDA, przejścia są usuwane automatycznie, gdy zaplanowano animacji. W przeciwnym razie należy ręcznie usunąć przejścia.  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects  
 Określa, jak można zniszczyć obiekty animacji. Jeśli ten parametr ma wartość TRUE, obiekty animacji zostanie automatycznie zniszczona, gdy grupa zostanie zniszczony. W przeciwnym razie animacji obiekty muszą zostać zniszczone ręcznie. Wartość domyślna to FALSE. Ta wartość TRUE tylko wtedy, gdy wszystkie obiekty animacji, które należą do grupy są dynamicznie przydzielane z nowy operator.  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes  
 Określa, jak można zniszczyć klatek. Jeśli ta wartość wynosi TRUE, wszystkich kluczowych są usuwane i zniszczone; w przeciwnym razie usuwane są tylko na liście. Wartość domyślna to TRUE.  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects  
 Zawiera listę obiektów animacji.  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames  
 Zawiera listę klatek.  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID  
 Unikatowy identyfikator grupy animacji.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController  
 Wskaźnik do kontrolera animacji, do której należy ta grupa.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard  
 Wskazuje scenorysu animacji. Ten wskaźnik jest prawidłowy tylko po wywołaniu na Animuj.  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes  
 Usuwa i opcjonalnie niszczy wszystkich kluczowych, które należą do grupy animacji.  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli m_bAutodestroyKeyframes element członkowski ma wartość PRAWDA, funkcja kluczowych są usuwane i niszczone, w przeciwnym razie kluczowych właśnie są usuwane z wewnętrzną listę klatek.  
  
##  <a name="removetransitions"></a>CAnimationGroup::RemoveTransitions  
 Usuwa przejścia z obiektów animacji, które należą do grupy animacji.  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli flaga m_bAutoclearTransitions jest ustawiona na wartość TRUE, ta metoda pętli wszystkich obiektów animacji, które należą do grupy i wywołuje CAnimationObject::ClearTransitions(FALSE).  
  
##  <a name="schedule"></a>CAnimationGroup::Schedule  
 Planuje animacji w określonym czasie.  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>Parametry  
 `pTimer`  
 Wskaźnik do czasomierza animacji.  
  
 `time`  
 Określa czas, aby zaplanować animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończy się pomyślnie; Wartość FALSE, jeśli metoda nie powiedzie się, czy animacja nie została wywołana z bScheduleNow ustawiony na wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można zaplanować animacji w określonym czasie. Animuj należy wywołać z bScheduleNow wartość FALSE.  
  
##  <a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions  
 Poleca się, że wszystkie obiekty animacji, które należą do grupy automatycznie zniszczyć przejścia.  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoDestroy`  
 Określa, jak można zniszczyć przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość FALSE, tylko wtedy, gdy przydzielić przejścia na stosie. Wartość domyślna to TRUE, w związku z tym zdecydowanie zaleca się przydzielić przy użyciu operatora nowe obiekty przejścia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
