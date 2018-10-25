---
title: Klasa CAnimationRect | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec22bfd2805f4af432821c4aaeb350a2cf635cfa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083428"
---
# <a name="canimationrect-class"></a>Klasa CAnimationRect

Implementuje funkcje prostokąta, którego boki mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Przeciążone. Konstruuje obiekt prostokąt animacji.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Dodaje przejścia dla współrzędnych po lewej stronie, górnej, prawej strony i dolnej.|
|[CAnimationRect::GetBottom](#getbottom)|Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna dolnej.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla granice prostokąta.|
|[CAnimationRect::GetLeft](#getleft)|Zapewnia dostęp do CAnimationVariable reprezentująca współrzędną po lewej stronie.|
|[CAnimationRect::GetRight](#getright)|Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna prawej.|
|[CAnimationRect::GetTop](#gettop)|Zapewnia dostęp do CAnimationVariable reprezentujący górną współrzędną.|
|[CAnimationRect::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne zhermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Konwertuje CAnimationRect prostokątny|
|[CAnimationRect::operator =](#operator_eq)|Przypisuje CAnimationRect prostokąt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Określa, czy prostokąt ma ustalony rozmiar.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Powiązana zmienna zhermetyzowany animacji, która reprezentuje dołu prostokąta animacji.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Zmienna zhermetyzowany animacji, która reprezentuje po lewej stronie jest powiązana prostokąta animacji.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Zmienna zhermetyzowany animacji, która reprezentuje po prawej stronie jest powiązana prostokąta animacji.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Określa początkowy rozmiar prostokąta animacji.|
|[CAnimationRect::m_topValue](#m_topvalue)|Zmienna zhermetyzowany animacji, która reprezentuje górnej powiązany prostokąta animacji.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationRect hermetyzuje cztery obiekty CAnimationVariable i może reprezentować w aplikacjach prostokąta. Aby użyć tej klasy w aplikacji, po prostu utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywoływać AddTransition dla każdego przejścia, które mają być stosowane do lewy, prawy górny i dolny współrzędnych.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

Dodaje przejścia dla współrzędnych po lewej stronie, górnej, prawej strony i dolnej.

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parametry

*pLeftTransition*<br/>
Określa przeniesienie po lewej stronie.

*pTopTransition*<br/>
Określa przejścia dla górnej.

*pRightTransition*<br/>
Określa przeniesienie po prawej stronie.

*pBottomTransition*<br/>
Określa przejścia dla dolnej.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dodać określonego przejścia do wewnętrznej listy przejścia, które mają być stosowane do zmiennych animacji dla każdej strony prostokąta. Po dodaniu przejść, nie są stosowane natychmiast i przechowywane na liście wewnętrznych. Przejścia są stosowane (dodane do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie ma potrzeby zastosowanie przejścia do jednej strony, prostokąt, można przekazać wartości NULL.

##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect

Tworzy obiekt CAnimationRect.

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
Określa domyślny prostokąta.

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

*(czas pacyficzny)*<br/>
Współrzędna w lewym górnym rogu.

*Sz*<br/>
Rozmiar prostokąta.

*nLeft*<br/>
Określa współrzędną lewej granicy.

*nTop*<br/>
Określa współrzędną górnej powiązany.

*nRight*<br/>
Określa współrzędną prawej granicy.

*nBottom*<br/>
Określa współrzędną dolnej powiązany.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany przy użyciu wartości domyślne po lewej stronie, górnej, prawej strony i dolnej, identyfikator grupy, które zostaną ustawione na 0 lub identyfikator obiektu. Można ich zmienić później w czasie wykonywania za pomocą SetDefaultValue i identyfikator zestawu.

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

Umieszcza zmienne zhermetyzowany animacji z listy.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
Po powrocie z tej funkcji zawiera wskaźniki do czterech obiektów CAnimationVariable reprezentujący współrzędnych prostokąta.

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna dolnej.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący Współrzędna dolnej.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący Współrzędna dolnej.

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

Zwraca wartości domyślne dla granice prostokąta.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

CRect wartość zawierający wartości domyślne dla lewy, prawy, górny i dolny.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję można pobrać wartości domyślnej, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

##  <a name="getleft"></a>  CAnimationRect::GetLeft

Zapewnia dostęp do CAnimationVariable reprezentująca współrzędną po lewej stronie.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący lewą współrzędną.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący lewą współrzędną.

##  <a name="getright"></a>  CAnimationRect::GetRight

Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna prawej.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący Współrzędna prawej.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący Współrzędna prawej.

##  <a name="gettop"></a>  CAnimationRect::GetTop

Zapewnia dostęp do CAnimationVariable reprezentujący górną współrzędną.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący górną współrzędną.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący górną współrzędną.

##  <a name="getvalue"></a>  CAnimationRect::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Dane wyjściowe. Gdy metoda zwróci wartość, zawiera wartość bieżącą.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżąca wartość został pomyślnie pobrany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać bieżącą wartość prostokąt animacji. Jeśli ta metoda kończy się niepowodzeniem lub podstawowej COM obiekty do lewej, góra, prawo i w dół nie zostały zainicjowane, prostokąt zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub SetDefaultValue.

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

Określa, czy prostokąt ma ustalony rozmiar.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Uwagi

Jeśli ten element członkowski ma wartość true, rozmiar prostokąta jest stały i w prawo, a dolny — wartości są ponownie obliczane, każdym razem, gdy w lewym górnym rogu zostanie przeniesiona zgodnie z ustalonym rozmiarze. Ustaw tę wartość na wartość TRUE, aby łatwo przenieść prostokąt wokół ekranu. W takim przypadku stosowane do prawej i u dołu współrzędnych przejścia są ignorowane. Rozmiar są przechowywane wewnętrznie, podczas konstruowania obiektu i/lub wywołaj SetDefaultValue. Domyślnie ten element członkowski ma wartość FALSE.

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

Powiązana zmienna zhermetyzowany animacji, która reprezentuje dołu prostokąta animacji.

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

Zmienna zhermetyzowany animacji, która reprezentuje po lewej stronie jest powiązana prostokąta animacji.

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

Zmienna zhermetyzowany animacji, która reprezentuje po prawej stronie jest powiązana prostokąta animacji.

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

Określa początkowy rozmiar prostokąta animacji.

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

Zmienna zhermetyzowany animacji, która reprezentuje górnej powiązany prostokąta animacji.

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

Konwertuje CAnimationRect prostokątny

```
operator RECT();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość prostokąta animacji jako prostokątny

### <a name="remarks"></a>Uwagi

Ta funkcja wywołuje wewnętrznie GetValue. Jeśli GetValue jakiegoś powodu nie powiedzie się, zwrócone Prostokąt będzie zawierać wartości domyślne dla wszystkich współrzędnych prostokąta.

##  <a name="operator_eq"></a>  CAnimationRect::operator =

Przypisuje CAnimationRect prostokąt.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Nowa wartość prostokąt animacji.

### <a name="remarks"></a>Uwagi

Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, która odtwarza obiektów COM dla składników koloru, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Określa nowe wartości domyślne po lewej stronie, górnej, prawej strony i dolnej.

### <a name="remarks"></a>Uwagi

Aby ustawić wartość domyślną obiektu animacji, należy użyć tej funkcji. Ta metoda przypisuje wartości domyślne granice prostokąta. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
