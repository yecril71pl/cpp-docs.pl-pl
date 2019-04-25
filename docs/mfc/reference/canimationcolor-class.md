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
ms.openlocfilehash: ee6003a22db78c2a510579c3d717fec887f8a6ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151178"
---
# <a name="canimationcolor-class"></a>Klasa CAnimationColor

Implementuje funkcje koloru, których składniki czerwony, zielony i niebieski mogą być animowane.

## <a name="syntax"></a>Składnia

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Przeciążone. Konstruuje obiekt, animacji kolorów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Dodaje przejścia dla składników czerwony, zielony i niebieski.|
|[CAnimationColor::GetB](#getb)|Zapewnia dostęp do CAnimationVariable reprezentujący składnik niebieski.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla składników koloru.|
|[CAnimationColor::GetG](#getg)|Zapewnia dostęp do CAnimationVariable reprezentujący składnik zielony.|
|[CAnimationColor::GetR](#getr)|Zapewnia dostęp do CAnimationVariable reprezentujący składnik czerwony.|
|[CAnimationColor::GetValue](#getvalue)|Zwraca bieżącą wartość.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne zhermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|Przypisuje CAnimationColor kolorów.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Zmienna zhermetyzowany animacji, która reprezentuje składnik niebieski, animacji kolorów.|
|[CAnimationColor::m_gValue](#m_gvalue)|Zmienna zhermetyzowany animacji, która reprezentuje składnik zielony, animacji kolorów.|
|[CAnimationColor::m_rValue](#m_rvalue)|Zmienna zhermetyzowany animacji, która reprezentuje składnik czerwony, animacji kolorów.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationColor hermetyzuje trzy obiekty CAnimationVariable i może reprezentować w aplikacjach koloru. Na przykład, można użyć tej klasy animacji kolorów dowolnego obiektu, na ekranie (np. kolor tekstu, kolor tła itp.). Aby użyć tej klasy w aplikacji, po prostu utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywoływać AddTransition dla każdego przejścia, które mają być stosowane do składników czerwony, zielony i niebieski.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationColor::AddTransition

Dodaje przejścia dla składników czerwony, zielony i niebieski.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parametry

*pRTransition*<br/>
Przejście dla składnika czerwony.

*pGTransition*<br/>
Przejście dla składnika zielony.

*pBTransition*<br/>
Przejście dla składnika niebieski.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dodać określonego przejścia do wewnętrznej listy przejścia, które mają być stosowane do zmiennych animacji reprezentująca składniki kolorów. Po dodaniu przejść, nie są stosowane natychmiast i przechowywane na liście wewnętrznych. Przejścia są stosowane (dodane do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie ma potrzeby zastosowanie przejścia do jednego ze składników koloru, można przekazać wartości NULL.

##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor

Tworzy obiekt CAnimationColor.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Określa domyślny kolor.

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany przy użyciu wartości domyślnych dla czerwony, zielony, niebieski, identyfikator grupy, które zostaną ustawione na 0 lub identyfikator obiektu. Można ich zmienić później w czasie wykonywania za pomocą SetDefaultValue i identyfikator zestawu.

##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList

Umieszcza zmienne zhermetyzowany animacji z listy.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
Po powrocie z tej funkcji zawiera wskaźniki do trzech obiektów CAnimationVariable reprezentująca składniki czerwony, zielony i niebieski.

##  <a name="getb"></a>  CAnimationColor::GetB

Zapewnia dostęp do CAnimationVariable reprezentujący składnik niebieski.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący składnik niebieski.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący składnik niebieski.

##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue

Zwraca wartości domyślne dla składników koloru.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Wartość zwracana

Wartość COLORREF zawierający wartości domyślne dla składników RGB.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję można pobrać wartości domyślnej, która została wcześniej ustawiona przez konstruktora lub SetDefaultValue.

##  <a name="getg"></a>  CAnimationColor::GetG

Zapewnia dostęp do CAnimationVariable reprezentujący składnik zielony.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujące składnik zielony.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujące składnik zielony.

##  <a name="getr"></a>  CAnimationColor::GetR

Zapewnia dostęp do CAnimationVariable reprezentujący składnik czerwony.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zhermetyzowanego CAnimationVariable reprezentujący składnik czerwony.

### <a name="remarks"></a>Uwagi

Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący składnik czerwony.

##  <a name="getvalue"></a>  CAnimationColor::GetValue

Zwraca bieżącą wartość.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Dane wyjściowe. Gdy metoda zwróci wartość, zawiera wartość bieżącą.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżąca wartość został pomyślnie pobrany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać bieżącą wartość koloru animacji. Jeśli ta metoda nie powiedzie się lub nie zostały zainicjowane podstawowych obiektów COM dla składników koloru, kolor zawiera wartość domyślną, która została wcześniej ustawiona w konstruktorze lub SetDefaultValue.

##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue

Zmienna zhermetyzowany animacji, która reprezentuje składnik niebieski, animacji kolorów.

```
CAnimationVariable m_bValue;
```

##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue

Zmienna zhermetyzowany animacji, która reprezentuje składnik zielony, animacji kolorów.

```
CAnimationVariable m_gValue;
```

##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue

Zmienna zhermetyzowany animacji, która reprezentuje składnik czerwony, animacji kolorów.

```
CAnimationVariable m_rValue;
```

##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq"></a>  CAnimationColor::operator =

Przypisuje CAnimationColor kolorów.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Określa nową wartość koloru animacji.

### <a name="remarks"></a>Uwagi

Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, która odtwarza obiektów COM dla składników koloru, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Określa nowe wartości domyślne dla składników czerwonego, zielonego i niebieskiego.

### <a name="remarks"></a>Uwagi

Aby ustawić wartość domyślną obiektu animacji, należy użyć tej funkcji. Tej metody przypisuje wartości domyślne do kolorów składników animacji kolorów. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="see-also"></a>Zobacz także

[Klasy](../../mfc/reference/mfc-classes.md)
