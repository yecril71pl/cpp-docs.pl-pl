---
title: Klasa CAnimationPoint
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: fcdd07efb46c97d27a9f1349c297688b5705f176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755142"
---
# <a name="canimationpoint-class"></a>Klasa CAnimationPoint

Implementuje funkcjonalność punktu, którego współrzędne mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Przeciążone. Konstruuje obiekt CAnimationPoint.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Dodaje przejścia dla współrzędnych X i Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne współrzędnych X i Y.|
|[CAnimationPoint::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationPoint::GetX](#getx)|Zapewnia dostęp do CAnimationVariable dla współrzędnych X.|
|[CAnimationPoint::GetY](#gety)|Zapewnia dostęp do CAnimationVariable dla współrzędnych Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zhermetyzowane zmienne animacji na liście. (Zastępuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Konwertuje CAnimationPoint do CPoint.|
|[CAnimationPoint::operator=](#operator_eq)|Przypisuje ptSrc do CAnimationPoint.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Zhermetyzowana zmienna animacji reprezentująca współrzędną X punktu animacji.|
|[CAnimationPoint::m_yValue](#m_yvalue)|Zhermetyzowana zmienna animacji reprezentująca współrzędną Y punktu animacji.|

## <a name="remarks"></a>Uwagi

CAnimationPoint Klasa hermetyzuje dwa CAnimationVariable obiektów i może reprezentować w aplikacjach punkt. Na przykład można użyć tej klasy do animowania pozycji dowolnego obiektu na ekranie (np. ciągu tekstowego, okręgu, punktu itp.). Aby użyć tej klasy w aplikacji, wystarczy utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być stosowane do współrzędnych X i/lub Y.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>CAnimationPoint::AddTransition

Dodaje przejścia dla współrzędnych X i Y.

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parametry

*pXTransition (tłumaczenie str.)*<br/>
Wskaźnik do przejścia dla współrzędnych X.

*pYTransition (Tłumaczenie) pY*<br/>
Wskaźnik do przejścia dla współrzędnej Y.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać określone przejścia do wewnętrznej listy przejść, które mają być stosowane do zmiennych animacji dla współrzędnych X i Y. Po dodaniu przejść nie są one stosowane natychmiast i przechowywane na liście wewnętrznej. Przejścia są stosowane (dodawane do serii ujęć dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednej z współrzędnych, można przekazać NULL.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint

Konstruuje obiekt CAnimationPoint.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*ptDefault (niem.*<br/>
Określa domyślne współrzędne punktów.

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Konstruuje obiekt CAnimationPoint z właściwościami domyślnymi: domyślne współrzędne punktów, identyfikator grupy i identyfikator obiektu są ustawione na 0.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList

Umieszcza zhermetyzowane zmienne animacji na liście.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Po powrocie funkcja zawiera wskaźniki do dwóch CAnimationVariable obiektów reprezentujących współrzędne X i Y.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue

Zwraca wartości domyślne współrzędnych X i Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Punkt zawierający wartość domyślną.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać wartość domyślną, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>CAnimationPoint::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parametry

*wartość ptValue*<br/>
Wyjście. Zawiera bieżącą wartość, gdy ta metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać bieżącą wartość punktu animacji. Jeśli ta metoda nie powiedzie się lub podstawowe obiekty COM dla współrzędnych X i Y nie zostały zainicjowane, ptValue zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub przez SetDefaultValue.

## <a name="canimationpointgetx"></a><a name="getx"></a>CAnimationPoint::GetX

Zapewnia dostęp do CAnimationVariable dla współrzędnych X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący współrzędnych X.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący współrzędnych X.

## <a name="canimationpointgety"></a><a name="gety"></a>CAnimationPoint::GetY

Zapewnia dostęp do CAnimationVariable dla współrzędnych Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący współrzędną Y.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący współrzędnych Y.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>CAnimationPoint::m_xValue

Zhermetyzowana zmienna animacji reprezentująca współrzędną X punktu animacji.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>CAnimationPoint::m_yValue

Zhermetyzowana zmienna animacji reprezentująca współrzędną Y punktu animacji.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>CAnimationPoint::operator CPoint

Konwertuje CAnimationPoint do CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość CAnimationPoint jako CPoint.

### <a name="remarks"></a>Uwagi

Ta funkcja wewnętrznie wywołuje GetValue. Jeśli GetValue z jakiegoś powodu nie powiedzie się, zwracany punkt będzie zawierać wartości domyślne dla współrzędnych X i Y.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>CAnimationPoint::operator=

Przypisuje ptSrc do CAnimationPoint.

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parametry

*ptSrc (polski)*<br/>
Odnosi się do CPoint lub POINT.

### <a name="remarks"></a>Uwagi

Przypisuje ptSrc do CAnimationPoint. Zaleca się, aby to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, który odtwarza podstawowe obiekty COM dla współrzędnych X i Y, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue

Ustawia wartość domyślną.

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parametry

*ptDefault (niem.*<br/>
Określa domyślną wartość punktu.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do ustawiania wartości domyślnej na obiekt animacji. Ta metoda przypisuje wartości domyślne do współrzędnych X i Y punktu animacji. Odtwarza również podstawowe obiekty COM, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
