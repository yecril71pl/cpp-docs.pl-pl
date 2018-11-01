---
title: Klasa CAnimationVariable
ms.date: 11/04/2016
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
ms.openlocfilehash: 1ad14060c7607698cd647ae34fb35b6ea3ae547c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559565"
---
# <a name="canimationvariable-class"></a>Klasa CAnimationVariable

Przedstawia zmienną animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationVariable;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Konstruuje obiekt zmiennej animacji.|
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt CAnimationVariable.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Dodaje przejścia.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Dodaje przejścia z wewnętrznej listy do scenorysu.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Czyści przejścia.|
|[CAnimationVariable::Create](#create)|Tworzy obiekt źródłowy COM zmiennej animacji.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Tworzy wszystkie przejścia, które mają być stosowane do tej zmiennej animacji.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Włącza lub wyłącza zdarzeń IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Włącza lub wyłącza zdarzeń ValueChanged.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Zwraca wartość domyślną.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Zwraca element nadrzędny obiektu animacji.|
|[CAnimationVariable::GetValue](#getvalue)|Przeciążone. Zwraca bieżącą wartość zmiennej animacji.|
|[CAnimationVariable::GetVariable](#getvariable)|Zwraca wskaźnik do obiektu IUIAnimationVariable COM.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Ustawia domyślną wartość i zwalnia obiektu IUIAnimationVariable COM.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Określa relację między zmienną animacji i obiektu animacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy należy usunąć obiekty powiązane przejścia.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Określa domyślną wartość, która jest propagowana do IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Zawiera listę przejść, które animować tej zmiennej animacji.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Wskaźnik do obiektu animacji, który hermetyzuje tej zmiennej animacji.|
|[CAnimationVariable::m_variable](#m_variable)|Przechowuje wskaźnik do obiektu IUIAnimationVariable COM. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub tworzenie nie powiodło się.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationVariable hermetyzuje obiektu IUIAnimationVariable COM. Przechowuje listę przejścia, które ma zostać zastosowany do zmiennej animacji w scenorysu. CAnimationVariable obiekty osadzone zostaną do obiektów w animacji, które mogą reprezentować w aplikacji jest animowany wartość, punkt, rozmiar, kolor i prostokąt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAnimationVariable`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>  CAnimationVariable:: ~ CAnimationVariable

Destruktor. Wywołuje się, kiedy niszczony jest obiekt CAnimationVariable.

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>  CAnimationVariable::AddTransition

Dodaje przejścia.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Wskaźnik do przejścia do dodania.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana, aby dodać przejście do wewnętrznej listy przejścia, które ma zostać zastosowany do zmiennej animacji. Ta lista powinny zostać wyczyszczone, gdy zaplanowano animacji.

##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions

Dodaje przejścia z wewnętrznej listy do scenorysu.

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera animacji elementu nadrzędnego.

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDependOnKeyframes*<br/>
Wartość TRUE, jeśli tej metody należy dodać przejść, które są zależne od ramek kluczowych.

### <a name="remarks"></a>Uwagi

Metoda ta umożliwia dodanie przejścia z wewnętrznej listy do scenorysu. Jest wywoływana z kodu najwyższego poziomu kilka razy do dodania przejścia, które nie są zależne od klatki kluczowe i Dodaj przejść, które są zależne od ramek kluczowych. Jeśli nie utworzono bazowego zmiennej animacji obiekt COM, ta metoda tworzy na tym etapie.

##  <a name="canimationvariable"></a>  CAnimationVariable::CAnimationVariable

Konstruuje obiekt zmiennej animacji.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa domyślną wartość.

### <a name="remarks"></a>Uwagi

Konstruuje obiekt zmiennej animacji i ustawia jego wartość domyślną. Wartość domyślna jest używany, gdy zmienna nie jest animowany lub nie mogą być animowane.

##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions

Czyści przejścia.

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Określa, czy ta metoda powinna usunąć obiekty przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie przejścia z listy wewnętrznych przejść. Jeśli bAutodestroy ma wartość TRUE lub m_bAutodestroyTransitions ma wartość TRUE, przejścia są usuwane. W przeciwnym razie obiekt wywołujący powinien cofnięcie przydziału obiektów przejścia.

##  <a name="create"></a>  CAnimationVariable::Create

Tworzy obiekt źródłowy COM zmiennej animacji.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
Wskaźnik do Menedżera animacji.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie utworzono zmienną animacji; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy podstawowy zmiennej animacji obiektu COM i ustawia jego wartość domyślną.

##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions

Tworzy wszystkie przejścia, które mają być stosowane do tej zmiennej animacji.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejścia standardowe.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie; utworzono przejścia w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy potrzebuje, aby przejść, które zostały dodane do zmiennej wewnętrznej listy przejścia.

##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent

Włącza lub wyłącza zdarzeń IntegerValueChanged.

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera elementu nadrzędnego.

*bWłączenie*<br/>
Wartość TRUE — Włącz zdarzenia FALSE - wyłącz zdarzenia systemu.

### <a name="remarks"></a>Uwagi

Po włączeniu zdarzeń ValueChanged struktura wywołuje metodę wirtualną CAnimationController::OnAnimationIntegerValueChanged. Należy zastąpić go w klasę pochodną CAnimationController, aby przetworzyć tego zdarzenia. Ta metoda jest wywoływana za każdym razem, gdy zmiany liczby całkowitej wartość zmiennej animacji.

##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent

Włącza lub wyłącza zdarzeń ValueChanged.

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera elementu nadrzędnego.

*bWłączenie*<br/>
Wartość TRUE — Włącz zdarzenia FALSE - wyłącz zdarzenia systemu.

### <a name="remarks"></a>Uwagi

Po włączeniu zdarzeń ValueChanged struktura wywołuje metodę wirtualną CAnimationController::OnAnimationValueChanged. Należy zastąpić go w klasę pochodną CAnimationController, aby przetworzyć tego zdarzenia. Ta metoda jest wywoływana za każdym razem, gdy wartość zmiennej animacji zostanie zmieniona.

##  <a name="getdefaultvalue"></a>  CAnimationVariable::GetDefaultValue

Zwraca wartość domyślną.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość domyślna.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia uzyskanie domyślna wartość zmiennej animacji. W konstruktorze lub metodą SetDefaultValue można ustawić wartość domyślną.

##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject

Zwraca element nadrzędny obiektu animacji.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu animacji nadrzędnego, jeśli relacja zostało nawiązane, w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać można pobrać wskaźnik do obiektu nadrzędnego animacji (kontenera).

##  <a name="getvalue"></a>  CAnimationVariable::GetValue

Zwraca bieżącą wartość zmiennej animacji.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue*<br/>
Bieżąca wartość zmiennej animacji.

*nWartość:*<br/>
Bieżąca wartość zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

S_OK wartości zostały pobrane pomyślnie, czy podstawowy zmiennej animacji nie została utworzona. W przeciwnym razie kod błędu HRESULT.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać można pobrać bieżącą wartość zmiennej animacji. Jeśli nie utworzono obiekt COM, dblValue będzie zawierać wartość domyślną, gdy funkcja zwraca.

##  <a name="getvariable"></a>  CAnimationVariable::GetVariable

Zwraca wskaźnik do obiektu IUIAnimationVariable COM.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Wartość zwracana

Nieprawidłowy wskaźnik do obiektu IUIAnimationVariable COM lub wartość NULL, jeśli zmiennej animacji nie został utworzony lub nie można utworzyć.

### <a name="remarks"></a>Uwagi

Dostęp do bazowego obiektu IUIAnimationVariable COM i bezpośrednio wywołać jego metody, jeśli to konieczne, należy użyć tej funkcji.

##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions

Określa, czy należy usunąć obiekty powiązane przejścia.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Uwagi

Ustaw tę wartość na wartość true, Wymuś usunięcie przejścia obiektów, gdy są usuwane z listy wewnętrznych przejść. Jeśli ta wartość wynosi FALSE przejścia powinny być usuwane przez wywołanie aplikacji. Listy przejść zawsze jest czyszczona po zaplanowaniu animacji. Wartość domyślna to FALSE.

##  <a name="m_dbldefaultvalue"></a>  CAnimationVariable::m_dblDefaultValue

Określa domyślną wartość, która jest propagowana do IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions

Zawiera listę przejść, które animować tej zmiennej animacji.

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject

Wskaźnik do obiektu animacji, który hermetyzuje tej zmiennej animacji.

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>  CAnimationVariable::m_variable

Przechowuje wskaźnik do obiektu IUIAnimationVariable COM. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub tworzenie nie powiodło się.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>  CAnimationVariable::SetDefaultValue

Ustawia domyślną wartość i zwalnia obiektu IUIAnimationVariable COM.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa nową wartość domyślną.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia Zresetuj wartość domyślną. Ta metoda zwalnia w związku z tym obiekt wewnętrzny IUIAnimationVariable COM, gdy zmienna animacji są odtwarzane, obiekt COM pobiera nową wartością domyślną. Wartością domyślną jest zwracany przez GetValue, jeśli nie utworzono obiekt COM, reprezentujący zmiennej animacji lub jeśli zmienna nie została animowany.

##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject

Określa relację między zmienną animacji i obiektu animacji.

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Wskaźnik do obiektu animacji, który zawiera tę zmienną.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana wewnętrznie do ustanawiania relacji jeden do jednego między zmienną animacji i obiektu animacji, który hermetyzuje go.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
