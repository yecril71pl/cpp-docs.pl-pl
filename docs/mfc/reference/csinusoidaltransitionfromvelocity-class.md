---
title: Klasa CSinusoidalTransitionFromVelocity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9f5cc55adac2bf5900d9891635a025716b9c1f3
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078582"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>Klasa CSinusoidalTransitionFromVelocity
Hermetyzuje przejście sinusoidalnego szybkość pracy, które ma amplitudy określonej na podstawie początkowej prędkość animacji zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSinusoidalTransitionFromVelocity : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](#csinusoidaltransitionfromvelocity)|Tworzy obiekt przejścia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::m_duration](#m_duration)|Czas trwania przejścia.|  
|[CSinusoidalTransitionFromVelocity::m_period](#m_period)|Okres oscylacji sinusoidalnego wave w sekundach.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość zmiennej animacji oscillates wokół wartości początkowej przez cały czas trwania przejścia sinusoidalnego zakresu. Amplitudy drgań zależy od prędkości zmiennej animacji po rozpoczęciu przejścia. Ponieważ wszystkie przejścia są automatycznie usuwane, zaleca się ich przydzielony przy użyciu nowego operatora. Hermetyzowany obiektu IUIAnimationTransition COM utworzeniu przez CAnimationController::AnimateGroup, aż do, a następnie jest NULL. Po utworzenia tego obiektu modelu COM nie ma wpływu, zmiana zmiennych Członkowskich.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="create"></a>  CSinusoidalTransitionFromVelocity::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
 *pLibrary*  
 Wskaźnik do przejścia biblioteki, która odpowiada za tworzenie przejścia standardowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście jest tworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="csinusoidaltransitionfromvelocity"></a>  CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity  
 Tworzy obiekt przejścia.  
  
```  
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,  
    UI_ANIMATION_SECONDS period);
```  
  
### <a name="parameters"></a>Parametry  
 *Czas trwania*  
 Czas trwania przejścia.  
  
 *Okres*  
 Okres oscylacji sinusoidalnego wave w sekundach.  
  
##  <a name="m_duration"></a>  CSinusoidalTransitionFromVelocity::m_duration  
 Czas trwania przejścia.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_period"></a>  CSinusoidalTransitionFromVelocity::m_period  
 Okres oscylacji sinusoidalnego wave w sekundach.  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
