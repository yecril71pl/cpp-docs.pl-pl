---
title: Klasa CLinearTransitionFromSpeed | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
dev_langs: C++
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 41c15851be56520f1452e9167ce19ee657df5a02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="clineartransitionfromspeed-class"></a>Klasa CLinearTransitionFromSpeed
Hermetyzuje prędkość liniową przejście.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Tworzy obiekt prędkość liniową przejścia i inicjuje go o prędkości i końcowa wartość.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji na końcu przejścia.|  
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|Wartość bezwzględna prędkość zmiennej.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas przejścia prędkość liniową wartość zmiennej animacji zmienia się z określoną szybkością. Czas trwania przejścia jest określana przez różnicę między to wartość początkowa i końcowa określona wartość. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed::CLinearTransitionFromSpeed  
 Tworzy obiekt prędkość liniową przejścia i inicjuje go o prędkości i końcowa wartość.  
  
```  
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblSpeed`  
 Wartość bezwzględna prędkość zmiennej.  
  
 `dblFinalValue`  
 Wartość zmiennej animacji na końcu przejścia.  
  
##  <a name="create"></a>CLinearTransitionFromSpeed::Create  
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
  
##  <a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed::m_dblFinalValue  
 Wartość zmiennej animacji na końcu przejścia.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblspeed"></a>CLinearTransitionFromSpeed::m_dblSpeed  
 Wartość bezwzględna prędkość zmiennej.  
  
```  
DOUBLE m_dblSpeed;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
