---
title: Klasa CBaseTransition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
dev_langs:
- C++
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db69941b0ee0f2267185604318d240d107604177
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cbasetransition-class"></a>Klasa CBaseTransition
Reprezentuje przejście podstawowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CBaseTransition : public CObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-enumerations"></a>Wyliczenia publiczny  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION_TYPE — wyliczenie](#transition_type_enumeration)|Określa typy przejścia są obecnie obsługiwane przez MFC implementacji interfejsu API systemu Windows animacji.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|Tworzy obiekt transtion podstawowej.|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|Destruktor. Wywoływane, gdy trwa niszczenie obiektów przejścia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Dodaje przejście do scenorysu.|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Dodaje przejście do scenorysu.|  
|[CBaseTransition::Clear](#clear)|Wersje hermetyzowany obiektu IUIAnimationTransition COM.|  
|[CBaseTransition::Create](#create)|Tworzy przejście COM.|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Zwraca uruchomić kluczową.|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Zwraca wskaźnik do zmiennej pokrewne.|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Zwraca uruchomić kluczową.|  
|[CBaseTransition::GetTransition](#gettransition)|Przeciążone. Zwraca wskaźnik do obiektu źródłowego przejścia COM.|  
|[CBaseTransition::GetType](#gettype)|Zwraca wartość typu przejścia.|  
|[CBaseTransition::IsAdded](#isadded)|Informuje, czy przejście został dodany do scenorysu.|  
|[CBaseTransition::SetKeyframes](#setkeyframes)|Ustawia kluczowych przejścia.|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Ustanawia relację między zmiennej animacji i przejść.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|Określa, czy przejście został dodany do scenorysu.|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Przechowuje wskaźnik do klatki kluczowej, który określa koniec przejścia.|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Wskaźnik do zmiennej animacji, która jest animowany z przejściem przechowywane w m_transition.|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Przechowuje wskaźnik do klatki kluczowej, który określa początek przejścia.|  
|[CBaseTransition::m_transition](#m_transition)|Przechowuje wskaźnik do IUIAnimationTransition. Wartość NULL, jeśli nie został utworzony obiekt COM przejścia.|  
|[CBaseTransition::m_type](#m_type)|Przechowuje typ przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa hermetyzuje IUIAnimationTransition interfejs i służy jako klasa podstawowa dla wszystkich przejść.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseTransition`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="_dtorcbasetransition"></a>  CBaseTransition:: ~ CBaseTransition  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektów przejścia.  
  
```  
virtual ~CBaseTransition();
```  
  
##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard  
 Dodaje przejście do scenorysu.  
  
```  
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do scenorysu, którego będzie animować pokrewne zmiennej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście zostało pomyślnie dodane do scenorysu.  
  
### <a name="remarks"></a>Uwagi  
 Stosuje przejścia do powiązanych zmiennej w scenorysu. Jeśli jest to pierwszy przejścia zastosowane do tej zmiennej w tym scenorysu, przejście rozpoczyna się od początku scenorysu. W przeciwnym wypadku przejścia jest dołączany do przejścia ostatnio dodany do zmiennej.  
  
##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes  
 Dodaje przejście do scenorysu.  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Wskaźnik do scenorysu, którego będzie animować pokrewne zmiennej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście zostało pomyślnie dodane do scenorysu.  
  
### <a name="remarks"></a>Uwagi  
 Stosuje przejścia do powiązanych zmiennej w scenorysu. Jeśli określono klatki kluczowej start, przejście rozpoczyna się od tego klatki kluczowej. Jeśli określono klatki kluczowej zakończenia, przejście zaczyna się od klatki kluczowej start i i zatrzymuje się na klatkę zakończenia. Jeśli przejście został utworzony z określonym parametrem czas trwania, ten czas trwania jest zastępowany czas między początkową i końcową klatek. Jeśli nie określono żadnych klatki kluczowej, przejście jest dołączany do przejścia ostatnio dodany do zmiennej.  
  
##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition  
 Tworzy obiekt transtion podstawowej.  
  
```  
CBaseTransition();
```  
  
##  <a name="clear"></a>  CBaseTransition::Clear  
 Wersje hermetyzowany obiektu IUIAnimationTransition COM.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę należy wywoływać z metody tworzenia klasy pochodnej, aby zapobiec przeciek interfejsu IUITransition.  
  
##  <a name="create"></a>  CBaseTransition::Create  
 Tworzy przejście COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Wskaźnik do przejścia biblioteki, która tworzy standardowe przejścia. Może to być wartość NULL dla niestandardowych przejść.  
  
 `pFactory`  
 Wskaźnik do przejścia factory, które tworzy niestandardowe przejścia. Może to być wartość NULL dla przejścia standardowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście obiektu modelu COM został pomyślnie utworzony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Jest to czystej funkcji wirtualnej musi zostać zastąpiony w klasie pochodnej. Jest ona wywoływana przez platformę, by utworzyć wystąpienia obiektu źródłowego przejścia COM.  
  
##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe  
 Zwraca uruchomić kluczową.  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do klatki kluczowej, lub wartość NULL, jeśli przejście nie powinny zostać wstawione między klatek.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można uzyskać dostępu do obiektu klatki kluczowej, która wcześniej została ustawiona przez SetKeyframes. Jest ona wywoływana przez kod najwyższego poziomu podczas przejścia są dodawane do scenorysu.  
  
##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable  
 Zwraca wskaźnik do zmiennej pokrewne.  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do zmiennej animacji lub wartość NULL, jeśli nie została ustawiona zmienna animacji przez SetRelatedVariable.  
  
### <a name="remarks"></a>Uwagi  
 Jest to metoda dostępu do zmiennej pokrewne animacji.  
  
##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe  
 Zwraca uruchomić kluczową.  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do kluczową lub wartość NULL, jeśli przejście nie mogą rozpoczynać się od kluczową.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można uzyskać dostępu do obiektu klatki kluczowej, która wcześniej została ustawiona przez SetKeyframes. Jest ona wywoływana przez kod najwyższego poziomu podczas przejścia są dodawane do scenorysu.  
  
##  <a name="gettransition"></a>  CBaseTransition::GetTransition  
 Zwraca wskaźnik do obiektu źródłowego przejścia COM.  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Wskaźnik do przejścia biblioteki, która tworzy standardowe przejścia. Może to być wartość NULL dla niestandardowych przejść.  
  
 `pFactory`  
 Wskaźnik do przejścia factory, które tworzy niestandardowe przejścia. Może to być wartość NULL dla przejścia standardowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nie można utworzyć prawidłowego wskaźnika IUIAnimationTransition lub wartość NULL, jeśli podstawowy przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wskaźnik do obiektu źródłowego przejścia COM i tworzy go, jeśli to konieczne.  
  
##  <a name="gettype"></a>  CBaseTransition::GetType  
 Zwraca wartość typu przejścia.  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden z TRANSITION_TYPE wyliczyć wartości.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można zidentyfikować obiekt przejście przez jego typu. Typ jest ustawiany w Konstruktorze w klasie pochodnej.  
  
##  <a name="isadded"></a>  CBaseTransition::IsAdded  
 Informuje, czy przejście został dodany do scenorysu.  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli przejście został dodany do scenorysu, w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta flaga jest ustawiona wewnętrznie, gdy kod najwyższego poziomu dodaje przejścia do scenorysu.  
  
##  <a name="m_badded"></a>  CBaseTransition::m_bAdded  
 Określa, czy przejście został dodany do scenorysu.  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe  
 Przechowuje wskaźnik do klatki kluczowej, który określa koniec przejścia.  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable  
 Wskaźnik do zmiennej animacji, która jest animowany z przejściem przechowywane w m_transition.  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe  
 Przechowuje wskaźnik do klatki kluczowej, który określa początek przejścia.  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>  CBaseTransition::m_transition  
 Przechowuje wskaźnik do IUIAnimationTransition. Wartość NULL, jeśli nie został utworzony obiekt COM przejścia.  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>  CBaseTransition::m_type  
 Przechowuje typ przejścia.  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>  CBaseTransition::SetKeyframes  
 Ustawia kluczowych przejścia.  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pStart`  
 Kluczową Określa początek przejścia.  
  
 `pEnd`  
 Kluczową Określa koniec przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda określa, że przejście do uruchamiania po określonej klatki kluczowej i, opcjonalnie, jeśli ustawienia nie ma wartości NULL, Zakończ przed określonym klatki kluczowej. Jeśli przejście został utworzony z określonym parametrem czas trwania, ten czas trwania jest zastępowany czas między początkową i końcową klatek.  
  
##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable  
 Ustanawia relację między zmiennej animacji i przejść.  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Wskaźnik do zmiennej pokrewne animacji.  
  
### <a name="remarks"></a>Uwagi  
 Ustanawia relację między zmiennej animacji i przejść. Przejście może odnosić się tylko do jednej zmiennej.  
  
##  <a name="transition_type_enumeration"></a>  CBaseTransition::TRANSITION_TYPE — wyliczenie  
 Określa typy przejścia są obecnie obsługiwane przez MFC implementacji interfejsu API systemu Windows animacji.  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ przejścia jest ustawiona w Konstruktorze określonych przejścia. Na przykład CSinusoidalTransitionFromRange ustawia jego typ SINUSOIDAL_FROM_RANGE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
