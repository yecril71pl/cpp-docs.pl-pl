---
title: Klasa CDiscreteTransition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
dev_langs:
- C++
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0252cc64a1d14a6d096a5c4ad6dd2e0d6c3c7ff
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957035"
---
# <a name="cdiscretetransition-class"></a>Klasa CDiscreteTransition
Hermetyzuje odrębny przejścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Tworzy obiekt odrębny przejścia i inicjuje jego parametrów.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDiscreteTransition::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|  
|[CDiscreteTransition::m_delay](#m_delay)|Ilość czasu, za pomocą którego natychmiastowe przełączenie końcowa wartość opóźnienia.|  
|[CDiscreteTransition::m_hold](#m_hold)|Ilość czasu, przez których mają być przechowywane w końcowej wartości zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas przejścia dyskretnych zmienna animacji pozostaje w początkowej wartości przez określony okres czasu, a następnie przełącza natychmiast do określonej wartości końcowej i pozostaje w tym wartości czasu wstrzymania danego. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition  
 Tworzy obiekt odrębny przejścia i inicjuje jego parametrów.  
  
```  
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,  
    DOUBLE dblFinalValue,  
    UI_ANIMATION_SECONDS hold);
```  
  
### <a name="parameters"></a>Parametry  
 *delay*  
 Ilość czasu, za pomocą którego natychmiastowe przełączenie końcowa wartość opóźnienia.  
  
 *dblFinalValue*  
 Wartość zmiennej animacji na końcu przejścia.  
  
 *blokady*  
 Ilość czasu, przez których mają być przechowywane w końcowej wartości zmiennej.  
  
##  <a name="create"></a>  CDiscreteTransition::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
*pLibrary*  
 Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), który definiuje biblioteki standardowe przejścia.  

  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście jest tworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue  
 Wartość zmiennej animacji na końcu przejścia.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_delay"></a>  CDiscreteTransition::m_delay  
 Ilość czasu, za pomocą którego natychmiastowe przełączenie końcowa wartość opóźnienia.  
  
```  
UI_ANIMATION_SECONDS m_delay;  
```  
  
##  <a name="m_hold"></a>  CDiscreteTransition::m_hold  
 Ilość czasu, przez których mają być przechowywane w końcowej wartości zmiennej.  
  
```  
UI_ANIMATION_SECONDS m_hold;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
