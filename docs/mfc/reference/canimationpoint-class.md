---
title: CAnimationPoint Class
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
ms.openlocfilehash: 15f06d2fa3478570d2f784879a13e7b68515e746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218541"
---
# <a name="canimationpoint-class"></a>CAnimationPoint Class

Implementuje funkcje punktu, którego współrzędne mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Przeciążone. Tworzy obiekt CAnimationPoint.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Dodaje przejścia dla X i współrzędne Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla X i współrzędne Y.|
|[CAnimationPoint::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationPoint::GetX](#getx)|Zapewnia dostęp do CAnimationVariable dla współrzędną X.|
|[CAnimationPoint::GetY](#gety)|Zapewnia dostęp do CAnimationVariable współrzędnej Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne zhermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Konwertuje CAnimationPoint CPoint.|
|[CAnimationPoint::operator =](#operator_eq)|Przypisuje ptSrc CAnimationPoint.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Zmienna zhermetyzowany animacji, która reprezentuje X współrzędnych punktu animacji.|
|[CAnimationPoint::m_yValue](#m_yvalue)|Zmienna zhermetyzowany animacji, która przedstawia współrzędną Y punktu animacji.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationPoint hermetyzuje dwa obiekty CAnimationVariable i może reprezentować w aplikacjach punkt. Na przykład można użyć tej klasy, aby animować położenie obiektów na ekranie (na przykład ciąg tekstowy, okrąg, punkt itp.). Aby użyć tej klasy w aplikacji, po prostu utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywoływać AddTransition dla każdego przejścia, które mają być stosowane do współrzędne X i/lub Y.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

Dodaje przejścia dla X i współrzędne Y.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parametry

*pXTransition*<br/>
Wskaźnik do przejścia dla X współrzędne.

*pYTransition*<br/>
Koordynowanie wskaźnik, do którego nastąpi przejście, y.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dodać określonego przejścia do wewnętrznej listy przejścia, które mają być stosowane do zmiennych animacji dla X i współrzędne Y. Po dodaniu przejść, nie są stosowane natychmiast i przechowywane na liście wewnętrznych. Przejścia są stosowane (dodane do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie potrzebujesz zastosować przejścia do jednej współrzędnych, można przekazać wartości NULL.

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

Tworzy obiekt CAnimationPoint.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*ptDefault*<br/>
Określa domyślny współrzędnych punktu.

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Tworzy obiekt CAnimationPoint za pomocą właściwości domyślne: domyślnie współrzędnych punktu, identyfikator grupy i identyfikator obiektu są ustawione na 0.

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

Umieszcza zmienne zhermetyzowany animacji z listy.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
Po powrocie z tej funkcji zawiera wskaźniki do dwóch obiektów CAnimationVariable reprezentujący współrzędne X i Y.

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

Zwraca wartości domyślne dla X i współrzędne Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Punkt zawierającego wartość domyślną.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję można pobrać wartości domyślnej, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parametry

*ptValue*<br/>
Dane wyjściowe. Gdy metoda zwróci wartość, zawiera wartość bieżącą.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżąca wartość został pomyślnie pobrany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać bieżącą wartość punktu animacji. Jeśli ta metoda kończy się niepowodzeniem lub podstawowego modelu COM, obiekty x i współrzędne Y nie zostały zainicjowane, ptValue zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub SetDefaultValue.

##  <a name="getx"></a>  CAnimationPoint::GetX

Zapewnia dostęp do CAnimationVariable dla współrzędną X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący X koordynacji.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący X koordynacji.

##  <a name="gety"></a>  CAnimationPoint::GetY

Zapewnia dostęp do CAnimationVariable współrzędnej Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentująca współrzędną Y.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentująca współrzędną Y.

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

Zmienna zhermetyzowany animacji, która reprezentuje X współrzędnych punktu animacji.

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

Zmienna zhermetyzowany animacji, która przedstawia współrzędną Y punktu animacji.

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CAnimationPoint::operator CPoint

Konwertuje CAnimationPoint CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość CAnimationPoint jako CPoint.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje wewnętrznie GetValue. W przypadku niepowodzenia GetValue jakiegoś powodu zwracanego punktu będzie zawierać wartości domyślne dla X i współrzędne Y.

##  <a name="operator_eq"></a>  CAnimationPoint::operator =

Przypisuje ptSrc CAnimationPoint.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parametry

*ptSrc*<br/>
Odnosi się do CPoint lub punktu.

### <a name="remarks"></a>Uwagi

Przypisuje ptSrc CAnimationPoint. Zaleca się zrobić, czy przed jego rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, która odtwarza podstawowego modelu COM obiektów dla współrzędne X i Y, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parametry

*ptDefault*<br/>
Określa domyślną wartość punktu.

### <a name="remarks"></a>Uwagi

Aby ustawić wartość domyślną obiektu animacji, należy użyć tej funkcji. To ustawienie domyślne przypisuje metody wartości współrzędnych X i Y punktu animacji. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
