---
title: Klasa CLinearTransition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64b53cafc60e556ac142cdaf1f56608e5ab3de70
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211744"
---
# <a name="clineartransition-class"></a>Klasa CLinearTransition
Hermetyzuje liniowe przejścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CLinearTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransition::CLinearTransition](#clineartransition)|Tworzy obiekt liniowe przejścia i inicjuje ją z czas trwania i końcowa wartość.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransition::Create](#create)|Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|Wartość zmiennej animacji z końcem przejścia.|  
|[CLinearTransition::m_duration](#m_duration)|Czas trwania przejścia.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas liniowe przejścia wartość zmiennej animacji przechodzi liniowo ze swojej wartości początkowej określonej wartości końcowej. Ponieważ wszystkie przejścia są automatycznie czyszczone, zaleca się ich przydzielone za pomocą nowego operatora. Zhermetyzowanego obiektu IUIAnimationTransition COM przy utworzono CAnimationController::AnimateGroup, aż do, a następnie ma wartość NULL. Zmienianie zmiennych składowych, po tworzenie ten obiekt COM nie ma wpływu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransition](../../mfc/reference/clineartransition-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="clineartransition"></a>  CLinearTransition::CLinearTransition  
 Tworzy obiekt liniowe przejścia i inicjuje ją z czas trwania i końcowa wartość.  
  
```  
CLinearTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametry  
 *Czas trwania*  
 Czas trwania przejścia.  
  
 *dblFinalValue*  
 Wartość zmiennej animacji z końcem przejścia.  
  
##  <a name="create"></a>  CLinearTransition::Create  
 Wywołania biblioteki przejścia do utworzenia obiektu zhermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
*pLibrary*  
 Wskaźnik do [interfejsu IUIAnimationTransitionLibrary](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), który definiuje bibliotekę przejścia standardowe.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przejście został utworzony pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_dblfinalvalue"></a>  CLinearTransition::m_dblFinalValue  
 Wartość zmiennej animacji z końcem przejścia.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_duration"></a>  CLinearTransition::m_duration  
 Czas trwania przejścia.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
