---
title: Klasa CCustomTransition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
dev_langs:
- C++
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b94fd32bd00a484c5f8e3ba9e86efc5a9637e4e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccustomtransition-class"></a>Klasa CCustomTransition
Implementuje niestandardowych przejścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Tworzy obiekt niestandardowych przejścia.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM. (Przesłania [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Ustawia wartość początkową, które mają zostać zastosowane do zmiennej animacji skojarzone z tym przejścia.|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Ustawia początkowej szybkość pracy, które mają zostać zastosowane do zmiennej animacji skojarzone z tym przejścia.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Określa, czy z SetInitialValue określono wartość początkowa.|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Określa, czy prędkość początkowa określono z SetInitialVelocity.|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|Przechowuje wartość początkowa.|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Przechowuje prędkość początkowa.|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Przechowuje wskaźnik do interpolatora niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa CCustomTransitions umożliwia deweloperom wdrażanie niestandardowych przejścia. Ma ona utworzony i używany jako standardowa przejścia, ale jego konstruktora akceptuje jako parametr wskaźnik do niestandardowych interpolatora. Wykonaj poniższe kroki, aby użyć niestandardowej przejścia: 1. Wyprowadzenia klasy z CCustomInterpolator i wdrożenie co najmniej InterpolateValue metody. 2. Upewnij się, że okres istnienia obiektu niestandardowych interpolatora musi być dłuższy niż czas trwania animacji gdzie są używane. 3. Utwórz wystąpienie (użycie operatora new) obiektu CCustomTransition i przekazać wskaźnik do niestandardowych interpolatora w konstruktorze. 4. Jeśli te parametry są wymagane dla niestandardowych interpolacji wywołać CCustomTransition::SetInitialValue i CCustomTransition::SetInitialVelocity. 5. Zatrzymaj wskaźnik myszy niestandardowych przechodzenia do metody AddTransition obiektu animacji, którego wartość należy animowany przy użyciu niestandardowego algorytmu. 6. Jeśli należy zmienić wartość obiektu animacji interfejsu API systemu Windows animacji spowodują wywołanie w CCustomInterpolator InterpolateValue (i innych odpowiednich metod).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="ccustomtransition"></a>CCustomTransition::CCustomTransition  
 Tworzy obiekt niestandardowych przejścia.  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Wskaźnik do interpolatora niestandardowych.  
  
##  <a name="create"></a>CCustomTransition::Create  
 Wywołuje biblioteki przejścia do utworzenia obiektu hermetyzowany przejścia COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>Parametry  
 `pFactory`  
 Wskaźnik do przejścia factory, które jest odpowiedzialny za tworzenie niestandardowych przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Tej metody można również ustawić wartość początkowa i prędkość początkowa ma zostać zastosowany do zmiennej animacji, który jest skojarzony z tym przejścia. W tym celu należy wywołać SetInitialValue i SetInitialVelocity przed platformę tworzy obiekt COM hermetyzowany przejścia (zdarza się to podczas wywoływania CAnimationController::AnimateGroup).  
  
##  <a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified  
 Określa, czy z SetInitialValue określono wartość początkowa.  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified  
 Określa, czy prędkość początkowa określono z SetInitialVelocity.  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="m_initialvalue"></a>CCustomTransition::m_initialValue  
 Przechowuje wartość początkowa.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity  
 Przechowuje prędkość początkowa.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator  
 Przechowuje wskaźnik do interpolatora niestandardowych.  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="setinitialvalue"></a>CCustomTransition::SetInitialValue  
 Ustawia wartość początkową, które mają zostać zastosowane do zmiennej animacji skojarzone z tym przejścia.  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity  
 Ustawia początkowej szybkość pracy, które mają zostać zastosowane do zmiennej animacji skojarzone z tym przejścia.  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialVelocity`  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
