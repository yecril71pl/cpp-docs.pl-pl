---
title: Klasa CAnimationBaseObject
ms.date: 11/04/2016
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
ms.openlocfilehash: 6527abf5c91cf440bbbe76d0d5fe49ce2c5dbef7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430449"
---
# <a name="canimationbaseobject-class"></a>Klasa CAnimationBaseObject

Klasa bazowa dla wszystkich obiektów w animacji.

## <a name="syntax"></a>Składnia

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Przeciążone. Konstruuje obiekt animacji.|
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|Destruktor. Wywołuje się, kiedy niszczony jest obiekt animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Dodaje przejścia do scenorysu, za pomocą zmiennej zhermetyzowany animacji.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Usuwa wszystkie powiązane przejścia.|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Określa, czy obiekt animacji zawiera zmienną określonego animacji.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Tworzy przejścia skojarzona z obiektem animacji.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Odłącza obiektu animacji z kontrolera animacji elementu nadrzędnego.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Konfiguruje zmienić wartości liczby całkowitej programu obsługi zdarzeń.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Ustawia wartość zmienić program obsługi zdarzeń.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Informuje, czy przejście powiązane są niszczone, automatycznie.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Zwraca bieżący identyfikator grupy.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Zwraca identyfikator bieżącego obiektu.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Zwraca dane zdefiniowane przez użytkownika.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Ustawia flagę, która porządkuje automatycznie zniszczyć przejścia.|
|[CAnimationBaseObject::SetID](#setid)|Ustawia nowych identyfikatorów.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Zestawy danych zdefiniowane przez użytkownika.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Zbiera wskaźniki do zmiennych zawartej animacji.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Ustanawia relację między zmienne animacji, zawarte w obiektu animacji oraz ich kontenerów.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy powiązane przejścia należy zniszczyć automatycznie.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Przechowuje dane użytkownika.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Określa identyfikator grupy obiektu animacji.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Określa identyfikator obiektu animacji.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Wskaźnik do kontrolera elementu nadrzędnego animacji.|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje podstawowe metody dla wszystkich obiektów w animacji. Obiekt animacji można reprezentować wartość, punkt, rozmiar, prostokąta lub koloru w aplikacji, a także wszystkie jednostki niestandardowe. Obiektów w animacji są przechowywane w grupach animacji (patrz CAnimationGroup). Każda grupa mogą być animowane oddzielnie i mogą być traktowane jako analogowy scenorysu. Animacja hermetyzuje jedną lub więcej animacji zmiennych (zobacz CAnimationVariable), w zależności od jego reprezentację w postaci logicznej. Na przykład CAnimationRect zawiera cztery zmienne animacji — jedną zmienną dla każdego rogu prostokąta. Każda klasa obiektu animacji udostępnia przeciążona metoda AddTransition, który powinien być używany do zastosowania przejścia do zmiennych zhermetyzowany animacji. Obiekt animacji można zidentyfikować przez identyfikator obiektu (opcjonalnie) i identyfikatora grupy. Identyfikator grupy jest niezbędne, aby umieścić obiekt animacji do prawidłowej grupy, ale jeśli nie zostanie określony identyfikator grupy, obiekt jest umieszczany w domyślnej grupie o identyfikatorze 0. Jeśli wywołasz identyfikator zestawu przy użyciu innego identyfikatora grupy, obiekt animacji zostanie przeniesiony do innej grupy (Nowa grupa jest tworzony, jeśli to konieczne).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject

Destruktor. Wywołuje się, kiedy niszczony jest obiekt animacji.

```
virtual ~CAnimationBaseObject();
```

##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions

Dodaje przejścia do scenorysu, za pomocą zmiennej zhermetyzowany animacji.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDependOnKeyframes*<br/>
O wartości FAŁSZ metoda ta umożliwia dodanie tych przejść, które nie są zależne od ramek kluczowych.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli przejścia zostały pomyślnie dodane.

### <a name="remarks"></a>Uwagi

Dodaje powiązane przejścia, które zostały dodane za pomocą AddTransition (przeciążonych metod w klasach pochodnych), do scenorysu.

##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject

Konstruuje obiekt animacji.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Danych zdefiniowane przez użytkownika, który może być skojarzony z obiektem animacji i później pobrana w czasie wykonywania.

### <a name="remarks"></a>Uwagi

Tworzy obiektów w animacji i przypisuje domyślny identyfikator obiektu (0) i identyfikator grupy: (0).

##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions

Usuwa wszystkie powiązane przejścia.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bAutodestroy*<br/>
Określa, czy należy automatycznie niszczy obiektów przejścia lub po prostu usunąć je z listy.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie powiązane przejścia i niszczy takie obiekty, jeśli flaga bAutodestroy lub m_bAutodestroyTransitions ma wartość TRUE. Przejścia należy zniszczyć automatycznie tylko wtedy, gdy nie są przydzielane na stosie. Jeśli powyższe flagi mają wartość FAŁSZ, przejścia po prostu są usuwane z wewnętrzną listę powiązanych przejścia.

##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable

Określa, czy obiekt animacji zawiera zmienną określonego animacji.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pVariable*<br/>
Wskaźnik do zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zmienna animacji znajduje się w obiekcie animacji; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do określenia, czy zmienną animacji, określony przez pVariable znajduje się w obrębie obiektu animacji. Obiekt Animacja w zależności od jego typu, może zawierać wiele zmiennych animacji. Na przykład CAnimationColor zawiera trzy zmienne, jedną dla każdego składnika koloru (czerwony, zielony i niebieski). Gdy wartość zmiennej animacji została zmieniona, interfejs API animacji Windows wysyła zdarzenia ValueChanged lub IntegerValueChanged (jeśli jest włączona) i parametr to zdarzenie jest wskaźnik do interfejsu IUIAnimationVariable zmiennej animacji. Ta metoda ułatwia uzyskiwanie wskaźnika do animacji ze wskaźnika do zawartego w nim obiektu COM.

##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions

Tworzy przejścia skojarzona z obiektem animacji.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie; utworzono przejścia w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Pętli listę zmiennych animacji hermetyzowane w obiekcie pochodnej animacji i tworzy przejścia skojarzone z każdej zmiennej animacji.

##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController

Odłącza obiektu animacji z kontrolera animacji elementu nadrzędnego.

```
void DetachFromController();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest używana wewnętrznie.

##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent

Konfiguruje zmienić wartości liczby całkowitej programu obsługi zdarzeń.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera elementu nadrzędnego.

*bWłączenie*<br/>
Określa, czy włączyć lub wyłączyć zdarzenia zmienić wartości liczby całkowitej.

### <a name="remarks"></a>Uwagi

Jeśli program obsługi zdarzeń zmienić wartości liczby całkowitej jest włączona, może obsługiwać to zdarzenie w metodzie CAnimationController::OnAnimationIntegerValueChanged, która powinna zostać przesłonięta w klasie pochodnej CAnimationController. Ta metoda jest wywoływana za każdym razem, gdy zmieniono wartość całkowitą animacji.

##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent

Ustawia wartość zmienić program obsługi zdarzeń.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pController*<br/>
Wskaźnik do kontrolera elementu nadrzędnego.

*bWłączenie*<br/>
Określa, czy włączyć lub wyłączyć zdarzenia zmienić wartości.

### <a name="remarks"></a>Uwagi

Jeśli program obsługi zdarzeń zmienić wartości jest włączona, może obsługiwać to zdarzenie w metodzie CAnimationController::OnAnimationValueChanged, która powinna zostać przesłonięta w klasie pochodnej CAnimationController. Ta metoda jest wywoływana za każdym razem, gdy zmieniono wartość animacji.

##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList

Zbiera wskaźniki do zmiennych zawartej animacji.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst) = 0;
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
Lista, które należy podać ze zmiennymi animacji w obiekcie animacji.

### <a name="remarks"></a>Uwagi

Jest to czysty metodę wirtualną, która musi zostać zastąpiona w klasie pochodnej. Obiekt Animacja w zależności od jego typu, zawiera co najmniej jednej zmiennej animacji. Na przykład CAnimationPoint zawiera dwie zmienne dla współrzędne X i Y odpowiednio. Klasa bazowa CAnimationBaseObject implementuje kilka metod ogólnych, które działają na listę zmiennych animacji: ApplyTransitions ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Te metody wywołania GetAnimationVariableList, która jest wypełniona w klasie pochodnej zmiennych rzeczywistych animacji zawarte w obiekcie określonym animacji, a następnie pętli listy i wykonać odpowiednie działania. Jeśli tworzysz obiekt animacji niestandardowej, należy dodać do dzieł wszystkie zmienne animacji zawarte w tym obiekcie.

##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions

Informuje, czy przejście powiązane są niszczone, automatycznie.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Wartość zwracana

W przypadku opcji TRUE przejścia powiązane są niszczone, automatycznie. w przypadku wartości FAŁSZ obiektów przejścia należy cofnięta przez wywołanie aplikacji.

### <a name="remarks"></a>Uwagi

Domyślnie ta flaga ma wartość TRUE. Tylko wtedy, gdy przydzielone przejścia na stosie i/lub przejścia należy cofnąć przydział przez aplikacji wywołującej, należy ustawić tę flagę.

##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID

Zwraca bieżący identyfikator grupy.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator bieżącej grupy.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania identyfikatora grupy. Jeśli identyfikator grupy nie zostało ustawione jawnie w konstruktorze lub za pomocą identyfikator zestawu, przez 0.

##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID

Zwraca identyfikator bieżącego obiektu.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania identyfikatora obiektu. Jeśli identyfikator obiektu nie zostało ustawione jawnie w konstruktorze lub za pomocą identyfikator zestawu, przez 0.

##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData

Zwraca dane zdefiniowane przez użytkownika.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość danych niestandardowych.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu pobrania danych niestandardowych w czasie wykonywania. Zwrócona wartość będzie równa 0, jeśli go nie została jawnie zainicjowana w konstruktorze lub SetUserData.

##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions

Określa, czy powiązane przejścia należy zniszczyć automatycznie.

```
BOOL m_bAutodestroyTransitions;
```

##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData

Przechowuje dane użytkownika.

```
DWORD m_dwUserData;
```

##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID

Określa identyfikator grupy obiektu animacji.

```
UINT32 m_nGroupID;
```

##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID

Określa identyfikator obiektu animacji.

```
UINT32 m_nObjectID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController

Wskaźnik do kontrolera elementu nadrzędnego animacji.

```
CAnimationController* m_pParentController;
```

##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions

Ustawia flagę, która porządkuje automatycznie zniszczyć przejścia.

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parametry

*bDane wartości*<br/>
Określa, automatycznego niszczenia flagi.

### <a name="remarks"></a>Uwagi

Tylko wtedy, gdy przydzielone obiekty przejścia za pomocą nowego operatora, należy ustawić tę flagę. Jeśli powodu przejścia obiekty są przydzielane na stosie, automatycznego niszczenia Flaga powinna być wartość FALSE. Domyślnie ta flaga ma wartość TRUE.

##  <a name="setid"></a>  CAnimationBaseObject::SetID

Ustawia nowych identyfikatorów.

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parametry

*nObjectID*<br/>
Określa identyfikator nowego obiektu.

*nGroupID*<br/>
Określa identyfikator nowej grupy.

### <a name="remarks"></a>Uwagi

Umożliwia zmianę Identyfikatora obiektu i identyfikatora grupy. Jeśli nowy identyfikator grupy jest inny niż bieżący identyfikator, obiekt Animacja zostanie przeniesiony do innej grupy (Nowa grupa zostanie utworzony, jeśli to konieczne).

##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects

Ustanawia relację między zmienne animacji, zawarte w obiektu animacji oraz ich kontenerów.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Uwagi

Jest to dysk pomocnika, który może służyć do ustanawiania relacji między zmienne animacji, zawarte w obiektu animacji oraz ich kontenerów. Działa za pośrednictwem zmiennych animacji w pętli i ustawia wskaźnik wstecz do obiektu nadrzędnego animacji do każdej zmiennej animacji. W bieżącej implementacji, które rzeczywistego relacji jest określana w CAnimationBaseObject::ApplyTransitions w związku z tym wskaźniki Wstecz nie są ustawione, dopóki nie wywołasz CAnimationGroup::Animate. Poznanie zależności mogą być przydatne, gdy pozwala na rozpoczęcie przetwarzania zdarzeń i musisz pobrać animacji nadrzędnego obiektu z CAnimationVariable (Użyj CAnimationVariable::GetParentAnimationObject).

##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData

Zestawy danych zdefiniowane przez użytkownika.

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
Określa dane niestandardowe.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia kojarzenie danych niestandardowych z obiektu animacji. Te dane mogą zostać odzyskane w czasie wykonywania przez funkcji GetUserData.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
