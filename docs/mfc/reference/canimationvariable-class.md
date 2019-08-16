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
ms.openlocfilehash: b6767ed42d66aff467ef36bd2a7b5234ad181ced
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507541"
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
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Konstruuje obiekt zmiennej animacji.|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|Destruktor. Wywołuje się, gdy obiekt CAnimationVariable jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable:: AddTransition](#addtransition)|Dodaje przejście.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Dodaje przejścia z listy wewnętrznej do scenorysu.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Czyści przejścia.|
|[CAnimationVariable:: Create](#create)|Tworzy obiekt COM zmiennej animacji bazowej.|
|[CAnimationVariable:: settransitions](#createtransitions)|Tworzy wszystkie przejścia, które mają zostać zastosowane do tej zmiennej animacji.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Włącza lub wyłącza zdarzenie IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Włącza lub wyłącza zdarzenie ValueChanged.|
|[CAnimationVariable:: getdefaultvalue](#getdefaultvalue)|Zwraca wartość domyślną.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Zwraca obiekt animacji nadrzędnej.|
|[CAnimationVariable:: GetValue](#getvalue)|Przeciążone. Zwraca bieżącą wartość zmiennej animacji.|
|[CAnimationVariable:: getvariable](#getvariable)|Zwraca wskaźnik do obiektu COM IUIAnimationVariable.|
|[CAnimationVariable:: SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną i zwalnia obiekt COM IUIAnimationVariable.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Ustawia relację między zmienną animacji a obiektem animacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy powiązane obiekty przejścia mają być usuwane.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Określa wartość domyślną, która jest przekazywana do IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Zawiera listę przejść, które animują tę zmienną animacji.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Wskaźnik do obiektu animacji, który hermetyzuje tę zmienną animacji.|
|[CAnimationVariable::m_variable](#m_variable)|Przechowuje wskaźnik do obiektu COM IUIAnimationVariable. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub jeśli Tworzenie nie powiodło się.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationVariable hermetyzuje obiekt COM IUIAnimationVariable. Zawiera również listę przejść, które mają zostać zastosowane do zmiennej animacji w scenorysie. Obiekty CAnimationVariable są osadzone w obiektach animacji, które mogą reprezentować w aplikacji animowaną wartość, punkt, rozmiar, kolor i prostokąt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CAnimationVariable`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller. h

##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable

Destruktor. Wywołuje się, gdy obiekt CAnimationVariable jest niszczony.

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>CAnimationVariable:: AddTransition

Dodaje przejście.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Wskaźnik do przejścia do dodania.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana w celu dodania przejścia do wewnętrznej listy przejść, które mają zostać zastosowane do zmiennej animacji. Ta lista powinna zostać wyczyszczona po zaplanowaniu animacji.

##  <a name="applytransitions"></a>CAnimationVariable::ApplyTransitions

Dodaje przejścia z listy wewnętrznej do scenorysu.

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do nadrzędnego kontrolera animacji.

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDependOnKeyframes*<br/>
PRAWDA, jeśli ta metoda powinna dodawać przejścia, które są zależne od klatek kluczowych.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje przejścia z listy wewnętrznej do scenorysu. Jest on wywoływany z kodu najwyższego poziomu kilka razy, aby dodać przejścia, które nie zależą od klatek kluczowych i Dodaj przejścia, które zależą od klatek kluczowych. Jeśli obiekt COM zmiennej animacji bazowej nie został utworzony, ta metoda tworzy ją na tym etapie.

##  <a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable

Konstruuje obiekt zmiennej animacji.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa wartość domyślną.

### <a name="remarks"></a>Uwagi

Konstruuje obiekt zmiennej animacji i ustawia jego wartość domyślną. Wartość domyślna jest używana, gdy zmienna nie jest animowana lub nie można jej animować.

##  <a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Czyści przejścia.

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Określa, czy ta metoda powinna usuwać obiekty przejścia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa wszystkie przejścia z wewnętrznej listy przejść. Jeśli bAutodestroy ma wartość TRUE lub m_bAutodestroyTransitions ma wartość TRUE, przejścia są usuwane. W przeciwnym razie obiekt wywołujący powinien cofnąć alokację obiektów przejścia.

##  <a name="create"></a>CAnimationVariable:: Create

Tworzy obiekt COM zmiennej animacji bazowej.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parametry

*pManager*<br/>
Wskaźnik do Menedżera animacji.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli zmienna animacji została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy obiekt COM zmiennej animacji i ustawia jego wartość domyślną.

##  <a name="createtransitions"></a>CAnimationVariable:: settransitions

Tworzy wszystkie przejścia, które mają zostać zastosowane do tej zmiennej animacji.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parametry

*pLibrary*<br/>
Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejść standardowych.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pomyślnie utworzono przejścia; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy musi utworzyć przejścia, które zostały dodane do wewnętrznej listy przejść zmiennej.

##  <a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Włącza lub wyłącza zdarzenie IntegerValueChanged.

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bEnable*<br/>
TRUE — włączenie zdarzenia, FAŁSZ — wyłączenie zdarzenia.

### <a name="remarks"></a>Uwagi

Po włączeniu zdarzenia ValueChanged Framework wywołuje metodę wirtualną CAnimationController:: OnAnimationIntegerValueChanged. Aby przetworzyć to zdarzenie, należy przesłonić go w klasie pochodzącej od CAnimationController. Ta metoda jest wywoływana za każdym razem, gdy zostanie zmieniona wartość całkowita zmiennej animacji.

##  <a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Włącza lub wyłącza zdarzenie ValueChanged.

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bEnable*<br/>
TRUE — włączenie zdarzenia, FAŁSZ — wyłączenie zdarzenia.

### <a name="remarks"></a>Uwagi

Po włączeniu zdarzenia ValueChanged Framework wywołuje metodę wirtualną CAnimationController:: OnAnimationValueChanged. Aby przetworzyć to zdarzenie, należy przesłonić go w klasie pochodzącej od CAnimationController. Ta metoda jest wywoływana za każdym razem, gdy wartość zmiennej animacji jest zmieniana.

##  <a name="getdefaultvalue"></a>CAnimationVariable:: getdefaultvalue

Zwraca wartość domyślną.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość domyślna.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby uzyskać wartość domyślną zmiennej animacji. Wartość domyślną można ustawić w konstruktorze lub przez metodę SetDefaultValue.

##  <a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject

Zwraca obiekt animacji nadrzędnej.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu animacji nadrzędnej, jeśli relacja została ustanowiona, w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, aby pobrać wskaźnik do nadrzędnego obiektu animacji (kontenera).

##  <a name="getvalue"></a>CAnimationVariable:: GetValue

Zwraca bieżącą wartość zmiennej animacji.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue*<br/>
Bieżąca wartość zmiennej animacji.

*nWartość*<br/>
Bieżąca wartość zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

S_OK Jeśli wartość została pomyślna, lub zmienna animacji bazowa nie została utworzona. Kod błędu HRESULT w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda może zostać wywołana w celu pobrania bieżącej wartości zmiennej animacji. Jeśli źródłowy obiekt COM nie został utworzony, dblValue będzie zawierać wartość domyślną, gdy funkcja zwraca.

##  <a name="getvariable"></a>CAnimationVariable:: getvariable

Zwraca wskaźnik do obiektu COM IUIAnimationVariable.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik do obiektu COM IUIAnimationVariable lub wartość NULL, jeśli zmienna animacji nie została utworzona lub nie można jej utworzyć.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby uzyskać dostęp do bazowego obiektu COM IUIAnimationVariable i wywoływać metody bezpośrednio, w razie potrzeby.

##  <a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions

Określa, czy powiązane obiekty przejścia mają być usuwane.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Uwagi

Ustaw tę wartość na TRUE, aby wymusić usunięcie obiektów przejścia, gdy są usuwane z wewnętrznej listy przejść. Jeśli ta wartość jest FAŁSZYWa, przejścia powinny zostać usunięte przez wywołanie aplikacji. Lista przejść jest zawsze czyszczona po zaplanowaniu animacji. Wartość domyślna to FALSE.

##  <a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue

Określa wartość domyślną, która jest przekazywana do IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions

Zawiera listę przejść, które animują tę zmienną animacji.

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject

Wskaźnik do obiektu animacji, który hermetyzuje tę zmienną animacji.

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>CAnimationVariable::m_variable

Przechowuje wskaźnik do obiektu COM IUIAnimationVariable. Wartość NULL, jeśli obiekt COM nie został jeszcze utworzony lub jeśli Tworzenie nie powiodło się.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>CAnimationVariable:: SetDefaultValue

Ustawia wartość domyślną i zwalnia obiekt COM IUIAnimationVariable.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa nową wartość domyślną.

### <a name="remarks"></a>Uwagi

Użyj tej metody do zresetowania wartości domyślnej. Ta metoda zwalnia wewnętrzny obiekt COM IUIAnimationVariable, dlatego gdy zmienna animacji zostanie odtworzona, źródłowy obiekt COM pobiera nową wartość domyślną. Wartość domyślna jest zwracana przez GetValue, jeśli obiekt COM reprezentujący zmienną animacji nie został utworzony lub jeśli zmienna nie została animowana.

##  <a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject

Ustawia relację między zmienną animacji a obiektem animacji.

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parametry

*pParentObject*<br/>
Wskaźnik do obiektu animacji, który zawiera tę zmienną.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana wewnętrznie w celu ustanowienia relacji jeden-do-jednego między zmienną animacji a obiektem animacji, który hermetyzuje go.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
