---
title: Klasa CParabolicTransitionFromAcceleration | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
dev_langs: C++
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 219d8e153501334a3de02aa12153e05a4345b215
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cparabolictransitionfromacceleration-class"></a>Klasa CParabolicTransitionFromAcceleration
Hermetyzuje przejścia paraboliczne przyspieszenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|Konstruuje przejścia paraboliczne przyspieszenia i inicjuje go z określonymi parametrami.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|Akceleracja zmiennej animacji podczas przejścia.|  
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|  
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|Prędkość animacji zmiennej na końcu przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas przejścia paraboliczne przyspieszenie wartość zmiennej animacji zmienia się z wartości początkowej do końcowej koniec określonej prędkości. Można kontrolować, jak szybko osiągnie końcowa wartość zmiennej, określając przyspieszenie. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration  
 Konstruuje przejścia paraboliczne przyspieszenia i inicjuje go z określonymi parametrami.  
  
```  
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,  
    DOUBLE dblFinalVelocity,  
    DOUBLE dblAcceleration);
```  
  
### <a name="parameters"></a>Parametry  
 `dblFinalValue`  
 Wartość zmiennej animacji na końcu przejścia.  
  
 `dblFinalVelocity`  
 Prędkość animacji zmiennej na końcu przejścia.  
  
 `dblAcceleration`  
 Akceleracja zmiennej animacji podczas przejścia.  
  
##  <a name="create"></a>CParabolicTransitionFromAcceleration::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* /* not used */);
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Wskaźnik do przejścia biblioteki, która odpowiada za tworzenie przejścia standardowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście jest tworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_dblacceleration"></a>CParabolicTransitionFromAcceleration::m_dblAcceleration  
 Akceleracja zmiennej animacji podczas przejścia.  
  
```  
DOUBLE m_dblAcceleration;  
```  
  
##  <a name="m_dblfinalvalue"></a>CParabolicTransitionFromAcceleration::m_dblFinalValue  
 Wartość zmiennej animacji na końcu przejścia.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>CParabolicTransitionFromAcceleration::m_dblFinalVelocity  
 Prędkość animacji zmiennej na końcu przejścia.  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
