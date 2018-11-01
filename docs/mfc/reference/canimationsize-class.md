---
title: Klasa CAnimationSize
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: ad7200ca53aa99104270209ca253b93d2393d8a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448649"
---
# <a name="canimationsize-class"></a>Klasa CAnimationSize

Implementuje funkcje obiektu wymiarowego, którego wymiary mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Przeciążone. Konstruuje obiekt rozmiar animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Dodaje przejścia dla szerokości i wysokości.|
|[CAnimationSize::GetCX](#getcx)|Zapewnia dostęp do CAnimationVariable reprezentująca szerokość.|
|[CAnimationSize::GetCY](#getcy)|Zapewnia dostęp do CAnimationVariable reprezentująca wysokość.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla szerokości i wysokości.|
|[CAnimationSize::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne zhermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|Konwertuje CAnimationSize CSize.|
|[CAnimationSize::operator =](#operator_eq)|Przypisuje szSrc CAnimationSize.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Zmienna zhermetyzowany animacji, która reprezentuje szerokość w rozmiarze animacji.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Zmienna zhermetyzowany animacji, która reprezentuje wysokość w rozmiarze animacji.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationSize hermetyzuje dwa obiekty CAnimationVariable i może reprezentować w aplikacjach o rozmiarze. Na przykład, można użyć tej klasy, aby animować rozmiar dowolne dwa obiektu trójwymiarowego na ekranie (takich jak prostokąt, kontrolować itp.). Aby użyć tej klasy w aplikacji, po prostu utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywoływać AddTransition dla każdego przejścia, które mają być stosowane do szerokość lub wysokość.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationSize::AddTransition

Dodaje przejścia dla szerokości i wysokości.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parametry

*pCXTransition*<br/>
Wskaźnik do przejścia na szerokość.

*pCYTransition*<br/>
Wskaźnik do przejścia do wysokości.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dodać określonego przejścia do wewnętrznej listy przejścia, które mają być stosowane do zmiennych animacji, szerokość i wysokość. Po dodaniu przejść, nie są stosowane natychmiast i przechowywane na liście wewnętrznych. Przejścia są stosowane (dodane do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie potrzebujesz zastosować przejścia do jednej z wymiarów, można przekazać wartości NULL.

##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize

Konstruuje obiekt rozmiar animacji.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*szDefault*<br/>
Określa domyślny rozmiar.

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany przy użyciu wartości domyślnych dla szerokości, wysokości obiektu, identyfikator i identyfikator grupy, które zostaną ustawione na 0. Można ich zmienić później w czasie wykonywania za pomocą SetDefaultValue i identyfikator zestawu.

##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList

Umieszcza zmienne zhermetyzowany animacji z listy.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
Po powrocie z tej funkcji zawiera wskaźniki do dwóch obiektów CAnimationVariable reprezentująca szerokość i wysokość.

##  <a name="getcx"></a>  CAnimationSize::GetCX

Zapewnia dostęp do CAnimationVariable reprezentująca szerokość.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentująca szerokość.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentująca szerokość.

##  <a name="getcy"></a>  CAnimationSize::GetCY

Zapewnia dostęp do CAnimationVariable reprezentująca wysokość.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentująca wysokość.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentująca wysokość.

##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue

Zwraca wartości domyślne dla szerokości i wysokości.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt CSize zawierający wartości domyślne.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję można pobrać wartości domyślnej, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationSize::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parametry

*szValue*<br/>
Dane wyjściowe. Gdy metoda zwróci wartość, zawiera wartość bieżącą.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżąca wartość został pomyślnie pobrany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać bieżącą wartość rozmiaru animacji. Jeśli ta metoda nie powiedzie się lub nie zostały zainicjowane podstawowych obiektów COM dla szerokości i rozmiar, szValue zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub SetDefaultValue.

##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue

Zmienna zhermetyzowany animacji, która reprezentuje szerokość w rozmiarze animacji.

```
CAnimationVariable m_cxValue;
```

##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue

Zmienna zhermetyzowany animacji, która reprezentuje wysokość w rozmiarze animacji.

```
CAnimationVariable m_cyValue;
```

##  <a name="operator_csize"></a>  CAnimationSize::operator CSize

Konwertuje CAnimationSize CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru CSize animacji.

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje wewnętrznie GetValue. Jeśli GetValue jakiegoś powodu nie powiedzie się, rozmiaru zwróconego będzie zawierać wartości domyślne dla szerokości i wysokości.

##  <a name="operator_eq"></a>  CAnimationSize::operator =

Przypisuje szSrc CAnimationSize.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parametry

*szSrc*<br/>
Odnosi się do CSize lub rozmiaru.

### <a name="remarks"></a>Uwagi

Przypisuje szSrc CAnimationSize. Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, która odtwarza obiektów COM dla szerokości i wysokości, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parametry

*szDefault*<br/>
Określa nowy rozmiar domyślny.

### <a name="remarks"></a>Uwagi

Aby ustawić wartość domyślną obiektu animacji, należy użyć tej funkcji. Ta metoda przypisuje wartości domyślne szerokość i wysokość w rozmiarze animacji. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
