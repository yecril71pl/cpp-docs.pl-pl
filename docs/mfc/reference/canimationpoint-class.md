---
title: Klasa CAnimationPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58c8c9aaaf212e98fdeff1e639bb09423304e643
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957406"
---
# <a name="canimationpoint-class"></a>Klasa CAnimationPoint
Implementuje funkcje punktu, w których współrzędne można animować.  
  
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
|[CAnimationPoint::AddTransition](#addtransition)|Dodaje przejścia dla X i Y.|  
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Zwraca domyślne wartości x i Y.|  
|[CAnimationPoint::GetValue](#getvalue)|Zwraca bieżącą wartość.|  
|[CAnimationPoint::GetX](#getx)|Zapewnia dostęp do CAnimationVariable dla współrzędną X.|  
|[CAnimationPoint::GetY](#gety)|Zapewnia dostęp do CAnimationVariable w współrzędną Y.|  
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne hermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Konwertuje CAnimationPoint CPoint.|  
|[CAnimationPoint::operator =](#operator_eq)|Przypisuje ptSrc CAnimationPoint.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationPoint::m_xValue](#m_xvalue)|Zmienna hermetyzowany animacji, która reprezentuje X współrzędnych punktu animacji.|  
|[CAnimationPoint::m_yValue](#m_yvalue)|Zmienna hermetyzowany animacji, która reprezentuje współrzędną Y punktu animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationPoint hermetyzuje dwa obiekty CAnimationVariable i może reprezentować w aplikacjach punktu. Na przykład można tej klasy animować pozycji wszystkich obiektów na ekranie (np. ciąg tekstowy, koło, punktu itp.). Używanie tej klasy w aplikacji, po prostu tworzenia wystąpienia obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i Wywołaj AddTransition dla każdego przejścia ma zostać zastosowany do współrzędne X i/lub Y.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationPoint`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationPoint::AddTransition  
 Dodaje przejścia dla X i Y.  
  
```  
void AddTransition(
    CBaseTransition* pXTransition,  
    CBaseTransition* pYTransition);
```  
  
### <a name="parameters"></a>Parametry  
 *pXTransition*  
 Wskaźnik do przejścia dla X współrzędnych.  
  
 *pYTransition*  
 Wskaźnik do przejścia y współrzędną.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można dodać określony przejścia do wewnętrznej listy przejść do zastosowania do zmiennych animacji x i Y. Po dodaniu przejścia nie są stosowane natychmiast i przechowywane w wewnętrznej liście. Przejścia są stosowane (dodany do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednego z współrzędne, można przekazać wartości NULL.  
  
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
 *ptDefault*  
 Określa domyślny współrzędnych punktu.  
  
 *nGroupID*  
 Określa identyfikator grupy.  
  
 *nObjectID*  
 Określa identyfikator obiektu.  
  
 *dwUserData*  
 Określa dane zdefiniowane przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy obiekt CAnimationPoint z domyślnych właściwości: domyślna współrzędnych punktu, identyfikator grupy i identyfikator obiektu są ustawione na 0.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList  
 Umieszcza zmienne hermetyzowany animacji z listy.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 *lst*  
 Funkcja zwraca wartość, zawiera wskaźniki do dwóch obiektów CAnimationVariable reprezentujący współrzędne X i Y.  
  
##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue  
 Zwraca domyślne wartości x i Y.  
  
```  
CPoint GetDefaultValue();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Punkt zawierającego wartość domyślną.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać wartości domyślnej, który wcześniej został ustawiony przez konstruktora lub SetDefaultValue.  
  
##  <a name="getvalue"></a>  CAnimationPoint::GetValue  
 Zwraca bieżącą wartość.  
  
```  
BOOL GetValue(CPoint& ptValue);
```  
  
### <a name="parameters"></a>Parametry  
 *ptValue*  
 Dane wyjściowe. Gdy metoda zwróci wartość, zawiera bieżącą wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać bieżącą wartość punktu animacji. Jeśli ta metoda kończy się niepowodzeniem lub podstawowej COM obiekty x i Y współrzędne nie zostały zainicjowane, ptValue zawiera wartość domyślną, które było wcześniej ustawione w konstruktorze lub SetDefaultValue.  
  
##  <a name="getx"></a>  CAnimationPoint::GetX  
 Zapewnia dostęp do CAnimationVariable dla współrzędną X.  
  
```  
CAnimationVariable& GetX();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący X współrzędną.  
  
### <a name="remarks"></a>Uwagi  
 Możesz wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący X współrzędną.  
  
##  <a name="gety"></a>  CAnimationPoint::GetY  
 Zapewnia dostęp do CAnimationVariable w współrzędną Y.  
  
```  
CAnimationVariable& GetY();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący współrzędną Y.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący współrzędną Y.  
  
##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue  
 Zmienna hermetyzowany animacji, która reprezentuje X współrzędnych punktu animacji.  
  
```  
CAnimationVariable m_xValue;  
```  
  
##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue  
 Zmienna hermetyzowany animacji, która reprezentuje współrzędną Y punktu animacji.  
  
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
 Ta funkcja wymaga wewnętrznie GetValue. Jeśli GetValue jakiegoś powodu nie powiedzie się, punkt zwrócony będzie zawierać wartości domyślne dla X i Y.  
  
##  <a name="operator_eq"></a>  CAnimationPoint::operator =  
 Przypisuje ptSrc CAnimationPoint.  
  
```  
void operator=(const CPoint& ptSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *ptSrc*  
 Odnosi się do CPoint lub punktu.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje ptSrc CAnimationPoint. Zaleca się czy, że przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, który odtwarza podstawowej COM obiektów dla współrzędne X i Y, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue  
 Ustawia wartość domyślną.  
  
```  
void SetDefaultValue(const POINT& ptDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *ptDefault*  
 Określa domyślną wartość punktu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby ustawić wartość domyślną wartość obiektu animacji. Wartości domyślne przypisuje tej metody do współrzędne X i Y punktu animacji. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
