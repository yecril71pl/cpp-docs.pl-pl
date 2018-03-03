---
title: Klasa CInterpolatorBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
dev_langs:
- C++
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79cea720391127f52d441de8f02c53756790d4b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cinterpolatorbase-class"></a>Klasa CInterpolatorBase
Implementuje wywołanie zwrotne, które jest wywoływane przez interfejs API animacji, gdy należy obliczyć nową wartość zmiennej animacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Konstruuje `CInterpolatorBase` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](#createinstance)|Tworzy wystąpienie `CInterpolatorBase` i przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|Pobiera interpolatora zależności. (Przesłania `CUIAnimationInterpolatorBase::GetDependencies`.)|  
|[CInterpolatorBase::GetDuration](#getduration)|Pobiera interpolatora czasu trwania. (Przesłania `CUIAnimationInterpolatorBase::GetDuration`.)|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Pobiera wartość końcowego, do którego prowadzi interpolatora. (Przesłania `CUIAnimationInterpolatorBase::GetFinalValue`.)|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Wartość od danego przesunięcia interpolacji (zastępuje `CUIAnimationInterpolatorBase::InterpolateValue`.)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Szybkość pracy od danego przesunięcia interpolacji (zastępuje `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.|  
|[CInterpolatorBase::SetDuration](#setduration)|Ustawia czas trwania interpolatora (zastępuje `CUIAnimationInterpolatorBase::SetDuration`.)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Ustawia wartość początkową interpolatora i szybkość pracy. (Przesłania `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|  
  
## <a name="remarks"></a>Uwagi  
 Ten program obsługi jest tworzony i przekazane do `IUIAnimationTransitionFactory::CreateTransition` podczas `CCustomTransition` obiekt jest tworzony jako część procesu inicjalizacji animacji (uruchomione przez `CAnimationController::AnimateGroup`). Zazwyczaj nie trzeba korzystać bezpośrednio do tej klasy, po prostu routs wszystkie zdarzenia do `CCustomInterpolator`-klasy, w których wskaźnik jest przekazany do konstruktora `CCustomTransition`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 Tworzy obiekt CInterpolatorBase.  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 Tworzy wystąpienie CInterpolatorBase i przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Wskaźnik do interpolatora niestandardowych.  
  
 `ppHandler`  
 Dane wyjściowe. Zawiera wskaźnik do wystąpienia CInterpolatorBase po powrocie z funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 Pobiera interpolatora zależności.  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValueDependencies`  
 Dane wyjściowe. Do SetInitialValueAndVelocity przekazany aspektów interpolatora, które są zależne od wartości początkowej.  
  
 `initialVelocityDependencies`  
 Dane wyjściowe. Aspekty interpolatora, które są zależne od prędkości początkowej przekazany do SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Dane wyjściowe. Aspekty interpolatora, które są zależne od czasu trwania przekazany do SetDuration.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody GetDependencies zwraca E_FAIL.  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 Pobiera interpolatora czasu trwania.  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Dane wyjściowe. Czas trwania przejścia, w sekundach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody GetDuration zwraca E_FAIL.  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 Pobiera wartość końcowego, do którego prowadzi interpolatora.  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Dane wyjściowe. Końcowa wartość zmiennej na końcu przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody GetFinalValue zwraca E_FAIL.  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 Interpolacji wartość danego przesunięcia.  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `offset`  
 Przesunięcie od początku przejścia. Przesunięcie zawsze jest większa niż lub równa zero i mniejsza niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia jest równy zero.  
  
 `value`  
 Dane wyjściowe. Wartość interpolowanym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody InterpolateValue zwraca E_FAIL.  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 Szybkość pracy od danego przesunięcia interpolacji  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parametry  
 `offset`  
 Przesunięcie od początku przejścia. Przesunięcie zawsze jest większa lub równa zero i mniejsza niż czas trwania przejścia. Ta metoda nie jest wywoływana, jeśli czas trwania przejścia jest równy zero.  
  
 `velocity`  
 Dane wyjściowe. Szybkość pracy zmiennej przy przesunięciu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody InterpolateVelocity zwraca E_FAIL.  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 Przechowuje wskaźnik do interpolatora niestandardowego, który będzie obsługiwał zdarzenia.  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Wskaźnik do interpolatora niestandardowych.  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 Ustawia czas trwania interpolatora  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Czas trwania przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody SetDuration zwraca E_FAIL.  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 Ustawia wartość początkową interpolatora i szybkość pracy.  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
 Wartość zmiennej w chwili rozpoczęcia przejścia.  
  
 `initialVelocity`  
 Szybkość pracy zmiennej w chwili rozpoczęcia przejścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. Jeśli nie ustawiono CCustomInterpolator lub niestandardowych implementacja zwraca wartość FALSE z metody SetInitialValueAndVelocity zwraca E_FAIL.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
