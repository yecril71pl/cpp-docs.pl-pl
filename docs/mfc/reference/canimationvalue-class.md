---
title: Klasa CAnimationValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afa8c61894a62df81705f98d461a37c35f615510
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062592"
---
# <a name="canimationvalue-class"></a>Klasa CAnimationValue

Implementuje funkcje obiektu animacji, które posiada jedną wartość.

## <a name="syntax"></a>Składnia

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Przeciążone. Tworzy obiekt CAnimationValue.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Dodaje przejście ma być stosowany do wartości.|
|[CAnimationValue::GetValue](#getvalue)|Przeciążone. Pobiera bieżącą wartość.|
|[CAnimationValue::GetVariable](#getvariable)|Zapewnia dostęp do zhermetyzowanego animacji zmiennej.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmiennej animacji zhermetyzowany z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::operator podwójnej PRECYZJI](#operator_double)|Zapewnia konwersji między CAnimationValue i podwójnej PRECYZJI.|
|[CAnimationValue::operator INT32](#operator_int32)|Zapewnia konwersji między CAnimationValue i INT32.|
|[CAnimationValue::operator =](#operator_eq)|Przeciążone. Przypisuje wartość INT32 CAnimationValue.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Zmienna zhermetyzowany animacji, która reprezentuje wartość animacji.|

## <a name="remarks"></a>Uwagi

Klasa CAnimationValue hermetyzuje pojedynczy obiekt CAnimationVariable i może reprezentować w aplikacjach pojedynczą wartość animowany. Na przykład, można użyć tej klasy, dla przejrzystości animowany (efekt fade), kąt (w celu obracania obiektów), lub dla wszystkich innych przypadkach, gdy trzeba utworzyć animację, w zależności od pojedynczej wartości animowany. Aby użyć tej klasy w aplikacji, po prostu utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywoływać AddTransition dla każdego przejścia, które mają być stosowane do wartości.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

Dodaje przejście ma być stosowany do wartości.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition*<br/>
Wskaźnik do obiektu przejścia.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dodać przejście do wewnętrznej listy przejścia, które mają być stosowane do zmiennej animacji. Po dodaniu przejść, nie są stosowane natychmiast i przechowywane na liście wewnętrznych. Przejścia są stosowane (dodane do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup.

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

Tworzy obiekt CAnimationValue.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa wartość domyślną.

*nGroupID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
Określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Tworzy obiekt CAnimationValue przy użyciu domyślnych właściwości: wartość domyślną, identyfikator grupy i identyfikator obiektu są ustawione na 0.

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

Umieszcza zmiennej animacji zhermetyzowany z listy.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*dzieł*<br/>
Po powrocie z tej funkcji zawiera wskaźnik do CAnimationVariable reprezentujący wartość animowany.

##  <a name="getvalue"></a>  CAnimationValue::GetValue

Pobiera bieżącą wartość.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue*<br/>
Dane wyjściowe. Gdy funkcja zwraca zawiera bieżącą wartość zmiennej animacji.

*nWartość:*<br/>
Dane wyjściowe. Gdy funkcja zwraca zawiera bieżącą wartość zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżąca wartość został pobrany pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać bieżącą wartość. Ta implementacja wywołuje zhermetyzowanego obiektu COM, a jeśli wywołanie zakończy się niepowodzeniem, ta metoda zwraca domyślną wartość, która została wcześniej ustawiona w konstruktorze lub SetDefaultValue.

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

Zapewnia dostęp do zhermetyzowanego animacji zmiennej.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zmiennej zhermetyzowany animacji.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia dostęp do zmiennej zhermetyzowany animacji. Z CAnimationVariable uzyskasz dostęp do bazowego obiektu IUIAnimationVariable, w których wskaźnik może mieć wartość NULL, jeśli nie utworzono zmienną animacji.

##  <a name="m_value"></a>  CAnimationValue::m_value

Zmienna zhermetyzowany animacji, która reprezentuje wartość animacji.

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator podwójnej PRECYZJI

Zapewnia konwersji między CAnimationValue i podwójnej PRECYZJI.

```
operator DOUBLE();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość animacji.

### <a name="remarks"></a>Uwagi

Zapewnia konwersji między CAnimationValue i podwójnej PRECYZJI. Wewnętrznie, ta metoda wywołuje metody GetValue i nie sprawdza błędy. Jeśli GetValue zakończy się niepowodzeniem, zwracana wartość będzie zawierać wcześniej ustawione w konstruktorze lub SetDefaultValue wartości domyślnej.

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

Zapewnia konwersji między CAnimationValue i INT32.

```
operator INT32();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość wartości animacji w postaci liczby całkowitej.

### <a name="remarks"></a>Uwagi

Zapewnia konwersji między CAnimationValue i INT32. Wewnętrznie, ta metoda wywołuje metody GetValue i nie sprawdza błędy. Jeśli GetValue zakończy się niepowodzeniem, zwracana wartość będzie zawierać wcześniej ustawione w konstruktorze lub SetDefaultValue wartości domyślnej.

##  <a name="operator_eq"></a>  CAnimationValue::operator =

Przypisuje wartość typu DOUBLE CAnimationValue.

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parametry

*dblVal*<br/>
Określa wartość do przypisania do wartości animacji.

*nVal*<br/>
Określa wartość do przypisania do wartości animacji.

### <a name="remarks"></a>Uwagi

Przypisuje wartość typu DOUBLE CAnimationValue. Ta wartość jest ustawiana jako wartości domyślnej dla zmiennej zhermetyzowany animacji. Jeśli subskrybujesz ten obiekt animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa domyślną wartość.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia ustawianie wartości domyślnej. Wartość domyślna jest zwracana do aplikacji, gdy animacji nie została uruchomiona i/lub nie został utworzony obiekt COM. Jeśli już utworzono obiekt COM, zhermetyzowanych w ramach CAnimationVarible, ta metoda tworzy go ponownie, dlatego może być konieczne wywoływanie metod EnableValueChanged/EnableIntegerValueChanged ponownie.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
