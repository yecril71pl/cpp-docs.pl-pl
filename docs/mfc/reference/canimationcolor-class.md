---
title: Klasa CAnimationColor
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 5940cce6d55b95d8e1bac103cacc0bc828c213de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371108"
---
# <a name="canimationcolor-class"></a>Klasa CAnimationColor

Implementuje funkcjonalność koloru, którego składniki czerwony, zielony i niebieski mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Przeciążone. Konstruuje obiekt koloru animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Dodaje przejścia dla komponentów Czerwony, Zielony i Niebieski.|
|[CAnimationColor::GetB](#getb)|Zapewnia dostęp do CAnimationVariable reprezentujący składnik Blue.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla komponentów kolorów.|
|[CAnimationColor::GetG](#getg)|Zapewnia dostęp do CAnimationVariable reprezentujący zielony składnik.|
|[CAnimationColor::GetR](#getr)|Zapewnia dostęp do CAnimationVariable reprezentujący czerwony składnik.|
|[CAnimationColor::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zhermetyzowane zmienne animacji na liście. (Zastępuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|Przypisuje kolor do CAnimationColor.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Zhermetyzowana zmienna animacji reprezentująca niebieski składnik koloru animacji.|
|[CAnimationColor::m_gValue](#m_gvalue)|Zhermetyzowana zmienna animacji reprezentująca zielony składnik koloru animacji.|
|[CAnimationColor::m_rValue](#m_rvalue)|Zhermetyzowana zmienna animacji reprezentująca czerwony składnik koloru animacji.|

## <a name="remarks"></a>Uwagi

CAnimationColor Klasa hermetyzuje trzy CAnimationVariable obiektów i może reprezentować w aplikacjach kolor. Na przykład można użyć tej klasy do animowania kolorów dowolnego obiektu na ekranie (np. koloru tekstu, koloru tła itp.). Aby użyć tej klasy w aplikacji, wystarczy utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być stosowane do składników Czerwony, Zielony i Niebieski.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>CAnimationColor::AddTransition

Dodaje przejścia dla komponentów Czerwony, Zielony i Niebieski.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parametry

*pRTransition (tłumaczenie na pR)*<br/>
Przejście dla komponentu Czerwony.

*pGTransition (tłumaczenie pG)*<br/>
Przejście dla komponentu Zielony.

*pBTransition (tłumaczenie na pB)*<br/>
Przejście dla niebieskiego komponentu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać określone przejścia do wewnętrznej listy przejść, które mają być stosowane do zmiennych animacji reprezentujących składniki kolorów. Po dodaniu przejść nie są one stosowane natychmiast i przechowywane na liście wewnętrznej. Przejścia są stosowane (dodawane do serii ujęć dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba stosować przejścia do jednego ze składników kolorów, można przekazać null.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>CAnimationColor::CAnimationColor

Konstruuje CAnimationColor obiektu.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Określa kolor domyślny.

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany z wartościami domyślnymi dla czerwonego, zielonego, niebieskiego, identyfikatora obiektu i identyfikatora grupy, który zostanie ustawiony na 0. Można je zmienić później w czasie wykonywania przy użyciu SetDefaultValue i SetID.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationColor::GetAnimationVariableList

Umieszcza zhermetyzowane zmienne animacji na liście.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Po powrocie funkcja zawiera wskaźniki do trzech CAnimationVariable obiektów reprezentujących czerwone, zielone i niebieskie składniki.

## <a name="canimationcolorgetb"></a><a name="getb"></a>CAnimationColor::GetB

Zapewnia dostęp do CAnimationVariable reprezentujący składnik Blue.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący składnik Blue.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący składnik Blue.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationColor::GetDefaultValue

Zwraca wartości domyślne dla komponentów kolorów.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF zawierająca wartości domyślne dla komponentów RGB.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać wartość domyślną, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

## <a name="canimationcolorgetg"></a><a name="getg"></a>CAnimationColor::GetG

Zapewnia dostęp do CAnimationVariable reprezentujący zielony składnik.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący zielony składnik.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący zielony składnik.

## <a name="canimationcolorgetr"></a><a name="getr"></a>CAnimationColor::GetR

Zapewnia dostęp do CAnimationVariable reprezentujący czerwony składnik.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący czerwony składnik.

### <a name="remarks"></a>Uwagi

Tę metodę można wywołać, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący czerwony składnik.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>CAnimationColor::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Wyjście. Zawiera bieżącą wartość, gdy ta metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać bieżącą wartość koloru animacji. Jeśli ta metoda nie powiedzie się lub podstawowe obiekty COM dla składników kolorów nie zostały zainicjowane, kolor zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub przez SetDefaultValue.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>CAnimationColor::m_bValue

Zhermetyzowana zmienna animacji reprezentująca niebieski składnik koloru animacji.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>CAnimationColor::m_gValue

Zhermetyzowana zmienna animacji reprezentująca zielony składnik koloru animacji.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>CAnimationColor::m_rValue

Zhermetyzowana zmienna animacji reprezentująca czerwony składnik koloru animacji.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Wartość zwracana

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>CAnimationColor::operator=

Przypisuje kolor do CAnimationColor.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Określa nową wartość Kolor animacji.

### <a name="remarks"></a>Uwagi

Zaleca się, aby to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, który odtwarza podstawowe obiekty COM dla składników kolorów, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationColor::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Określa nowe wartości domyślne dla komponentów czerwonych, zielonych i niebieskich.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do ustawiania wartości domyślnej na obiekt animacji. Ta metoda przypisuje wartości domyślne do składników kolorów koloru animacji. Odtwarza również podstawowe obiekty COM, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
