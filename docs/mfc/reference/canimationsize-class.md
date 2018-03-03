---
title: Klasa CAnimationSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2acbdad3ec5b08ef5d83b3a6cfdb2eadd3c0e17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationsize-class"></a>Klasa CAnimationSize
Implementuje funkcje obiektu rozmiar, których wymiarów można animować.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|Przeciążone. Tworzy obiekt rozmiar animacji.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|Dodaje przejścia dla szerokości i wysokości.|  
|[CAnimationSize::GetCX](#getcx)|Zapewnia dostęp do CAnimationVariable reprezentujący szerokości.|  
|[CAnimationSize::GetCY](#getcy)|Zapewnia dostęp do CAnimationVariable reprezentujący wysokość.|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla szerokości i wysokości.|  
|[CAnimationSize::GetValue](#getvalue)|Zwraca bieżącą wartość.|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne hermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|Konwertuje CAnimationSize CSize.|  
|[CAnimationSize::operator =](#operator_eq)|Przypisuje szSrc CAnimationSize.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|Zmienna hermetyzowany animacji, która reprezentuje szerokość rozmiar animacji.|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|Zmienna hermetyzowany animacji, która reprezentuje wysokość w rozmiarze animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationSize hermetyzuje dwa obiekty CAnimationVariable i może reprezentować w aplikacji o rozmiarze. Na przykład ta klasa umożliwia animować rozmiar dowolnych dwóch wymiarów obiektu na ekranie (takie jak prostokąt, kontrolować itp). Używanie tej klasy w aplikacji, wystarczy tworzenia wystąpienia obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia ma zostać zastosowany do szerokości lub wysokości.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationSize::AddTransition  
 Dodaje przejścia dla szerokości i wysokości.  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pCXTransition`  
 Wskaźnik do przejścia do szerokości.  
  
 `pCYTransition`  
 Wskaźnik do przejścia do wysokości.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można dodać określony przejścia do wewnętrznej listy przejść do zastosowania do zmiennych animacji dla szerokości i wysokości. Po dodaniu przejścia nie są stosowane natychmiast i przechowywane w wewnętrznej liście. Przejścia są stosowane (dodany do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednego z wymiarów, należy przekazać wartość NULL.  
  
##  <a name="canimationsize"></a>CAnimationSize::CAnimationSize  
 Tworzy obiekt rozmiar animacji.  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `szDefault`  
 Określa domyślny rozmiar.  
  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `nObjectID`  
 Określa identyfikator obiektu.  
  
 `dwUserData`  
 Określa dane zdefiniowane przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest tworzony z wartościami domyślnymi dla szerokości, wysokości obiekt identyfikator i Identyfikatora grupy, który zostanie ustawiona na 0. Mogą zostać zmienione później w środowisku uruchomieniowym przy użyciu SetDefaultValue i identyfikator zestawu.  
  
##  <a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList  
 Umieszcza zmienne hermetyzowany animacji z listy.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Funkcja zwraca wartość, zawiera wskaźniki do dwóch obiektów CAnimationVariable reprezentujący szerokości i wysokości.  
  
##  <a name="getcx"></a>CAnimationSize::GetCX  
 Zapewnia dostęp do CAnimationVariable reprezentujący szerokości.  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący szerokości.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący szerokości.  
  
##  <a name="getcy"></a>CAnimationSize::GetCY  
 Zapewnia dostęp do CAnimationVariable reprezentujący wysokość.  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący wysokość.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący wysokość.  
  
##  <a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue  
 Zwraca wartości domyślne dla szerokości i wysokości.  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt CSize zawierający wartości domyślne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać wartości domyślnej, który wcześniej został ustawiony przez konstruktora lub SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationSize::GetValue  
 Zwraca bieżącą wartość.  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>Parametry  
 `szValue`  
 Dane wyjściowe. Gdy metoda zwróci wartość, zawiera bieżącą wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać bieżącą wartość rozmiaru animacji. Jeśli ta metoda nie powiedzie się lub nie zostały zainicjowane podstawowej obiektów COM dla szerokości i rozmiar, szValue zawiera wartość domyślną, które było wcześniej ustawione w konstruktorze lub SetDefaultValue.  
  
##  <a name="m_cxvalue"></a>CAnimationSize::m_cxValue  
 Zmienna hermetyzowany animacji, która reprezentuje szerokość rozmiar animacji.  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>CAnimationSize::m_cyValue  
 Zmienna hermetyzowany animacji, która reprezentuje wysokość w rozmiarze animacji.  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>CAnimationSize::operator CSize  
 Konwertuje CAnimationSize CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość rozmiaru animacji jako CSize.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga wewnętrznie GetValue. Jeśli GetValue jakiegoś powodu nie powiedzie się, rozmiar zwróconego będzie zawierać wartości domyślne dla szerokości i wysokości.  
  
##  <a name="operator_eq"></a>CAnimationSize::operator =  
 Przypisuje szSrc CAnimationSize.  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `szSrc`  
 Odnosi się do CSize lub rozmiaru.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje szSrc CAnimationSize. Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, polegające obiektów COM szerokość i wysokość, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
##  <a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue  
 Ustawia wartość domyślną.  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `szDefault`  
 Określa nowy domyślny rozmiar.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby ustawić wartość domyślną wartość obiektu animacji. Tej metody przypisuje wartości domyślne szerokość i wysokość w rozmiarze animacji. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
