---
title: Klasa CAnimationBaseObject
ms.date: 03/27/2019
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
ms.openlocfilehash: 9581ea142c6f87ae12665374a483abc00763ad97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371120"
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
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Przeciążone. Konstruuje obiekt animacji.|
|[CAnimationBaseObject::~CAnimationBaseObject](#_dtorcanimationbaseobject)|Destruktor. Wywoływane, gdy obiekt animacji jest niszczony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Dodaje przejścia do scenorysu ze zmienną animacji zhermetyzowaną.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Usuwa wszystkie powiązane przejścia.|
|[CAnimationBaseObject::ZawieraWarzylna](#containsvariable)|Określa, czy obiekt animacji zawiera określoną zmienną animacji.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Tworzy przejścia skojarzone z obiektem animacji.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Odłącza obiekt animacji od nadrzędnego kontrolera animacji.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Konfiguruje program obsługi zdarzeń Zmieniona wartość całkowita.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Konfiguruje program obsługi zdarzeń Zmieniona wartością.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Określa, czy powiązane przejście jest niszczone automatycznie.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Zwraca bieżący identyfikator grupy.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Zwraca bieżący identyfikator obiektu.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Zwraca dane zdefiniowane przez użytkownika.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Ustawia flagę, aby automatycznie niszczyć przejścia.|
|[CAnimationBaseObject::SetID](#setid)|Ustawia nowe identyfikatory.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Ustawia dane zdefiniowane przez użytkownika.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Zbiera wskaźniki do zawartych zmiennych animacji.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Ustanawia relację między zmiennymi animacji, zawarte w obiekcie animacji i ich kontenera.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Określa, czy powiązane przejścia powinny być automatycznie niszczone.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Przechowuje dane zdefiniowane przez użytkownika.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Określa identyfikator grupy obiektu animacji.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Określa identyfikator obiektu animacji.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Wskaźnik do nadrzędnego kontrolera animacji.|

## <a name="remarks"></a>Uwagi

Ta klasa implementuje podstawowe metody dla wszystkich obiektów animacji. Obiekt animacji może reprezentować wartość, punkt, rozmiar, prostokąt lub kolor w aplikacji, a także dowolną encję niestandardową. Obiekty animacji są przechowywane w grupach animacji (zobacz CAnimationGroup). Każda grupa może być animowana oddzielnie i może być traktowana jako analog scenorysu. Obiekt animacji hermetyzuje jedną lub więcej zmiennych animacji (patrz CAnimationVariable), w zależności od jego reprezentacji logicznej. Na przykład CAnimationRect zawiera cztery zmienne animacji - jedna zmienna dla każdej strony prostokąta. Każda klasa obiektu animacji udostępnia przeciążone AddTransition metody, które powinny być używane do stosowania przejść do zhermetyzowanych zmiennych animacji. Obiekt animacji można zidentyfikować za pomocą identyfikatora obiektu (opcjonalnie) i identyfikatora grupy. Identyfikator grupy jest niezbędny do umieszczenia obiektu animacji w celu skorygowania grupy, ale jeśli nie określono identyfikatora grupy, obiekt jest umieszczany w grupie domyślnej o identyfikatorze 0. Jeśli wywołasz SetID z innym identyfikatorem grupy, obiekt animacji zostanie przeniesiony do innej grupy (w razie potrzeby zostanie utworzona nowa grupa).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject::~CAnimationBaseObject

Destruktor. Wywoływane, gdy obiekt animacji jest niszczony.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions

Dodaje przejścia do scenorysu ze zmienną animacji zhermetyzowaną.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parametry

*pStoryboard*<br/>
Wskaźnik do scenorysu.

*bDependOnKeyframes*<br/>
Gdy FALSE, ta metoda dodaje tylko te przejścia, które nie zależą od klatek kluczowych.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejścia zostały dodane pomyślnie.

### <a name="remarks"></a>Uwagi

Dodaje powiązane przejścia, które zostały dodane z AddTransition (przeciążone metody w klasach pochodnych), do scenorysu.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Konstruuje obiekt animacji.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Dane zdefiniowane przez użytkownika, które mogą być skojarzone z obiektem animacji i pobierane później w czasie wykonywania.

### <a name="remarks"></a>Uwagi

Konstruuje obiekty animacji i przypisuje domyślny identyfikator obiektu (0) i identyfikator grupy (0).

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions

Usuwa wszystkie powiązane przejścia.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parametry

*bUtodestroj*<br/>
Określa, czy obiekty przejścia mają być automatycznie niszczone, czy po prostu usuwać je z listy pokrewnych.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie powiązane przejścia i niszczy je, jeśli bAutodestroy lub m_bAutodestroyTransitions flaga jest PRAWDA. Przejścia powinny być niszczone automatycznie tylko wtedy, gdy nie są przydzielane na stosie. Jeśli powyższe flagi są FALSE, przejścia są po prostu usuwane z wewnętrznej listy powiązanych przejść.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>CAnimationBaseObject::ZawieraWarzylna

Określa, czy obiekt animacji zawiera określoną zmienną animacji.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parametry

*pWarienne*<br/>
Wskaźnik do zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zmienna animacji znajduje się w obiekcie animacji; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda może służyć do określenia, czy zmienna animacji określona przez pVariable jest zawarta w obiekcie animacji. Obiekt animacji, w zależności od jego typu, może zawierać kilka zmiennych animacji. Na przykład CAnimationColor zawiera trzy zmienne, po jednej dla każdego składnika koloru (czerwony, zielony i niebieski). Po zmianie wartości zmiennej animacji interfejs API animacji systemu Windows wysyła zdarzenia ValueChanged lub IntegerValueChanged (jeśli jest włączona), a parametr tego zdarzenia jest wskaźnikiem do interfejsu IUIAnimationVariable zmiennej animacji. Ta metoda pomaga uzyskać wskaźnik do animacji ze wskaźnika do zawartego obiektu COM.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions

Tworzy przejścia skojarzone z obiektem animacji.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przejścia zostały utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Pętle nad listą zmiennych animacji hermetyzowanych w pochodnym obiekcie animacji i tworzy przejścia skojarzone z każdą zmienną animacji.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController

Odłącza obiekt animacji od nadrzędnego kontrolera animacji.

```
void DetachFromController();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest używana wewnętrznie.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent

Konfiguruje program obsługi zdarzeń Zmieniona wartość całkowita.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontroler*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bWłaszą*<br/>
Określa, czy włączyć lub wyłączyć zdarzenie Zmiana wartości całkowitej.

### <a name="remarks"></a>Uwagi

Jeśli program obsługi zdarzeń Zmieniona wartość całkowita jest włączona, można obsługiwać to zdarzenie w CAnimationController::OnAnimationIntegerValueChanged metody, które powinny być zastąpione w CAnimationController pochodną klasy. Ta metoda jest wywoływana za każdym razem, gdy wartość całkowita animacji została zmieniona.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent

Konfiguruje program obsługi zdarzeń Zmieniona wartością.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*pKontroler*<br/>
Wskaźnik do kontrolera nadrzędnego.

*bWłaszą*<br/>
Określa, czy włączyć lub wyłączyć zdarzenie Zmiana wartości.

### <a name="remarks"></a>Uwagi

Jeśli program obsługi zdarzeń Zmiana wartości jest włączona, można obsługiwać to zdarzenie w CAnimationController::OnAnimationValueChanged metody, które powinny zostać zastąpione w CAnimationController pochodne klasy. Ta metoda jest wywoływana za każdym razem, gdy wartość animacji została zmieniona.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList

Zbiera wskaźniki do zawartych zmiennych animacji.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Parametry

*list*<br/>
Lista, która musi być wypełniona zmiennymi animacji zawartymi w obiekcie animacji.

### <a name="remarks"></a>Uwagi

Ta czysta metoda wirtualna musi zostać zastąpiona w klasie pochodnej. Obiekt animacji, w zależności od jego typu, zawiera jedną lub więcej zmiennych animacji. Na przykład CAnimationPoint zawiera dwie zmienne, dla współrzędnych X i Y odpowiednio. Klasa podstawowa CAnimationBaseObject implementuje niektóre metody ogólne, które działają na liście zmiennych animacji: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Metody te wywołanie GetAnimationVariableList, który jest wypełniony w klasie pochodnej z rzeczywistych zmiennych animacji zawartych w określonym obiekcie animacji, a następnie pętli na liście i wykonać niezbędne akcje. W przypadku tworzenia obiektu animacji niestandardowej należy dodać do *listy* wszystkie zmienne animacji zawarte w tym obiekcie.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions

Określa, czy powiązane przejście jest niszczone automatycznie.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli TRUE, powiązane przejścia są niszczone automatycznie; jeśli FALSE, obiekty przejścia powinny być cofnięte alokacji przez wywołanie aplikacji.

### <a name="remarks"></a>Uwagi

Domyślnie ta flaga ma wartość PRAWDA. Ustaw tę flagę tylko wtedy, gdy przydzielone przejście na stosie i/lub przejścia powinny być cofnięte przez aplikację wywołującą.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>CAnimationBaseObject::GetGroupID

Zwraca bieżący identyfikator grupy.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący identyfikator grupy.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania identyfikatora grupy. Jest 0, jeśli identyfikator grupy nie został jawnie ustawiony w konstruktorze lub setid.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>CAnimationBaseObject::GetObjectID

Zwraca bieżący identyfikator obiektu.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący identyfikator obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do pobierania identyfikatora obiektu. Jest 0, jeśli identyfikator obiektu nie został ustawiony jawnie w konstruktorze lub setid.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>CAnimationBaseObject::GetUserData

Zwraca dane zdefiniowane przez użytkownika.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość danych niestandardowych.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać dane niestandardowe w czasie wykonywania. Zwracana wartość będzie 0, jeśli nie został jawnie zainicjowany w konstruktorze lub setuserdata.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions

Określa, czy powiązane przejścia powinny być automatycznie niszczone.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData

Przechowuje dane zdefiniowane przez użytkownika.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID

Określa identyfikator grupy obiektu animacji.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID

Określa identyfikator obiektu animacji.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController

Wskaźnik do nadrzędnego kontrolera animacji.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions

Ustawia flagę, aby automatycznie niszczyć przejścia.

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parametry

*bWartość*<br/>
Określa flagę automatycznego niszczenia.

### <a name="remarks"></a>Uwagi

Ustaw tę flagę tylko wtedy, gdy obiekty przejścia zostały przydzielone przy użyciu operatora new. Jeśli z jakiegoś powodu obiekty przejścia są przydzielane na stosie, flaga automatycznego niszczenia powinna być FAŁSZEM. Domyślnie ta flaga ma wartość PRAWDA.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>CAnimationBaseObject::SetID

Ustawia nowe identyfikatory.

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parametry

*nObjectID*<br/>
Określa nowy identyfikator obiektu.

*nGrupaID*<br/>
Określa nowy identyfikator grupy.

### <a name="remarks"></a>Uwagi

Umożliwia zmianę identyfikatora obiektu i identyfikatora grupy. Jeśli nowy identyfikator grupy różni się od bieżącego identyfikatora, obiekt animacji zostanie przeniesiony do innej grupy (w razie potrzeby zostanie utworzona nowa grupa).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects

Ustanawia relację między zmiennymi animacji, zawarte w obiekcie animacji i ich kontenera.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Uwagi

Ten pomocnik może służyć do ustanowienia relacji między zmiennymi animacji zawartych w obiekcie animacji i ich kontenera. Zapętla się przez zmienne animacji i ustawia wskaźnik wstecz do obiektu animacji nadrzędnej do każdej zmiennej animacji. W bieżącej implementacji rzeczywista relacja jest ustanawiana w CAnimationBaseObject::ApplyTransitions, w związku z tym wskaźniki wstecz nie są ustawione, dopóki nie zostanie wywołana CAnimationGroup::Animate. Znając relację może być pomocne podczas przetwarzania zdarzeń i trzeba uzyskać obiekt animacji nadrzędnej z CAnimationVariable. Użyj CAnimationVariable::GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>CAnimationBaseObject::SetUserData

Ustawia dane zdefiniowane przez użytkownika.

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parametry

*dwUserData*<br/>
Określa dane niestandardowe.

### <a name="remarks"></a>Uwagi

Ta metoda służy do kojarzenia danych niestandardowych z obiektem animacji. Te dane mogą być pobierane później w czasie wykonywania przez GetUserData.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
