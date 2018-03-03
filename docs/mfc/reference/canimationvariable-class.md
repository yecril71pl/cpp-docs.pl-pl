---
title: Klasa CAnimationVariable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a90db931ca53687c42263df6a4112eb478059227
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationvariable-class"></a>Klasa CAnimationVariable
Reprezentuje zmienną animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationVariable;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Tworzy obiekt zmiennej animacji.|  
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|Destruktor. Wywoływane, gdy obiekt CAnimationVariable jest niszczone.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](#addtransition)|Dodaje przejście.|  
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Dodaje przejścia z listy wewnętrznych do scenorysu.|  
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Czyści przejścia.|  
|[CAnimationVariable::Create](#create)|Tworzy obiekt źródłowy COM zmiennej animacji.|  
|[CAnimationVariable::CreateTransitions](#createtransitions)|Tworzy wszystkie przejścia, które ma zostać zastosowany do tej zmiennej animacji.|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Włącza lub wyłącza IntegerValueChanged zdarzeń.|  
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Włącza lub wyłącza ValueChanged zdarzeń.|  
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Zwraca wartość domyślną.|  
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Zwraca element nadrzędny obiekt animacji.|  
|[CAnimationVariable::GetValue](#getvalue)|Przeciążone. Zwraca bieżącą wartość zmiennej animacji.|  
|[CAnimationVariable::GetVariable](#getvariable)|Zwraca wskaźnik do obiektu IUIAnimationVariable COM.|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną i zwalnia obiektu IUIAnimationVariable COM.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Określa relację między zmienną animacji i obiektu animacji.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy mają zostać usunięte obiekty powiązane przejścia.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Określa wartość domyślną, która jest propagowana do IUIAnimationVariable.|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Zawiera listę przejścia Animacja tej zmiennej animacji.|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Wskaźnik do obiektu animacji, który hermetyzuje tej zmiennej animacji.|  
|[CAnimationVariable::m_variable](#m_variable)|Przechowuje wskaźnik do obiektu IUIAnimationVariable COM. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub tworzenie nie powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationVariable hermetyzuje obiektu IUIAnimationVariable COM. Przechowuje listę przejścia do zastosowania do zmiennej animacji w scenorysu. Obiekty CAnimationVariable są osadzone do obiektów animacji, które reprezentują w aplikacji animowany wartość, punkt, rozmiar, kolor i prostokąta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CAnimationVariable`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable  
 Destruktor. Wywoływane, gdy obiekt CAnimationVariable jest niszczone.  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="addtransition"></a>CAnimationVariable::AddTransition  
 Dodaje przejście.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pTransition`  
 Wskaźnik do przejścia do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, aby dodać przejście do wewnętrznej listy przejść do zastosowania do zmiennej animacji. Ta lista powinny zostać wyczyszczone, gdy zaplanowano animacji.  
  
##  <a name="applytransitions"></a>CAnimationVariable::ApplyTransitions  
 Dodaje przejścia z listy wewnętrznych do scenorysu.  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Wskaźnik do kontrolera elementu nadrzędnego animacji.  
  
 `pStoryboard`  
 Wskaźnik do scenorysu.  
  
 `bDependOnKeyframes`  
 Wartość TRUE, jeśli ta metoda należy dodać przejścia, które są zależne od kluczowych.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje przejścia z listy wewnętrznych do scenorysu. Jest ona wywoływana z kodu najwyższego poziomu kilka razy można dodać przejścia, które nie są zależne od kluczowych i Dodawanie przejść, które są zależne od kluczowych. Jeśli nie utworzono podstawowej zmiennej animacji obiektu COM, ta metoda tworzy na tym etapie.  
  
##  <a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable  
 Tworzy obiekt zmiennej animacji.  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Określa wartość domyślną.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy obiekt zmiennej animacji i ustawia wartość domyślną. Wartość domyślna jest używany, gdy zmienna nie jest animowany lub nie można animować.  
  
##  <a name="cleartransitions"></a>CAnimationVariable::ClearTransitions  
 Czyści przejścia.  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutodestroy`  
 Określa, czy ta metoda powinna usunąć przejścia obiektów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa wszystkie przejścia z wewnętrzną listę przejścia. Jeśli bAutodestroy ma wartość PRAWDA lub m_bAutodestroyTransitions ma wartość TRUE, przejścia są usuwane. W przeciwnym razie wywołujący powinien cofnięcie przydziału obiektów przejścia.  
  
##  <a name="create"></a>CAnimationVariable::Create  
 Tworzy obiekt źródłowy COM zmiennej animacji.  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>Parametry  
 `pManager`  
 Wskaźnik do Menedżera animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zmienna animacji został pomyślnie utworzony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje utworzenie podstawowej zmiennej animacji obiektu COM i ustawia wartość domyślną.  
  
##  <a name="createtransitions"></a>CAnimationVariable::CreateTransitions  
 Tworzy wszystkie przejścia, które ma zostać zastosowany do tej zmiennej animacji.  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
`pLibrary`  
 Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), który definiuje biblioteki standardowe przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejścia zostały utworzone pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy trzeba utworzyć przejścia, które zostały dodane do zmiennej na wewnętrznej liście przejścia.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent  
 Włącza lub wyłącza IntegerValueChanged zdarzeń.  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Wskaźnik do kontrolera elementu nadrzędnego.  
  
 `bEnable`  
 Wartość TRUE — Włączanie zdarzeń, FALSE - wyłącz zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu zdarzeń ValueChanged struktura wywołuje metody wirtualnej CAnimationController::OnAnimationIntegerValueChanged. Należy je zastąpić w klasy pochodzącej od CAnimationController, aby przetworzyć to zdarzenie. Ta metoda jest wywoływana za każdym razem, gdy zostanie zmieniona wartość całkowitą typu zmienną animacji.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent  
 Włącza lub wyłącza ValueChanged zdarzeń.  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `pController`  
 Wskaźnik do kontrolera elementu nadrzędnego.  
  
 `bEnable`  
 Wartość TRUE — Włączanie zdarzeń, FALSE - wyłącz zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu zdarzeń ValueChanged struktura wywołuje metody wirtualnej CAnimationController::OnAnimationValueChanged. Należy je zastąpić w klasy pochodzącej od CAnimationController, aby przetworzyć to zdarzenie. Ta metoda jest wywoływana za każdym razem, gdy zostanie zmieniona wartość zmiennej animacji.  
  
##  <a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue  
 Zwraca wartość domyślną.  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość domyślna.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do uzyskania wartości domyślnej zmiennej animacji. W konstruktorze lub metodą SetDefaultValue można ustawić wartości domyślnej.  
  
##  <a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject  
 Zwraca element nadrzędny obiekt animacji.  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu animacji nadrzędnego, jeśli zostało ustanowione relacji, w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać pobrać wskaźnika do obiektu nadrzędnego animacji (kontener).  
  
##  <a name="getvalue"></a>CAnimationVariable::GetValue  
 Zwraca bieżącą wartość zmiennej animacji.  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblValue`  
 Bieżąca wartość zmiennej animacji.  
  
 `nValue`  
 Bieżąca wartość zmiennej animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli wartość zostały pobrane pomyślnie, lub podstawowej zmiennej animacji nie został utworzony. W przeciwnym razie kod błędu HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać pobrać bieżącą wartość zmiennej animacji. Jeśli nie utworzono obiekt COM, dblValue będzie zawierać wartość domyślną, gdy funkcja zwraca wartość.  
  
##  <a name="getvariable"></a>CAnimationVariable::GetVariable  
 Zwraca wskaźnik do obiektu IUIAnimationVariable COM.  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do obiektu IUIAnimationVariable COM lub wartość NULL, jeśli zmienna animacji nie został utworzony, lub nie można utworzyć.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do dostępu do podstawowego obiektu IUIAnimationVariable COM i bezpośrednio wywołać metody w razie potrzeby.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions  
 Określa, czy mają zostać usunięte obiekty powiązane przejścia.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>Uwagi  
 Należy ustawić tę wartość na true, aby wymuszenia usunięcia obiektów przejścia, gdy są usuwane z wewnętrzną listę przejścia. Jeśli ta wartość wynosi FALSE przejścia należy usunąć wywołując aplikacji. Listy przejść zawsze są czyszczone po zaplanowano animacji. Wartość domyślna to FALSE.  
  
##  <a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue  
 Określa wartość domyślną, która jest propagowana do IUIAnimationVariable.  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions  
 Zawiera listę przejścia Animacja tej zmiennej animacji.  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject  
 Wskaźnik do obiektu animacji, który hermetyzuje tej zmiennej animacji.  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="m_variable"></a>CAnimationVariable::m_variable  
 Przechowuje wskaźnik do obiektu IUIAnimationVariable COM. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub tworzenie nie powiodło się.  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue  
 Ustawia wartość domyślną i zwalnia obiektu IUIAnimationVariable COM.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Określa nową wartość domyślną.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby zresetować wartość domyślną. Ta metoda zwalnia w związku z tym wewnętrznego obiektu IUIAnimationVariable COM, gdy zostaje odtworzone zmiennej animacji, obiekt COM pobiera nową wartością domyślną. Wartością domyślną jest zwracany przez GetValue, jeśli nie utworzono obiekt COM, reprezentujący zmiennej animacji lub zmienna ma nie animowany.  
  
##  <a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject  
 Określa relację między zmienną animacji i obiektu animacji.  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentObject`  
 Wskaźnik do obiektu animacji, który zawiera tę zmienną.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana wewnętrznie do ustanawiania relacji jeden do jednego między zmienną animacji i obiektu animacji, który hermetyzuje go.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
