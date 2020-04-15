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
ms.openlocfilehash: 80a90dfa37bc1d2c3c84e6451ae23af7ded767c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369705"
---
# <a name="canimationsize-class"></a>Klasa CAnimationSize

Implementuje funkcjonalność obiektu o rozmiarze, którego wymiary mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Przeciążone. Konstruuje obiekt o rozmiarze animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Dodaje przejścia dla szerokości i wysokości.|
|[CAnimationSize::GetCX](#getcx)|Zapewnia dostęp do CAnimationVariable reprezentujący Szerokość.|
|[Rozmiar CAnimationSize::GetCY](#getcy)|Zapewnia dostęp do CAnimationVariable reprezentujący wysokość.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla Szerokość i Wysokość.|
|[CAnimationSize::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zhermetyzowane zmienne animacji na liście. (Zastępuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|Konwertuje CAnimationSize do CSize.|
|[CAnimationSize::operator=](#operator_eq)|Przypisuje szSrc do CAnimationSize.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Zhermetyzowana zmienna animacji reprezentująca szerokość rozmiaru animacji.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Zhermetyzowana zmienna animacji reprezentująca wysokość rozmiaru animacji.|

## <a name="remarks"></a>Uwagi

CAnimationSize klasa hermetyzuje dwa CAnimationVariable obiektów i może reprezentować w aplikacjach rozmiar. Na przykład można użyć tej klasy do animowania rozmiaru dowolnego obiektu dwuwymiarowego na ekranie (np. prostokąta, formantu itp.). Aby użyć tej klasy w aplikacji, wystarczy utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być zastosowane do width i/lub height.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>CAnimationSize::AddTransition

Dodaje przejścia dla szerokości i wysokości.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parametry

*pCXTransition (Tłumaczenie pCX)*<br/>
Wskaźnik do przejścia dla szerokości.

*pCYTransition*<br/>
Wskaźnik do przejścia dla height.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać określone przejścia do wewnętrznej listy przejść, które mają być stosowane do zmiennych animacji dla szerokość i wysokość. Po dodaniu przejść nie są one stosowane natychmiast i przechowywane na liście wewnętrznej. Przejścia są stosowane (dodawane do serii ujęć dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba stosować przejścia do jednego z wymiarów, można przekazać null.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>CAnimationSize::CAnimationSize

Konstruuje obiekt o rozmiarze animacji.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*szDefault (szDefault)*<br/>
Określa rozmiar domyślny.

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany z domyślnymi wartościami szerokości, wysokości, identyfikatora obiektu i identyfikatora grupy, które zostaną ustawione na 0. Można je zmienić później w czasie wykonywania przy użyciu SetDefaultValue i SetID.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList

Umieszcza zhermetyzowane zmienne animacji na liście.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Po powrocie funkcja zawiera wskaźniki do dwóch CAnimationVariable obiektów reprezentujących szerokość i wysokość.

## <a name="canimationsizegetcx"></a><a name="getcx"></a>CAnimationSize::GetCX

Zapewnia dostęp do CAnimationVariable reprezentujący Szerokość.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący Szerokość.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący Szerokość.

## <a name="canimationsizegetcy"></a><a name="getcy"></a>Rozmiar CAnimationSize::GetCY

Zapewnia dostęp do CAnimationVariable reprezentujący wysokość.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący wysokość.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący wysokość.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue

Zwraca wartości domyślne dla Szerokość i Wysokość.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt CSize zawierający wartości domyślne.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać wartość domyślną, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>CAnimationSize::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parametry

*szValue (szValue)*<br/>
Wyjście. Zawiera bieżącą wartość, gdy ta metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać bieżącą wartość rozmiaru animacji. Jeśli ta metoda nie powiedzie się lub podstawowe obiekty COM dla width i size nie zostały zainicjowane, szValue zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub przez SetDefaultValue.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>CAnimationSize::m_cxValue

Zhermetyzowana zmienna animacji reprezentująca szerokość rozmiaru animacji.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>CAnimationSize::m_cyValue

Zhermetyzowana zmienna animacji reprezentująca wysokość rozmiaru animacji.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>CAnimationSize::operator CSize

Konwertuje CAnimationSize do CSize.

```
operator CSize();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość rozmiaru animacji jako CSize.

### <a name="remarks"></a>Uwagi

Ta funkcja wewnętrznie wywołuje GetValue. Jeśli GetValue z jakiegoś powodu nie powiedzie się, zwracany rozmiar będzie zawierać wartości domyślne dla szerokość i wysokość.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>CAnimationSize::operator=

Przypisuje szSrc do CAnimationSize.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parametry

*szsrc ( szsrc )*<br/>
Odnosi się do CSize lub SIZE.

### <a name="remarks"></a>Uwagi

Przypisuje szSrc do CAnimationSize. Zaleca się, aby to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, który odtwarza podstawowe obiekty COM dla szerokość i wysokość, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parametry

*szDefault (szDefault)*<br/>
Określa nowy rozmiar domyślny.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do ustawiania wartości domyślnej na obiekt animacji. Ta metoda przypisuje wartości domyślne do szerokości i wysokości rozmiaru animacji. Odtwarza również podstawowe obiekty COM, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
