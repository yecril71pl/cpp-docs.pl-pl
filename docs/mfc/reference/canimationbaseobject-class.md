---
title: Klasa CAnimationBaseObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs: C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b1fb434158d263b57fb34d15d976d9bae41c4df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="canimationbaseobject-class"></a>Klasa CAnimationBaseObject
Klasa podstawowa dla wszystkich obiektów animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Przeciążone. Tworzy obiekt animacji.|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|Destruktor. Wywoływane, gdy trwa niszczenie obiektu animacji.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Dodaje przejścia do scenorysu ze zmienną hermetyzowany animacji.|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Usuwa wszystkie powiązane przejścia.|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Określa, czy obiekt animacji zawiera zmienną określonego animacji.|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Tworzy przejścia skojarzona z obiektem animacji.|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Odłącza obiektu animacji na podstawie kontrolera animacji elementu nadrzędnego.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Ustawia całkowitą wartość zmieniona obsługi zdarzeń.|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Ustawia wartość zmieniona z obsługi zdarzeń.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Informuje, czy przejście pokrewne zostaną zniszczone automatycznie.|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Zwraca identyfikator bieżącej grupy.|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Zwraca identyfikator bieżącego obiektu.|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|Zwraca dane zdefiniowane przez użytkownika.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Ustawia flagę, która porządkuje automatycznie zniszczenie przejścia.|  
|[CAnimationBaseObject::SetID](#setid)|Ustawia nowych identyfikatorów.|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|Zestawy danych zdefiniowane przez użytkownika.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Zbiera wskaźników do zmiennych zawartych w niej animacji.|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Ustanawia relację między zmienne animacji, znajdujących się w obiekcie animacji i ich kontenera.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy powiązany przejścia należy zniszczyć automatycznie.|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Magazyny danych zdefiniowane przez użytkownika.|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Określa identyfikator grupy obiektu animacji.|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Określa identyfikator obiektu animacji.|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Wskaźnik do kontrolera elementu nadrzędnego animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa implementuje podstawowe metody dla wszystkich obiektów animacji. Obiektu animacji można reprezentują wartości, punkt, rozmiar, prostokąta lub kolor w aplikacji, a także wszelkie niestandardowe jednostki. Obiekty animacji są przechowywane w grupach animacji (zobacz CAnimationGroup). Każda grupa można animować oddzielnie i mogą być traktowane jako analogowy scenorysu. Obiektu animacji hermetyzuje co najmniej jeden animacji zmienne (zobacz CAnimationVariable), w zależności od jego logiczna reprezentacja. Na przykład CAnimationRect zawiera cztery zmienne animacji — jedną zmienną z każdej strony prostokąta. Każda klasa obiektu animacji przedstawia przeciążonej metody AddTransition, który powinien być używany do stosowania przejścia do zmiennych hermetyzowany animacji. Obiektu animacji mogą zostać zidentyfikowane przez identyfikator obiektu (opcjonalnie) i identyfikatora grupy. Identyfikator grupy jest niezbędne, aby umieścić obiekt animacji do prawidłowej grupy, ale jeśli nie określono Identyfikatora grupy, obiekt znajduje się w domyślnej grupie o identyfikatorze 0. Jeśli wywołujesz identyfikator zestawu z różnych GroupID obiektu animacji zostanie przeniesiony do innej grupy (Nowa grupa jest tworzony, jeśli to konieczne).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject:: ~ CAnimationBaseObject  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektu animacji.  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions  
 Dodaje przejścia do scenorysu ze zmienną hermetyzowany animacji.  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
 `bDependOnKeyframes`  
 O wartości FAŁSZ tej metody dodaje tylko przejścia, które nie są zależne od kluczowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejścia zostały pomyślnie dodane.  
  
### <a name="remarks"></a>Uwagi  
 Dodaje pokrewne przejścia, które zostały dodane z AddTransition (przeciążonych metod w klasach pochodnych), do scenorysu.  
  
##  <a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject  
 Tworzy obiekt animacji.  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `nObjectID`  
 Określa identyfikator obiektu.  
  
 `dwUserData`  
 Zdefiniowane przez użytkownika danych, który może być skojarzony z obiektem animacji i później pobrana w czasie wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy obiekty animacji i przypisuje domyślny identyfikator obiektu (0) i identyfikator grupy: (0).  
  
##  <a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions  
 Usuwa wszystkie powiązane przejścia.  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutodestroy`  
 Określa, czy automatycznie zniszczyć przejścia obiektów lub po prostu usuń je z listy.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie powiązane przejścia i niszczy ich, jeśli flaga bAutodestroy lub m_bAutodestroyTransitions ma wartość TRUE. Przejścia należy zniszczyć automatycznie tylko wtedy, gdy nie są przydzielane na stosie. Jeśli powyższe flagi mają wartość FAŁSZ, przejścia właśnie są usuwane z wewnętrzną listę powiązanych przejścia.  
  
##  <a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable  
 Określa, czy obiekt animacji zawiera zmienną określonego animacji.  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Wskaźnik do zmiennej animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zmienna animacji jest zawarte w obiekcie animacji; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda może służyć do określenia, czy zmienna animacji określony przez pVariable znajduje się w obrębie obiektu animacji. Obiektu animacji, w zależności od jego typu, może zawierać kilku zmiennych animacji. Na przykład CAnimationColor zawiera trzy zmienne, jedną dla każdego składnika kolorów (czerwony, zielonemu i niebieskiemu). Po zmianie wartości zmiennej animacji, interfejsu API systemu Windows animacji wysyła zdarzenia ValueChanged lub IntegerValueChanged (jeśli jest włączona) i parametr to zdarzenie jest wskaźnik do interfejsu IUIAnimationVariable zmiennej animacji. Tej metody pomaga uzyskać wskaźnik do animacji ze wskaźnika do obiektu COM zawartych w niej.  
  
##  <a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions  
 Tworzy przejścia skojarzona z obiektem animacji.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejścia zostały utworzone pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Pętli listę zmiennych animacji hermetyzowany w obiekcie pochodnej animacji i tworzy przejścia skojarzone z każdej zmiennej animacji.  
  
##  <a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController  
 Odłącza obiektu animacji na podstawie kontrolera animacji elementu nadrzędnego.  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana wewnętrznie.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent  
 Ustawia całkowitą wartość zmieniona obsługi zdarzeń.  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Wskaźnik do kontrolera elementu nadrzędnego.  
  
 `bEnable`  
 Określa, czy włączyć lub wyłączyć zdarzeń zmieniona wartość całkowitą.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu obsługi zdarzeń zmieniona wartość całkowitą może obsłużyć tego zdarzenia w metodzie CAnimationController::OnAnimationIntegerValueChanged, która powinna zostać przesłonięta w klasie pochodnej CAnimationController. Ta metoda jest wywoływana w każdym zmienił wartość całkowita animacji.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent  
 Ustawia wartość zmieniona z obsługi zdarzeń.  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Wskaźnik do kontrolera elementu nadrzędnego.  
  
 `bEnable`  
 Określa, czy włączyć lub wyłączyć zmieniona wartość zdarzeń.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu obsługi zdarzeń zmieniona wartość może obsłużyć tego zdarzenia w metodzie CAnimationController::OnAnimationValueChanged, która powinna zostać przesłonięta w klasie pochodnej CAnimationController. Ta metoda jest wywoływana za każdym razem, gdy zmieniono wartość animacji.  
  
##  <a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList  
 Zbiera wskaźników do zmiennych zawartych w niej animacji.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Lista musi być wypełniona ze zmiennymi animacji zawartych w obiekcie animacji.  
  
### <a name="remarks"></a>Uwagi  
 Jest to czysty metody wirtualnej, który musi zostać zastąpiony w klasie pochodnej. Obiektu animacji, w zależności od jego typu zawiera co najmniej jedną zmienną animacji. Na przykład CAnimationPoint zawiera dwie zmienne dla współrzędne X i Y odpowiednio. Klasa podstawowa CAnimationBaseObject implementuje niektórych metod ogólnych, które działają na listę zmiennych animacji: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Te metody wywołania GetAnimationVariableList, który jest wypełniony w klasie pochodnej zmienne rzeczywiste animacji zawartych w obiekcie określonej animacji, a następnie zapętlić na liście i wykonać odpowiednie działania. W przypadku utworzenia obiektu animacji niestandardowej, należy dodać do lst wszystkie zmienne animacji zawarte w tym obiekcie.  
  
##  <a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions  
 Informuje, czy przejście pokrewne zostaną zniszczone automatycznie.  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli PRAWDA, przejścia pokrewne zostaną zniszczone automatycznie; w przypadku wartości FAŁSZ przejścia obiektów należy alokację wywołując aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta flaga ma wartość TRUE. Ustawienia tej flagi tylko wtedy, gdy są przydzielone przejścia na stosie i/lub aplikacja wywołująca powinien można cofnąć przydziału przejścia.  
  
##  <a name="getgroupid"></a>CAnimationBaseObject::GetGroupID  
 Zwraca identyfikator bieżącej grupy.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator bieżącej grupy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do pobrania identyfikatora grupy. Jeśli identyfikator grupy nie został ustawiony jawnie w konstruktorze lub identyfikator zestawu tego 0.  
  
##  <a name="getobjectid"></a>CAnimationBaseObject::GetObjectID  
 Zwraca identyfikator bieżącego obiektu.  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator bieżącego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do pobrania identyfikatora obiektu. Jeśli identyfikator obiektu nie została ustawiona jawnie w konstruktorze lub identyfikator zestawu tego 0.  
  
##  <a name="getuserdata"></a>CAnimationBaseObject::GetUserData  
 Zwraca dane zdefiniowane przez użytkownika.  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość danych niestandardowych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można pobrać niestandardowych danych w czasie wykonywania. Zwrócona wartość będzie równa 0, jeśli nie został on jawnie zainicjowany w konstruktorze lub SetUserData.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions  
 Określa, czy powiązany przejścia należy zniszczyć automatycznie.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData  
 Magazyny danych zdefiniowane przez użytkownika.  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID  
 Określa identyfikator grupy obiektu animacji.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID  
 Określa identyfikator obiektu animacji.  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController  
 Wskaźnik do kontrolera elementu nadrzędnego animacji.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions  
 Ustawia flagę, która porządkuje automatycznie zniszczenie przejścia.  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>Parametry  
 `bValue`  
 Określa flagi zniszczyć automatycznie.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia tej flagi tylko wtedy, gdy przydzielony przy użyciu operatora nowe obiekty przejścia. Jeśli z jakiegoś powodu przydzielania przejścia obiektów na stosie zniszczyć automatycznie Flaga powinna być wartość FALSE. Domyślnie ta flaga ma wartość TRUE.  
  
##  <a name="setid"></a>CAnimationBaseObject::SetID  
 Ustawia nowych identyfikatorów.  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nObjectID`  
 Określa identyfikator nowego obiektu.  
  
 `nGroupID`  
 Określa identyfikator nowej grupy.  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia zmianę Identyfikatora obiektu i identyfikatora grupy. Jeśli nowy identyfikator grupy różni się od bieżącego Identyfikatora, obiekt animacji zostanie przeniesiony do innej grupy (Nowa grupa zostanie utworzony, w razie potrzeby).  
  
##  <a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects  
 Ustanawia relację między zmienne animacji, znajdujących się w obiekcie animacji i ich kontenera.  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>Uwagi  
 Jest to pomocnika, który może służyć do ustanawiania relacji między zmienne animacji, znajdujących się w obiekcie animacji i ich kontenera. On pętli zmienne animacji i ustawia wskaźnik wstecz do obiektu nadrzędnego animacji do każdej zmiennej animacji. W bieżącej implementacji nawiązuje wzajemnych relacji w CAnimationBaseObject::ApplyTransitions w związku z tym wstecz wskaźniki nie są ustawione do czasu wywołania CAnimationGroup::Animate. Znajomość relacji mogą być pomocne podczas możesz przetwarzania zdarzeń i trzeba uzyskać animacji nadrzędnego obiektu z CAnimationVariable (Użyj CAnimationVariable::GetParentAnimationObject).  
  
##  <a name="setuserdata"></a>CAnimationBaseObject::SetUserData  
 Zestawy danych zdefiniowane przez użytkownika.  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>Parametry  
 `dwUserData`  
 Określa dane niestandardowe.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia kojarzenie danych niestandardowych z obiektu animacji. Te dane mogą zostać odzyskane w czasie wykonywania przez funkcji GetUserData.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
