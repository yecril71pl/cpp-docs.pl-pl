---
title: Klasa CCustomInterpolator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
dev_langs: C++
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bd687a396b6538d73290a305959ba95f6b49c7e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccustominterpolator-class"></a>Klasa CCustomInterpolator
Implementuje interpolatora podstawowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Przeciążone. Tworzy obiekt interpolatora niestandardowych i inicjuje czas trwania i szybkość pracy do określonej wartości.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|Pobiera interpolatora zależności.|  
|[CCustomInterpolator::GetDuration](#getduration)|Pobiera interpolatora czasu trwania.|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Pobiera wartość końcowego, do którego prowadzi interpolatora.|  
|[CCustomInterpolator::Init](#init)|Inicjuje czas trwania i końcowa wartość.|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Wartość argumentu wartości od danego przesunięcia.|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Szybkość pracy od danego przesunięcia interpolacji|  
|[CCustomInterpolator::SetDuration](#setduration)|Ustawia czas trwania interpolatora.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową interpolatora i szybkość pracy.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Wartość interpolowanym.|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Prędkość interpolowanym.|  
|[CCustomInterpolator::m_duration](#m_duration)|Czas trwania przejścia.|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Końcowa wartość zmiennej na końcu przejścia.|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Wartość zmiennej w chwili rozpoczęcia przejścia.|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Szybkość pracy zmiennej w chwili rozpoczęcia przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Wyprowadzenia klasy z CCustomInterpolator i zastępować wszystkie metody niezbędne w celu wdrożenia algorytm interpolacji niestandardowych. Wskaźnik do tej klasy powinien zostać przekazany jako parametr do CCustomTransition.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
 Tworzy obiekt interpolatora niestandardowych i ustawia wszystkie wartości domyślne 0.  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Czas trwania przejścia.  
  
 `finalValue`  
  
### <a name="remarks"></a>Uwagi  
 Użyj CCustomInterpolator::Init zainicjować czas trwania i końcowa wartość później w kodzie.  
  
##  <a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 Pobiera interpolatora zależności.  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValueDependencies`  
 Dane wyjściowe. Do SetInitialValueAndVelocity przekazany aspektów interpolatora, które są zależne od wartości początkowej.  
  
 `initialVelocityDependencies`  
 Dane wyjściowe. Aspekty interpolatora, które są zależne od prędkości początkowej przekazany do SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Dane wyjściowe. Aspekty interpolatora, które są zależne od czasu trwania przekazany do SetDuration.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="getduration"></a>CCustomInterpolator::GetDuration  
 Pobiera interpolatora czasu trwania.  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Dane wyjściowe. Czas trwania przejścia, w sekundach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 Pobiera wartość końcowego, do którego prowadzi interpolatora.  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Dane wyjściowe. Końcowa wartość zmiennej na końcu przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="init"></a>CCustomInterpolator::Init  
 Inicjuje czas trwania i końcowa wartość.  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Czas trwania przejścia.  
  
 `finalValue`  
 Końcowa wartość zmiennej na końcu przejścia.  
  
##  <a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue  
 Wartość argumentu wartości od danego przesunięcia.  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Dane wyjściowe. Wartość interpolowanym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity  
 Szybkość pracy od danego przesunięcia interpolacji  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parametry  
 `velocity`  
 Dane wyjściowe. Szybkość pracy zmiennej przy przesunięciu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue  
 Wartość interpolowanym.  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity  
 Prędkość interpolowanym.  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="m_duration"></a>CCustomInterpolator::m_duration  
 Czas trwania przejścia.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 Końcowa wartość zmiennej na końcu przejścia.  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 Wartość zmiennej w chwili rozpoczęcia przejścia.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 Szybkość pracy zmiennej w chwili rozpoczęcia przejścia.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>CCustomInterpolator::SetDuration  
 Ustawia czas trwania interpolatora.  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Czas trwania przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
##  <a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
 Ustawia wartość początkową interpolatora i szybkość pracy.  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
 Wartość zmiennej w chwili rozpoczęcia przejścia.  
  
 `initialVelocity`  
 Szybkość pracy zmiennej w chwili rozpoczęcia przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Podstawowa implementacja zawsze zwraca wartość PRAWDA. Zwraca wartość FALSE z implementacji przesłoniętych Jeśli chcesz zakończyć się niepowodzeniem zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
