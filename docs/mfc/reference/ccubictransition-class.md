---
title: Klasa CCubicTransition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 806a8b92867d120a9ae099b96ecaf6fecfca4ea6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccubictransition-class"></a>Klasa CCubicTransition
Hermetyzuje przejścia trzeciego stopnia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](#ccubictransition)|Tworzy obiekt przejścia i inicjuje jego parametrów.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCubicTransition::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|  
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|Szybkość pracy zmiennej na końcu przejścia.|  
|[CCubicTransition::m_duration](#m_duration)|Czas trwania przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas przejścia trzeciego stopnia wartość zmiennej animacji zmienia ze swojej wartości początkowej do określonej wartości końcowej w czasie trwania przejścia koniec określonej szybkości. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCubicTransition`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="ccubictransition"></a>CCubicTransition::CCubicTransition  
 Tworzy obiekt przejścia i inicjuje jego parametrów.  
  
```  
CCubicTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE finalVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Czas trwania przejścia.  
  
 `finalValue`  
 Wartość zmiennej animacji na końcu przejścia.  
  
 `finalVelocity`  
 Szybkość pracy zmiennej na końcu przejścia.  
  
##  <a name="create"></a>CCubicTransition::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
`pLibrary`  
 Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), który definiuje biblioteki standardowe przejścia.  

### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście jest tworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue  
 Wartość zmiennej animacji na końcu przejścia.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity  
 Szybkość pracy zmiennej na końcu przejścia.  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
##  <a name="m_duration"></a>CCubicTransition::m_duration  
 Czas trwania przejścia.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
