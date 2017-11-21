---
title: Klasa CAnimationColor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e03ba23b30c714216356d49086a0d8f81df7db14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="canimationcolor-class"></a>Klasa CAnimationColor
Implementuje funkcje koloru, których składniki czerwony, zielonemu i niebieskiemu można animować.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationColor : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationColor::CAnimationColor](#canimationcolor)|Przeciążone. Tworzy obiekt animacji kolorów.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationColor::AddTransition](#addtransition)|Dodaje przejścia dla składników czerwony, zielony i niebieski.|  
|[CAnimationColor::GetB](#getb)|Zapewnia dostęp do CAnimationVariable reprezentujący składnika niebieski.|  
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla składników kolorów.|  
|[CAnimationColor::GetG](#getg)|Zapewnia dostęp do CAnimationVariable reprezentujący składnika zielony.|  
|[CAnimationColor::GetR](#getr)|Zapewnia dostęp do CAnimationVariable reprezentujący składnika czerwony.|  
|[CAnimationColor::GetValue](#getvalue)|Zwraca bieżącą wartość.|  
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne hermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationColor::operator COLORREF](#operator_colorref)||  
|[CAnimationColor::operator =](#operator_eq)|Przypisuje kolor CAnimationColor.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationColor::m_bValue](#m_bvalue)|Zmienna hermetyzowany animacji, która reprezentuje składnika niebieski koloru animacji.|  
|[CAnimationColor::m_gValue](#m_gvalue)|Zmienna hermetyzowany animacji, która reprezentuje składnika zielony koloru animacji.|  
|[CAnimationColor::m_rValue](#m_rvalue)|Zmienna hermetyzowany animacji, która reprezentuje składnika czerwony koloru animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationColor hermetyzuje trzy obiekty CAnimationVariable i może reprezentować w aplikacjach koloru. Na przykład ta klasa umożliwia animować kolory wszystkich obiektów na ekranie (takie jak kolor tekstu, kolor tła itp.). Używanie tej klasy w aplikacji, wystarczy tworzenia wystąpienia obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia ma zostać zastosowany do składników czerwony, zielony i niebieski.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationColor`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationColor::AddTransition  
 Dodaje przejścia dla składników czerwony, zielony i niebieski.  
  
```  
void AddTransition(
    CBaseTransition* pRTransition,  
    CBaseTransition* pGTransition,  
    CBaseTransition* pBTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pRTransition`  
 Przejście do składnika czerwony.  
  
 `pGTransition`  
 Przejście do składnika zielony.  
  
 `pBTransition`  
 Przejście do składnika niebieski.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można dodać określony przejścia do wewnętrznej listy przejść do zastosowania do zmiennych animacji reprezentująca składniki kolorów. Po dodaniu przejścia nie są stosowane natychmiast i przechowywane w wewnętrznej liście. Przejścia są stosowane (dodany do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednego ze składników kolorów, można przekazać wartości NULL.  
  
##  <a name="canimationcolor"></a>CAnimationColor::CAnimationColor  
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
 `color`  
 Określa domyślny kolor.  
  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `nObjectID`  
 Określa identyfikator obiektu.  
  
 `dwUserData`  
 Określa dane zdefiniowane przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest tworzony z wartościami domyślnymi zielony czerwony, niebieski, identyfikator grupy, która będzie równa 0 lub identyfikator obiektu. Mogą zostać zmienione później w środowisku uruchomieniowym przy użyciu SetDefaultValue i identyfikator zestawu.  
  
##  <a name="getanimationvariablelist"></a>CAnimationColor::GetAnimationVariableList  
 Umieszcza zmienne hermetyzowany animacji z listy.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Funkcja zwraca wartość, zawiera wskaźniki do trzech obiektów CAnimationVariable reprezentująca składniki czerwonemu, zielonemu i niebieski.  
  
##  <a name="getb"></a>CAnimationColor::GetB  
 Zapewnia dostęp do CAnimationVariable reprezentujący składnika niebieski.  
  
```  
CAnimationVariable& GetB();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący składnika niebieski.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący składnika niebieski.  
  
##  <a name="getdefaultvalue"></a>CAnimationColor::GetDefaultValue  
 Zwraca wartości domyślne dla składników kolorów.  
  
```  
COLORREF GetDefaultValue();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość COLORREF zawierający domyślne wartości RGB składników.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać wartości domyślnej, który wcześniej został ustawiony przez konstruktora lub SetDefaultValue.  
  
##  <a name="getg"></a>CAnimationColor::GetG  
 Zapewnia dostęp do CAnimationVariable reprezentujący składnika zielony.  
  
```  
CAnimationVariable& GetG();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentująca składnika zielony.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentująca składnika zielony.  
  
##  <a name="getr"></a>CAnimationColor::GetR  
 Zapewnia dostęp do CAnimationVariable reprezentujący składnika czerwony.  
  
```  
CAnimationVariable& GetR();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący składnika czerwony.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący składnika czerwony.  
  
##  <a name="getvalue"></a>CAnimationColor::GetValue  
 Zwraca bieżącą wartość.  
  
```  
BOOL GetValue(COLORREF& color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Dane wyjściowe. Gdy metoda zwróci wartość, zawiera bieżącą wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać bieżącą wartość koloru animacji. Jeśli ta metoda zawiedzie lub podstawowej obiektów COM dla składników kolorów nie zostały zainicjowane, kolor zawiera wartość domyślną, które było wcześniej ustawione w konstruktorze lub SetDefaultValue.  
  
##  <a name="m_bvalue"></a>CAnimationColor::m_bValue  
 Zmienna hermetyzowany animacji, która reprezentuje składnika niebieski koloru animacji.  
  
```  
CAnimationVariable m_bValue;  
```  
  
##  <a name="m_gvalue"></a>CAnimationColor::m_gValue  
 Zmienna hermetyzowany animacji, która reprezentuje składnika zielony koloru animacji.  
  
```  
CAnimationVariable m_gValue;  
```  
  
##  <a name="m_rvalue"></a>CAnimationColor::m_rValue  
 Zmienna hermetyzowany animacji, która reprezentuje składnika czerwony koloru animacji.  
  
```  
CAnimationVariable m_rValue;  
```  
  
##  <a name="operator_colorref"></a>CAnimationColor::operator COLORREF  
  
```  
operator COLORREF();
```   
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="operator_eq"></a>CAnimationColor::operator =  
 Przypisuje kolor CAnimationColor.  
  
```  
void operator=(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Określa nową wartość koloru animacji.  
  
### <a name="remarks"></a>Uwagi  
 Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, polegające obiektów COM dla składników kolorów, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
##  <a name="setdefaultvalue"></a>CAnimationColor::SetDefaultValue  
 Ustawia wartość domyślną.  
  
```  
void SetDefaultValue(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Określa nowe wartości domyślne dla składników czerwonemu, zielonemu i niebieski.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby ustawić wartość domyślną wartość obiektu animacji. Tej metody przypisuje wartości domyślne do kolorów składników animacji kolorów. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
