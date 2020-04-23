---
title: Klasa CAnimationVariable
ms.date: 03/27/2019
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
ms.openlocfilehash: b53a1338566a329fbdf5b91c41d0411a529afe8d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755073"
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
|[CAnimationVariable::CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVari](#canimationvariable)|Konstruuje obiekt zmiennej animacji.|
|[CAnimationVariable::~CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable ::~CAnimationVariable CAnimationVar](#_dtorcanimationvariable)|Destruktor. Wywoływane, gdy CAnimationVariable obiekt jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::AddTransition CAnimationVariable::AddTransition CAnimationVariable::AddTransition CAni](#addtransition)|Dodaje przejście.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Dodaje przejścia z listy wewnętrznej do scenorysu.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Czyści przejścia.|
|[CAnimationVariable::Tworzenie](#create)|Tworzy podstawowy obiekt COM zmiennej animacji.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Tworzy wszystkie przejścia, które mają być zastosowane do tej zmiennej animacji.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Włącza lub wyłącza zdarzenie IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Włącza lub wyłącza valuechanged zdarzenia.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Zwraca wartość domyślną.|
|[CAnimationVariable::GetParentAnimationObject CAnimationVariable::GetParentAnimationObject CAnimationVariable::GetParentAnimationObject CAni](#getparentanimationobject)|Zwraca nadrzędny obiekt animacji.|
|[CAnimationVariable::GetValue](#getvalue)|Przeciążone. Zwraca bieżącą wartość zmiennej animacji.|
|[CAnimationVariable::GetVariable CAnimationVariable::GetVariable CAnimationVariable::GetVariable CAni](#getvariable)|Zwraca wskaźnik do IUIAnimationVariable COM obiektu.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną i zwalnia IUIAnimationVariable COM obiektu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject CAnimationVariable::SetParentAnimationObject CAnimationVariable::SetParentAnimationObject CAni](#setparentanimationobject)|Ustawia relację między zmienną animacji a obiektem animacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy powiązane obiekty przejścia mają zostać usunięte.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Określa wartość domyślną, która jest propagowana do funkcji IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Zawiera listę przejść, które animują tę zmienną animacji.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Wskaźnik do obiektu animacji, który hermetyzuje tę zmienną animacji.|
|[CAnimationVariable::m_variable](#m_variable)|Przechowuje wskaźnik do IUIAnimationVariable COM obiektu. NULL, jeśli obiekt COM nie został jeszcze utworzony lub jeśli tworzenie nie powiodło się.|

## <a name="remarks"></a>Uwagi

CAnimationVariable klasa hermetyzuje IUIAnimationVariable COM obiektu. Zawiera również listę przejść, które mają być stosowane do zmiennej animacji w scenorysu. CAnimationVariable obiekty są osadzone w obiektach animacji, które mogą reprezentować w aplikacji animowaną wartość, punkt, rozmiar, kolor i prostokąt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAnimationVariable`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable::~CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable ::~CAnimationVariable CAnimationVar

Destruktor. Wywoływane, gdy CAnimationVariable obiekt jest niszczony.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition CAnimationVariable::AddTransition CAnimationVariable::AddTransition CAni

Dodaje przejście.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition (tłumaczenie na pTransition)*<br/>
Wskaźnik do przejścia, aby dodać.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, aby dodać przejście do wewnętrznej listy przejść, które mają być stosowane do zmiennej animacji. Ta lista powinna zostać wyczyszczona po zaplanowaniu animacji.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyTransitions

Dodaje przejścia z listy wewnętrznej do scenorysu.

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pKontroler*<br/>
Wskaźnik do nadrzędnego kontrolera animacji.

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDependOnKeyframes*<br/>
PRAWDA, jeśli ta metoda powinna dodać przejścia, które zależą od klatek kluczowych.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje przejścia z listy wewnętrznej do scenorysu. Jest wywoływana z kodu najwyższego poziomu kilka razy, aby dodać przejścia, które nie zależą od klatek kluczowych i dodać przejścia, które zależą od klatek kluczowych. Jeśli podstawowa zmienna animacji COM obiekt nie został utworzony, ta metoda tworzy go na tym etapie.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVariable CAnimationVari

Konstruuje obiekt zmiennej animacji.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa wartość domyślną.

### <a name="remarks"></a>Uwagi

Konstruuje obiekt zmiennej animacji i ustawia jego wartość domyślną. Wartość domyślna jest używana, gdy zmienna nie jest animowana lub nie może być animowana.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Czyści przejścia.

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bUtodestroj*<br/>
Określa, czy ta metoda powinna usuwać obiekty przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie przejścia z wewnętrznej listy przejść. Jeśli bAutodestroy ma wartość PRAWDA lub m_bAutodestroyTransitions jest PRAWDA, przejścia są usuwane. W przeciwnym razie obiekt wywołujący powinien zdążaćlokalizowanie obiektów przejścia.

## <a name="canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Tworzenie

Tworzy podstawowy obiekt COM zmiennej animacji.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
Wskaźnik do menedżera animacji.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zmienna animacji została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy podstawowy obiekt COM zmiennej animacji i ustawia jego wartość domyślną.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::CreateTransitions

Tworzy wszystkie przejścia, które mają być zastosowane do tej zmiennej animacji.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pBrabrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę standardowych przejść.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejścia zostały utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy musi utworzyć przejścia, które zostały dodane do wewnętrznej listy przejść zmiennej.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Włącza lub wyłącza zdarzenie IntegerValueChanged.

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontroler*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bWłaszą*<br/>
PRAWDA - włącz zdarzenie, FALSE - wyłącz zdarzenie.

### <a name="remarks"></a>Uwagi

Gdy valueChanged zdarzenie jest włączone, struktura wywołuje metodę wirtualną CAnimationController::OnAnimationIntegerValueChanged. Należy zastąpić go w klasie pochodną CAnimationController w celu przetworzenia tego zdarzenia. Ta metoda jest wywoływana za każdym razem, gdy zmieniana jest wartość całkowita zmiennej animacji.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Włącza lub wyłącza valuechanged zdarzenia.

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontroler*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bWłaszą*<br/>
PRAWDA - włącz zdarzenie, FALSE - wyłącz zdarzenie.

### <a name="remarks"></a>Uwagi

Gdy valueChanged zdarzenie jest włączone, struktura wywołuje metodę wirtualną CAnimationController::OnAnimationValueChanged. Należy zastąpić go w klasie pochodną CAnimationController w celu przetworzenia tego zdarzenia. Ta metoda jest wywoływana za każdym razem, gdy wartość zmiennej animacji jest zmieniana.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue

Zwraca wartość domyślną.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość domyślna.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do uzyskiwania domyślnej wartości zmiennej animacji. Wartość domyślną można ustawić w konstruktorze lub przez Metodę SetDefaultValue.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject CAnimationVariable::GetParentAnimationObject CAnimationVariable::GetParentAnimationObject CAni

Zwraca nadrzędny obiekt animacji.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu animacji nadrzędnej, jeśli relacja została ustanowiona, w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, aby pobrać wskaźnik do obiektu animacji nadrzędnej (kontenera).

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::GetValue

Zwraca bieżącą wartość zmiennej animacji.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue (wartość dblValue)*<br/>
Bieżąca wartość zmiennej animacji.

*wartość nValue*<br/>
Bieżąca wartość zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

S_OK, czy wartość została uzyskana pomyślnie lub podstawowa zmienna animacji nie została utworzona. W przeciwnym razie kod błędu HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda może być wywołana, aby pobrać bieżącą wartość zmiennej animacji. Jeśli podstawowy obiekt COM nie został utworzony, dblValue będzie zawierać wartość domyślną, gdy funkcja zwraca.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable CAnimationVariable::GetVariable CAnimationVariable::GetVariable CAni

Zwraca wskaźnik do IUIAnimationVariable COM obiektu.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do IUIAnimationVariable COM obiektu lub NULL, jeśli zmienna animacji nie został utworzony lub nie można utworzyć.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do uzyskiwania dostępu do podstawowej IUIAnimationVariable COM obiektu i wywołać jego metody bezpośrednio w razie potrzeby.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions

Określa, czy powiązane obiekty przejścia mają zostać usunięte.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Uwagi

Ustaw tę wartość na WARTOŚĆ TRUE, aby wymusić usunięcie obiektów przejściowych, gdy są one usuwane z wewnętrznej listy przejść. Jeśli ta wartość jest FALSE przejścia powinny zostać usunięte przez wywołanie aplikacji. Lista przejść jest zawsze czyszczona po zaplanowaniu animacji. Wartością domyślną jest FAŁSZ.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue

Określa wartość domyślną, która jest propagowana do funkcji IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions

Zawiera listę przejść, które animują tę zmienną animacji.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject

Wskaźnik do obiektu animacji, który hermetyzuje tę zmienną animacji.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>CAnimationVariable::m_variable

Przechowuje wskaźnik do IUIAnimationVariable COM obiektu. NULL, jeśli obiekt COM nie został jeszcze utworzony lub jeśli tworzenie nie powiodło się.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue

Ustawia wartość domyślną i zwalnia IUIAnimationVariable COM obiektu.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa nową wartość domyślną.

### <a name="remarks"></a>Uwagi

Ta metoda służy do resetowania wartości domyślnej. Ta metoda zwalnia wewnętrzny IUIAnimationVariable COM obiektu, w związku z tym, gdy zmienna animacji jest odtworzona, podstawowy obiekt COM pobiera nową wartość domyślną. Wartość domyślna jest zwracana przez GetValue, jeśli obiekt COM reprezentujący zmienną animacji nie został utworzony lub jeśli zmienna nie została animowana.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject CAnimationVariable::SetParentAnimationObject CAnimationVariable::SetParentAnimationObject CAni

Ustawia relację między zmienną animacji a obiektem animacji.

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Wskaźnik do obiektu animacji zawierającego tę zmienną.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana wewnętrznie, aby ustanowić relację jeden-do-jednego między zmienną animacji a obiektem animacji, który ją hermetyzuje.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
