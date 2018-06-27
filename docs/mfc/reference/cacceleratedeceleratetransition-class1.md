---
title: CAccelerateDecelerateTransition Class1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4342ed03991317bd030d308dbac9945734dcbd9e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954711"
---
# <a name="cacceleratedeceleratetransition-class"></a>Klasa CAccelerateDecelerateTransition
Implementuje accelerate-zwalnia przejścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Tworzy obiekt przejścia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Stosunek czas skraca czas trwania.|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Stosunek czas decelerating czasu trwania.|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Czas trwania przejścia.|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Wartość zmiennej animacji na końcu przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas accelerate-zwalnia przejścia, zmienna animacji przyspiesza i spowalnia w czasie trwania przejścia koniec określoną wartość. Można kontrolować, jak szybko zmiennej przyspieszają i zwalnia niezależnie, określając różne przyspieszenie i stosunek opóźnienia. Po początkowej prędkość wynosi zero, stosunek przyspieszenie jest część zmiennej automatycznemu przyspieszenia; czas trwania Podobnie o stosunku opóźnienia. Jeśli prędkość początkowa jest różna od zera, jest ułamku czasu między prędkość osiągnięcia zero i na końcu przejścia. Stosunek przyspieszenie i stosunek prędkości powinien Suma, umożliwiającej maksymalnie 1.0. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 Tworzy obiekt przejścia.  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>Parametry  
 *Czas trwania*  
 Czas trwania przejścia.  
  
 *finalValue*  
 Wartość zmiennej animacji na końcu przejścia.  
  
 *accelerationRatio*  
 Stosunek czas skraca czas trwania.  
  
 *decelerationRatio*  
 Stosunek czas decelerating czasu trwania.  
  
##  <a name="create"></a>  CAccelerateDecelerateTransition::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>Parametry  
*pLibrary*  
 Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](https://msdn.microsoft.com/library/windows/desktop/dd371897), który definiuje biblioteki standardowe przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście jest tworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio  
 Stosunek czas skraca czas trwania.  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio  
 Stosunek czas decelerating czasu trwania.  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration  
 Czas trwania przejścia.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue  
 Wartość zmiennej animacji na końcu przejścia.  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
