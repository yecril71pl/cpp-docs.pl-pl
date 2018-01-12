---
title: Klasa CAnimationRect | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b38b1225dbce3f747efeaa7aa1e5384f7931efe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="canimationrect-class"></a>Klasa CAnimationRect
Implementuje funkcje prostokąta, którego boki można animować.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](#canimationrect)|Przeciążone. Tworzy obiekt rect animacji.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](#addtransition)|Dodaje przejścia do lewej, górnej, prawej i dolnej współrzędnych.|  
|[CAnimationRect::GetBottom](#getbottom)|Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna dolnej.|  
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Zwraca wartości domyślne dla granice prostokąta.|  
|[CAnimationRect::GetLeft](#getleft)|Zapewnia dostęp do CAnimationVariable reprezentujący lewą współrzędną.|  
|[CAnimationRect::GetRight](#getright)|Zapewnia dostęp do CAnimationVariable reprezentujący prawa Współrzędna.|  
|[CAnimationRect::GetTop](#gettop)|Zapewnia dostęp do CAnimationVariable reprezentujący górną współrzędną.|  
|[CAnimationRect::GetValue](#getvalue)|Zwraca bieżącą wartość.|  
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Ustawia wartość domyślną.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Umieszcza zmienne hermetyzowany animacji z listy. (Przesłania [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::operator RECT](#operator_rect)|Konwertuje CAnimationRect obiektu RECT.|  
|[CAnimationRect::operator =](#operator_eq)|Przypisuje rect CAnimationRect.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Określa, czy prostokąt ma stały rozmiar.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Zmienna hermetyzowany animacji, która reprezentuje dolnej granica prostokąt animacji.|  
|[CAnimationRect::m_leftValue](#m_leftvalue)|Zmienna hermetyzowany animacji, która reprezentuje lewej granica prostokąt animacji.|  
|[CAnimationRect::m_rightValue](#m_rightvalue)|Zmienna hermetyzowany animacji, która reprezentuje prawa granica prostokąt animacji.|  
|[CAnimationRect::m_szInitial](#m_szinitial)|Określa początkowy rozmiar prostokąta animacji.|  
|[CAnimationRect::m_topValue](#m_topvalue)|Zmienna hermetyzowany animacji, która reprezentuje Top granica prostokąt animacji.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CAnimationRect hermetyzuje cztery CAnimationVariable obiektów i może reprezentować w aplikacjach prostokąta. Używanie tej klasy w aplikacji, wystarczy tworzenia wystąpienia obiektu tej klasy, dodaj go do kontrolera animacji przy użyciu CAnimationController::AddAnimationObject i wywołać AddTransition dla każdego przejścia do zastosowania dla współrzędnych lewy, prawy górny i dolny.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationRect`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationRect::AddTransition  
 Dodaje przejścia do lewej, górnej, prawej i dolnej współrzędnych.  
  
```  
void AddTransition(
    CBaseTransition* pLeftTransition,  
    CBaseTransition* pTopTransition,  
    CBaseTransition* pRightTransition,  
    CBaseTransition* pBottomTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pLeftTransition`  
 Określa przejście do lewej.  
  
 `pTopTransition`  
 Określa przejście dla górnej.  
  
 `pRightTransition`  
 Określa przejście dla prawej strony.  
  
 `pBottomTransition`  
 Określa przejście do dołu strony.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można dodać określony przejścia do wewnętrzną listę przejścia do zastosowania do zmiennych animacji dla każdej krawędzi prostokąta. Po dodaniu przejścia nie są stosowane natychmiast i przechowywane w wewnętrznej liście. Przejścia są stosowane (dodany do scenorysu dla określonej wartości) podczas wywoływania CAnimationController::AnimateGroup. Jeśli nie trzeba zastosować przejście do jednej strony, prostokąt, należy przekazać wartość NULL.  
  
##  <a name="canimationrect"></a>CAnimationRect::CAnimationRect  
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
 `rect`  
 Określa domyślny prostokąta.  
  
 `nGroupID`  
 Określa identyfikator grupy.  
  
 `nObjectID`  
 Określa identyfikator obiektu.  
  
 `dwUserData`  
 Określa dane zdefiniowane przez użytkownika.  
  
 `pt`  
 Współrzędne górnego lewego rogu.  
  
 `sz`  
 Rozmiar prostokąta.  
  
 `nLeft`  
 Określa współrzędną lewej granicy.  
  
 `nTop`  
 Określa współrzędną TOP powiązany.  
  
 `nRight`  
 Określa współrzędną prawej granicy.  
  
 `nBottom`  
 Określa współrzędną dolnej powiązany.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt jest tworzony z wartościami domyślnymi dla lewej, górnej, prawej i dolnej identyfikator obiektu i identyfikator grupy, która będzie równa 0. Mogą zostać zmienione później w środowisku uruchomieniowym przy użyciu SetDefaultValue i identyfikator zestawu.  
  
##  <a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList  
 Umieszcza zmienne hermetyzowany animacji z listy.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Funkcja zwraca wartość, zawiera wskaźniki do czterech obiektów CAnimationVariable reprezentujący współrzędne prostokąta.  
  
##  <a name="getbottom"></a>CAnimationRect::GetBottom  
 Zapewnia dostęp do CAnimationVariable reprezentujący Współrzędna dolnej.  
  
```  
CAnimationVariable& GetBottom();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący Współrzędna dolnej.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący Współrzędna dolnej.  
  
##  <a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue  
 Zwraca wartości domyślne dla granice prostokąta.  
  
```  
CRect GetDefaultValue();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość CRect zawierającą wartości domyślne dla lewo, prawo, górny i dolny.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać wartości domyślnej, który wcześniej został ustawiony przez konstruktora lub SetDefaultValue.  
  
##  <a name="getleft"></a>CAnimationRect::GetLeft  
 Zapewnia dostęp do CAnimationVariable reprezentujący lewą współrzędną.  
  
```  
CAnimationVariable& GetLeft();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący lewą współrzędną.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący lewą współrzędną.  
  
##  <a name="getright"></a>CAnimationRect::GetRight  
 Zapewnia dostęp do CAnimationVariable reprezentujący prawa Współrzędna.  
  
```  
CAnimationVariable& GetRight();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący prawa Współrzędna.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący prawa Współrzędna.  
  
##  <a name="gettop"></a>CAnimationRect::GetTop  
 Zapewnia dostęp do CAnimationVariable reprezentujący górną współrzędną.  
  
```  
CAnimationVariable& GetTop();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do hermetyzowany CAnimationVariable reprezentujący górną współrzędną.  
  
### <a name="remarks"></a>Uwagi  
 Można wywołać tę metodę, aby uzyskać bezpośredni dostęp do podstawowych CAnimationVariable reprezentujący górną współrzędną.  
  
##  <a name="getvalue"></a>CAnimationRect::GetValue  
 Zwraca bieżącą wartość.  
  
```  
BOOL GetValue(CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Dane wyjściowe. Gdy metoda zwróci wartość, zawiera bieżącą wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli bieżąca wartość została pomyślnie pobrana; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać bieżącą wartość prostokąta animacji. Jeśli ta metoda kończy się niepowodzeniem lub podstawowej COM obiekty do lewej, górnej, prawej i dolnej nie zostały zainicjowane, rect zawiera wartość domyślną, które było wcześniej ustawione w konstruktorze lub SetDefaultValue.  
  
##  <a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize  
 Określa, czy prostokąt ma stały rozmiar.  
  
```  
BOOL m_bFixedSize;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ten element członkowski ma wartość true, rozmiar prostokąta jest stałe i w prawo i dolnej wartości są obliczenia zawsze, gdy lewego górnego narożnika jest przenoszony zgodnie z ustalonym rozmiarze. Wartość tę należy ustawić wartość true, aby łatwo przenosić prostokątem ekranu. W takim przypadku przejścia stosowane do prawej i dolnej współrzędnych są ignorowane. Rozmiar jest przechowywany wewnętrznie podczas konstruowania obiektu i/lub wywołaj SetDefaultValue. Domyślnie ten element członkowski ma wartość FALSE.  
  
##  <a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue  
 Zmienna hermetyzowany animacji, która reprezentuje dolnej granica prostokąt animacji.  
  
```  
CAnimationVariable m_bottomValue;  
```  
  
##  <a name="m_leftvalue"></a>CAnimationRect::m_leftValue  
 Zmienna hermetyzowany animacji, która reprezentuje lewej granica prostokąt animacji.  
  
```  
CAnimationVariable m_leftValue;  
```  
  
##  <a name="m_rightvalue"></a>CAnimationRect::m_rightValue  
 Zmienna hermetyzowany animacji, która reprezentuje prawa granica prostokąt animacji.  
  
```  
CAnimationVariable m_rightValue;  
```  
  
##  <a name="m_szinitial"></a>CAnimationRect::m_szInitial  
 Określa początkowy rozmiar prostokąta animacji.  
  
```  
CSize m_szInitial;  
```  
  
##  <a name="m_topvalue"></a>CAnimationRect::m_topValue  
 Zmienna hermetyzowany animacji, która reprezentuje Top granica prostokąt animacji.  
  
```  
CAnimationVariable m_topValue;  
```  
  
##  <a name="operator_rect"></a>CAnimationRect::operator RECT  
 Konwertuje CAnimationRect obiektu RECT.  
  
```  
operator RECT();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca wartość prostokąta animacji jako obiektu RECT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wymaga wewnętrznie GetValue. Jeśli GetValue jakiegoś powodu nie powiedzie się, zwracane RECT będzie zawierać wartości domyślne dla wszystkich współrzędnych prostokąta.  
  
##  <a name="operator_eq"></a>CAnimationRect::operator =  
 Przypisuje rect CAnimationRect.  
  
```  
void operator=(const RECT& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Nowa wartość prostokąta animacji.  
  
### <a name="remarks"></a>Uwagi  
 Zaleca się to zrobić przed rozpoczęciem animacji, ponieważ ten operator wywołuje SetDefaultValue, polegające obiektów COM dla składników kolorów, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
##  <a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue  
 Ustawia wartość domyślną.  
  
```  
void SetDefaultValue(const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Określa nowe wartości domyślne dla lewej, górnej, prawej i dolnej.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby ustawić wartość domyślną wartość obiektu animacji. Tej metody przypisuje wartości domyślne granice prostokąta. Odtwarza również obiektów COM, jeśli zostały utworzone. Jeśli masz subskrypcję tego obiektu animacji na zdarzenia (ValueChanged lub IntegerValueChanged), należy ponownie włączyć te zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
