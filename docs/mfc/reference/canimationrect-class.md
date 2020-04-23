---
title: Klasa CAnimationRect
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 273ea2b548d35722ebf937d2db2b589fef5e69fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755137"
---
# <a name="canimationrect-class"></a>Klasa CAnimationRect

Implementuje funkcjonalność prostokąta, którego boki mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Przeciążone. Konstruuje obiekt rekt animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Dodaje przejścia dla współrzędnych lewej, górnej, prawej i dolnej.|
|[CAnimationRect::GetBottom](#getbottom)|Zapewnia dostęp do CAnimationVariable reprezentujący dolną współrzędną.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla granic prostokąta.|
|[CAnimationRect::GetLeft](#getleft)|Zapewnia dostęp do CAnimationVariable reprezentujący lewej współrzędnej.|
|[CAnimationRect::GetRight](#getright)|Zapewnia dostęp do CAnimationVariable reprezentujący prawą współrzędną.|
|[CAnimationRect::GetTop](#gettop)|Zapewnia dostęp do CAnimationVariable reprezentujący górnej współrzędnej.|
|[CAnimationRect::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zhermetyzowane zmienne animacji na liście. (Zastępuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Konwertuje CAnimationRect do RECT.|
|[CAnimationRect::operator=](#operator_eq)|Przypisuje rect do CAnimationRect.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Określa, czy prostokąt ma stały rozmiar.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Zhermetyzowana zmienna animacji reprezentująca dolną granicę prostokąta animacji.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Zhermetyzowana zmienna animacji reprezentująca lewą oprawę prostokąta animacji.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Zhermetyzowana zmienna animacji reprezentująca prawą granicę prostokąta animacji.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Określa początkowy rozmiar prostokąta animacji.|
|[CAnimationRect::m_topValue](#m_topvalue)|Zhermetyzowana zmienna animacji reprezentująca Górną granicę prostokąta animacji.|

## <a name="remarks"></a>Uwagi

CAnimationRect Klasa hermetyzuje cztery CAnimationVariable obiektów i może reprezentować w aplikacjach prostokąt. Aby użyć tej klasy w aplikacji, wystarczy utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być stosowane do lewej, prawej górnej i dolnej współrzędne.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>CAnimationRect::AddTransition

Dodaje przejścia dla współrzędnych lewej, górnej, prawej i dolnej.

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parametry

*pLeftTransition (Polski)*<br/>
Określa przejście dla lewej strony.

*pTopTransition (Tłumaczenie na wierzchu)*<br/>
Określa przejście dla górnej strony.

*pRightTransition (Tłumaczenie pRight)*<br/>
Określa przejście po prawej stronie.

*pBottomTransition (Tłumaczenie na bottom)*<br/>
Określa przejście dla dolnej części.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać określone przejścia do wewnętrznej listy przejść, które mają być stosowane do zmiennych animacji dla każdej strony prostokąta. Po dodaniu przejść nie są one stosowane natychmiast i przechowywane na liście wewnętrznej. Przejścia są stosowane (dodawane do serii ujęć dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednej z boków prostokąta, można przekazać NULL.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>CAnimationRect::CAnimationRect

Konstruuje CAnimationRect obiektu.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Określa domyślny prostokąt.

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

*Pt*<br/>
Współrzędna lewego górnego rogu.

*Sz*<br/>
Rozmiar prostokąta.

*nNaft*<br/>
Określa współrzędne lewej granicy.

*nNa szczycie*<br/>
Określa współrzędne górnej granicy.

*nWej*<br/>
Określa współrzędne prawej granicy.

*nBottom (właśc.*<br/>
Określa współrzędne dolnej granicy.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany z wartościami domyślnymi dla lewej, górnej, prawej i dolnej, identyfikatora obiektu i identyfikatora grupy, która zostanie ustawiona na 0. Można je zmienić później w czasie wykonywania przy użyciu SetDefaultValue i SetID.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList

Umieszcza zhermetyzowane zmienne animacji na liście.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Po powrocie funkcja zawiera wskaźniki do czterech CAnimationVariable obiektów reprezentujących współrzędne prostokąta.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>CAnimationRect::GetBottom

Zapewnia dostęp do CAnimationVariable reprezentujący dolną współrzędną.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący dolną współrzędną.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący dolnej współrzędnej.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue

Zwraca wartości domyślne dla granic prostokąta.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Wartość CRect zawierająca wartości domyślne dla lewej, prawej, górnej i dolnej.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać wartość domyślną, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

## <a name="canimationrectgetleft"></a><a name="getleft"></a>CAnimationRect::GetLeft

Zapewnia dostęp do CAnimationVariable reprezentujący lewej współrzędnej.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący lewą współrzędną.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący lewą współrzędną.

## <a name="canimationrectgetright"></a><a name="getright"></a>CAnimationRect::GetRight

Zapewnia dostęp do CAnimationVariable reprezentujący prawą współrzędną.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący prawą współrzędną.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący prawą współrzędną.

## <a name="canimationrectgettop"></a><a name="gettop"></a>CAnimationRect::GetTop

Zapewnia dostęp do CAnimationVariable reprezentujący górnej współrzędnej.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do hermetyzowanych CAnimationVariable reprezentujący górnej współrzędnej.

### <a name="remarks"></a>Uwagi

Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowej CAnimationVariable reprezentujący górnej współrzędnej.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>CAnimationRect::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Wyjście. Zawiera bieżącą wartość, gdy ta metoda zwraca.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać bieżącą wartość prostokąta animacji. Jeśli ta metoda nie powiedzie się lub podstawowe obiekty COM dla lewej, górnej, prawej i dolnej nie zostały zainicjowane, rect zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub przez SetDefaultValue.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize

Określa, czy prostokąt ma stały rozmiar.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Uwagi

Jeśli ten element członkowski jest true, a następnie rozmiar prostokąta jest stała i prawe i dolne wartości są ponownie obliczane za każdym razem, gdy lewy górny róg jest przenoszony zgodnie ze stałym rozmiarem. Ustaw tę wartość na WARTOŚĆ TRUE, aby łatwo przesuwać prostokąt po ekranie. W tym przypadku przejścia zastosowane do współrzędnych prawej i dolnej są ignorowane. Rozmiar jest przechowywany wewnętrznie podczas konstruowania obiektu i/lub wywołania SetDefaultValue. Domyślnie ten element członkowski jest ustawiony na FAŁSZ.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue

Zhermetyzowana zmienna animacji reprezentująca dolną granicę prostokąta animacji.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>CAnimationRect::m_leftValue

Zhermetyzowana zmienna animacji reprezentująca lewą oprawę prostokąta animacji.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>CAnimationRect::m_rightValue

Zhermetyzowana zmienna animacji reprezentująca prawą granicę prostokąta animacji.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>CAnimationRect::m_szInitial

Określa początkowy rozmiar prostokąta animacji.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>CAnimationRect::m_topValue

Zhermetyzowana zmienna animacji reprezentująca Górną granicę prostokąta animacji.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>CAnimationRect::operator RECT

Konwertuje CAnimationRect do RECT.

```
operator RECT();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta animacji jako RECT.

### <a name="remarks"></a>Uwagi

Ta funkcja wewnętrznie wywołuje GetValue. Jeśli GetValue z jakiegoś powodu nie powiedzie się, zwrócone RECT będzie zawierać wartości domyślne dla wszystkich współrzędnych prostokąta.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>CAnimationRect::operator=

Przypisuje rect do CAnimationRect.

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Nowa wartość prostokąta animacji.

### <a name="remarks"></a>Uwagi

Zaleca się, aby to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, który odtwarza podstawowe obiekty COM dla składników kolorów, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue

Ustawia wartość domyślną.

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Określa nowe wartości domyślne dla lewej, górnej, prawej i dolnej.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do ustawiania wartości domyślnej na obiekt animacji. Ta metoda przypisuje wartości domyślne do granic prostokąta. Odtwarza również podstawowe obiekty COM, jeśli zostały utworzone. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
