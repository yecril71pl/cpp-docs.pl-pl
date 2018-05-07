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
ms.openlocfilehash: 923b1b74a50fd13a57c1d9c7696f81acb28453e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="canimationvalue-class"></a>Klasa CAnimationValue
Implementuje funkcje obiektu animacji, który ma jedną wartość.  
  
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
|[CAnimationValue::GetVariable](#getvariable)|Zapewnia dostęp do zmiennej hermetyzowany animacji.|  
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmiennej hermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationValue::operator o podwójnej PRECYZJI](#operator_double)|Udostępnia konwersja między CAnimationValue i o podwójnej PRECYZJI.|  
|[CAnimationValue::operator INT32](#operator_int32)|Udostępnia konwersja między CAnimationValue i INT32.|  
|[CAnimationValue::operator =](#operator_eq)|Przeciążone. Przypisuje wartości INT32 CAnimationValue.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationValue::m_value](#m_value)|Zmienna hermetyzowany animacji, która reprezentuje wartość animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationValue hermetyzuje pojedynczego obiektu CAnimationVariable i może reprezentować w aplikacjach animowany pojedynczą wartość. Na przykład można użyć tej klasy dla przezroczystość animacji (efekt zanikania), kąt (w celu obracania obiektów), lub dla wszystkich innych przypadkach, gdy trzeba utworzyć animacji, w zależności od pojedynczej wartości animowany. Używanie tej klasy w aplikacji, wystarczy tworzenia wystąpienia obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia, które mają być stosowane do wartości.  
  
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
 `pTransition`  
 Wskaźnik do obiektu przejścia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby dodać przejście do wewnętrznej listy przejść do zastosowania do zmiennej animacji. Po dodaniu przejścia nie są stosowane natychmiast i przechowywane w wewnętrznej liście. Przejścia są stosowane (dodany do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup.  
  
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
 `dblDefaultValue`  
 Określa wartość domyślną.  
  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `nObjectID`  
 Określa identyfikator obiektu.  
  
 `dwUserData`  
 Określa dane zdefiniowane przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy obiekt CAnimationValue z domyślnych właściwości: wartość domyślna to identyfikator grupy i identyfikator obiektu są ustawione na 0.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList  
 Umieszcza zmiennej hermetyzowany animacji z listy.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Funkcja zwraca wartość, zawiera wskaźnik do CAnimationVariable reprezentujący wartość animowany.  
  
##  <a name="getvalue"></a>  CAnimationValue::GetValue  
 Pobiera bieżącą wartość.  
  
```  
BOOL GetValue(DOUBLE& dblValue);  
BOOL GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblValue`  
 Dane wyjściowe. Funkcja zwraca zawiera bieżącą wartość zmiennej animacji.  
  
 `nValue`  
 Dane wyjściowe. Funkcja zwraca zawiera bieżącą wartość zmiennej animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość została pobrana pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać bieżącą wartość. Ta implementacja wywołuje metodę hermetyzowany obiektu modelu COM, a jeśli wystąpi błąd wywołania, ta metoda zwraca domyślną wartość, która wcześniej została ustawiona w konstruktorze lub SetDefaultValue.  
  
##  <a name="getvariable"></a>  CAnimationValue::GetVariable  
 Zapewnia dostęp do zmiennej hermetyzowany animacji.  
  
```  
CAnimationVariable& GetVariable();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do zmiennej hermetyzowany animacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia dostęp do zmiennej hermetyzowany animacji. Z CAnimationVariable można uzyskać dostępu do obiektu źródłowego IUIAnimationVariable, w których wskaźnik może mieć wartość NULL, jeśli zmienna animacji nie został utworzony.  
  
##  <a name="m_value"></a>  CAnimationValue::m_value  
 Zmienna hermetyzowany animacji, która reprezentuje wartość animacji.  
  
```  
CAnimationVariable m_value;  
```  
  
##  <a name="operator_double"></a>  CAnimationValue::operator o podwójnej PRECYZJI  
 Udostępnia konwersja między CAnimationValue i o podwójnej PRECYZJI.  
  
```  
operator DOUBLE();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość animacji.  
  
### <a name="remarks"></a>Uwagi  
 Udostępnia konwersja między CAnimationValue i o podwójnej PRECYZJI. Wewnętrznie ta metoda wywołuje GetValue i nie sprawdza błędy. W przypadku niepowodzenia GetValue zwrócona wartość będzie zawierać wcześniej ustawione w konstruktorze lub SetDefaultValue wartości domyślnej.  
  
##  <a name="operator_int32"></a>  CAnimationValue::operator INT32  
 Udostępnia konwersja między CAnimationValue i INT32.  
  
```  
operator INT32();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość animacji wartości jako liczby całkowitej.  
  
### <a name="remarks"></a>Uwagi  
 Udostępnia konwersja między CAnimationValue i INT32. Wewnętrznie ta metoda wywołuje GetValue i nie sprawdza błędy. W przypadku niepowodzenia GetValue zwrócona wartość będzie zawierać wcześniej ustawione w konstruktorze lub SetDefaultValue wartości domyślnej.  
  
##  <a name="operator_eq"></a>  CAnimationValue::operator =  
 Przypisuje wartość typu DOUBLE CAnimationValue.  
  
```  
void operator=(DOUBLE dblVal);  
void operator=(INT32 nVal);
```  
  
### <a name="parameters"></a>Parametry  
 `dblVal`  
 Określa wartość do przypisania do wartości animacji.  
  
 `nVal`  
 Określa wartość do przypisania do wartości animacji.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje wartość typu DOUBLE CAnimationValue. Ta wartość jest ustawiana jako wartości domyślnej dla zmiennej hermetyzowany animacji. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue  
 Ustawia wartość domyślną.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Określa wartość domyślną.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby ustawić wartość domyślną. Wartość domyślna jest zwracana do aplikacji po animacji nie została uruchomiona i/lub obiekt COM nie został utworzony. Jeśli obiekt modelu COM z CAnimationVarible już została utworzona, ta metoda tworzy go ponownie, w związku z tym konieczne może być wywołanie metody EnableValueChanged/EnableIntegerValueChanged ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
