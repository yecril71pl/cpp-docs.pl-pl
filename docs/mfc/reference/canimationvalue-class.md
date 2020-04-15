---
title: Klasa CAnimationValue
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: 0437f0fc66f64ccb99157330154bf5aa4b5666b3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321978"
---
# <a name="canimationvalue-class"></a>Klasa CAnimationValue

Implementuje funkcjonalność obiektu animacji, który ma jedną wartość.

## <a name="syntax"></a>Składnia

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Przeciążone. Konstruuje CAnimationValue obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Dodaje przejście, które ma zostać zastosowane do wartości.|
|[CAnimationValue::GetValue](#getvalue)|Przeciążone. Pobiera bieżącą wartość.|
|[CAnimationValue::GetVariable](#getvariable)|Zapewnia dostęp do zmiennej animacji zhermetyzowanej.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zhermetyzowaną zmienną animacji na liście. (Zastępuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::operator DOUBLE](#operator_double)|Zapewnia konwersję między CAnimationValue i DOUBLE.|
|[CAnimationValue::operator INT32](#operator_int32)|Zapewnia konwersję między CAnimationValue i INT32.|
|[CAnimationValue::operator=](#operator_eq)|Przeciążone. Przypisuje wartość INT32 do CAnimationValue.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Zhermetyzowana zmienna animacji reprezentująca wartość animacji.|

## <a name="remarks"></a>Uwagi

CAnimationValue klasa hermetyzuje pojedynczy CAnimationVariable obiektu i może reprezentować w aplikacjach pojedynczą wartość animowaną. Na przykład tej klasy można użyć dla animowanej przezroczystości (efekt zanikania), kąta (obracania obiektów) lub w każdym innym przypadku, gdy trzeba utworzyć animację w zależności od pojedynczej animowanej wartości. Aby użyć tej klasy w aplikacji, wystarczy utworzyć wystąpienie obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być zastosowane do wartości.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition

Dodaje przejście, które ma zostać zastosowane do wartości.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parametry

*pTransition (tłumaczenie na pTransition)*<br/>
Wskaźnik do obiektu przejścia.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dodać przejście do wewnętrznej listy przejść, które mają być stosowane do zmiennej animacji. Po dodaniu przejść nie są one stosowane natychmiast i przechowywane na liście wewnętrznej. Przejścia są stosowane (dodawane do serii ujęć dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue

Konstruuje CAnimationValue obiektu.

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

*nGrupaID*<br/>
Określa identyfikator grupy.

*nObjectID*<br/>
Określa identyfikator obiektu.

*dwUserData*<br/>
określa dane zdefiniowane przez użytkownika.

### <a name="remarks"></a>Uwagi

Konstrukcje CAnimationValue obiekt z właściwościami domyślnymi: wartość domyślna, Identyfikator grupy i identyfikator obiektu są ustawione na 0.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList

Umieszcza zhermetyzowaną zmienną animacji na liście.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
Gdy funkcja zwraca, zawiera wskaźnik do CAnimationVariable reprezentujący animowaną wartość.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue

Pobiera bieżącą wartość.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parametry

*dblValue (wartość dblValue)*<br/>
Wyjście. Gdy funkcja zwraca zawiera bieżącą wartość zmiennej animacji.

*wartość nValue*<br/>
Wyjście. Gdy funkcja zwraca zawiera bieżącą wartość zmiennej animacji.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca wartość została pobrana pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać bieżącą wartość. Ta implementacja wywołuje zhermetyzowany obiekt COM, a jeśli wywołanie zakończy się niepowodzeniem, ta metoda zwraca wartość domyślną, która została wcześniej ustawiona w konstruktorze lub z SetDefaultValue.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable

Zapewnia dostęp do zmiennej animacji zhermetyzowanej.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do zmiennej animacji zhermetyzowanej.

### <a name="remarks"></a>Uwagi

Ta metoda służy do uzyskiwania dostępu do zmiennej animacji zhermetyzowanej. Z CAnimationVariable można uzyskać dostęp do podstawowej IUIAnimationVariable obiektu, którego wskaźnik może być NULL, jeśli zmienna animacji nie została utworzona.

## <a name="canimationvaluem_value"></a><a name="m_value"></a>CAnimationValue::m_value

Zhermetyzowana zmienna animacji reprezentująca wartość animacji.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operator DOUBLE

Zapewnia konwersję między CAnimationValue i DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość wartości animacji.

### <a name="remarks"></a>Uwagi

Zapewnia konwersję między CAnimationValue i DOUBLE. Ta metoda wewnętrznie wywołuje GetValue i nie sprawdza błędów. Jeśli GetValue nie powiedzie się, zwracana wartość będzie zawierać wartość domyślną wcześniej ustawioną w konstruktorze lub z SetDefaultValue.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::operator INT32

Zapewnia konwersję między CAnimationValue i INT32.

```
operator INT32();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość wartości animacji jako liczby całkowitej.

### <a name="remarks"></a>Uwagi

Zapewnia konwersję między CAnimationValue i INT32. Ta metoda wewnętrznie wywołuje GetValue i nie sprawdza błędów. Jeśli GetValue nie powiedzie się, zwracana wartość będzie zawierać wartość domyślną wcześniej ustawioną w konstruktorze lub z SetDefaultValue.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operator=

Przypisuje wartość DOUBLE do CAnimationValue.

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parametry

*dblVal (właśc.*<br/>
Określa wartość, która ma być przypisana do wartości animacji.

*nVal (Ł.*<br/>
Określa wartość, która ma być przypisana do wartości animacji.

### <a name="remarks"></a>Uwagi

Przypisuje wartość DOUBLE do CAnimationValue. Ta wartość jest ustawiana jako wartość domyślna dla zmiennej animacji zhermetyzowanej. Jeśli ten obiekt animacji został zasubskrybowany do zdarzeń (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue

Ustawia wartość domyślną.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parametry

*dblDefaultValue*<br/>
Określa wartość domyślną.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania wartości domyślnej. Wartość domyślna jest zwracana do aplikacji, gdy animacja nie została uruchomiona i/lub podstawowy obiekt COM nie został utworzony. Jeśli podstawowy obiekt COM zhermetyzowany w CAnimationVarible został już utworzony, ta metoda odtwarza go, dlatego może być konieczne wywołanie EnableValueChanged/EnableIntegerValueZmieniane metody ponownie.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
